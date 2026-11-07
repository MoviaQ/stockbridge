---
name: przeglad-integracji
description: Przegląd zmiany pod kątem typowych błędów integracyjnych - współbieżność, idempotentność, transakcje, awarie, kolejki, cache. Użyj przed oddaniem każdej zmiany, która dotyka zamówień, stanów magazynowych, kolejki, wywołań ERP lub kanałów.
---

# Przegląd integracji

Agenci najczęściej mylą się w miejscach, które działają na „szczęśliwej ścieżce”, a psują się przy współbieżności i awariach. Ta lista sprawdza dokładnie te miejsca.

## Kroki

1. Ustal zakres: `git diff` względem gałęzi bazowej (albo wskazane pliki).

2. Dla każdego punktu poniżej odpowiedz **TAK / NIE / NIE DOTYCZY** i przy TAK lub NIE wskaż `plik:linia`. Nie odpowiadaj z pamięci, przeczytaj kod.

### Współbieżność
- [ ] Czy gdziekolwiek jest wzorzec „odczytaj, policz, zapisz” na współdzielonych danych (licznik, status)? To błąd. Musi być atomowe polecenie lub blokada.
- [ ] Co się stanie, gdy ten kod wykona się równolegle w dwóch wątkach lub dwóch instancjach aplikacji?

### Idempotentność
- [ ] Czy przetworzenie tego samego zdarzenia dwa razy daje ten sam wynik?
- [ ] Czy zapis „to zdarzenie już przetworzono” jest w tej samej transakcji co skutek?

### Transakcje i outbox
- [ ] Czy jest wysyłka wiadomości lub wywołanie HTTP wewnątrz transakcji bazodanowej? (Transakcja może się wycofać, a wiadomość już poszła.)
- [ ] Czy jest zapis do bazy, a zaraz po nim wysyłka do kolejki bez outboxu?

### Awarie
- [ ] Czy każde wywołanie sieciowe ma ustawiony timeout?
- [ ] Co się stanie, gdy aplikacja padnie dokładnie między dwiema liniami tej zmiany?
- [ ] Czy jest pusty `catch`, `catch` z samym logiem bez decyzji, albo połknięty wyjątek?
- [ ] Czy retry ma limit i rosnącą przerwę? Czy po wyczerpaniu prób wiadomość trafia do DLQ z przyczyną?

### Kolejka
- [ ] Czy potwierdzenie (ack) następuje dopiero po skutecznym przetworzeniu?
- [ ] Czy kolejność wiadomości ma tu znaczenie? Jeśli tak, co ją gwarantuje?

### Cache
- [ ] Czy cache'owana jest liczba sztuk wysyłana do kanałów lub używana do decyzji? To błąd (zasada 4 w CLAUDE.md).
- [ ] Czy dla każdego nowego wpisu w cache jest TTL i wiadomo, kiedy jest unieważniany?

### Testy
- [ ] Czy zmiana ma test, który **nie przeszedłby** bez niej? (Uruchom go na starym kodzie, jeśli to możliwe.)
- [ ] Czy jakiś test został osłabiony, wyłączony lub ma zmienione oczekiwane wartości?

3. Podsumuj: lista problemów od najpoważniejszego, z `plik:linia` i scenariuszem, który psuje. Jeśli nic nie znaleziono, napisz, które punkty sprawdzono, a które były NIE DOTYCZY.
