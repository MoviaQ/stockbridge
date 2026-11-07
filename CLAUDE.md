# Ostatnia sztuka

Warstwa integracyjna między systemem ERP (SOAP) a kanałami sprzedaży (REST): sklep, Allegro, Zalando.
Cel: overselling zdarza się rzadko, każdy przypadek jest wykryty i obsłużony automatycznie, a żadne zamówienie nie ginie.
Projekt edukacyjny do portfolio. Opis problemu i architektury: `docs/plan.md`.

## Tryb pracy: to jest projekt do nauki

Właściciel repo uczy się Javy, Springa i systemów rozproszonych. Kod, którego nie rozumie, jest dla niego bezwartościowy.

- Pracuj małymi krokami. Jedna zmiana = jedna rzecz, którą da się przejrzeć w kilka minut.
- Przed implementacją powiedz w 2–3 zdaniach, co zrobisz i dlaczego. Przy nowym pojęciu (np. outbox, ack) dodaj jedno zdanie wyjaśnienia.
- Gdy są dwa sensowne podejścia, nie wybieraj po cichu. Opisz oba krótko i zapytaj.
- Nowe zadanie zaczynaj od skilla `/nowe-zadanie`.

## Co należy do człowieka, a co do agenta

| Obszar | Właściciel | Zasada dla agenta |
|---|---|---|
| `contracts/` (WSDL, OpenAPI) | człowiek | Nie zmieniaj. Jeśli kontrakt jest błędny lub niepełny, zgłoś to. |
| `docs/adr/` | człowiek | Możesz przygotować szkic przez `/adr`, decyzję podejmuje człowiek. |
| Testy scenariuszy awarii i współbieżności | człowiek | Nie osłabiaj ich, nie oznaczaj jako pominięte, nie zmieniaj oczekiwanych wartości, żeby przeszły. |
| Implementacja, konfiguracja, testy jednostkowe | agent | Człowiek przegląda każdą zmianę. |

## Zasady domenowe (łamanie ich to błąd, nie styl)

1. **Zmiana licznika stanów jest atomowa.** Jedno polecenie SQL (`SET available = available - 1 ... RETURNING available`), nigdy „odczytaj, policz, zapisz” w dwóch krokach.
2. **Każde zdarzenie z zewnątrz jest przetwarzane idempotentnie.** Identyfikator zdarzenia zapisany z ograniczeniem unikalności w tej samej transakcji co skutek.
3. **Zapis do bazy i wysłanie wiadomości idą przez outbox.** Nigdy `save()` i zaraz potem `send()` w tym samym kodzie.
4. **Nie cache'ujemy liczby sztuk wysyłanej do kanałów.** Cache (Redis) tylko dla katalogu, mapowania SKU → oferta i tokenów.
5. **Każde wywołanie sieciowe ma timeout.** Brak timeoutu = wątek wiszący w nieskończoność.
6. **Błąd nie znika po cichu.** Żadnego pustego `catch`. Wiadomość, której nie da się przetworzyć, trafia do DLQ z przyczyną.

Przed oddaniem zmiany dotykającej zamówień, stanów lub kolejki uruchom `/przeglad-integracji`.

## Raportowanie

Każde „zrobione” zawiera:
1. **Wynik** – jedno zdanie.
2. **Dowód** – jakie komendy/testy uruchomiono i z jakim wynikiem.
3. **Niesprawdzone** – co zostało nieweryfikowane i dlaczego.
4. **Skróty** – każde obejście, `@Disabled`, podniesiony limit, TODO. „Brak”, jeśli nie ma.

Nie pisz „powinno działać”. Jeśli czegoś nie uruchomiono, napisz to wprost.

Gdy człowiek wykryje twój błąd, zaproponuj wpis przez `/agent-log`.

## Pamięć projektu

Nie pamiętasz poprzednich rozmów. Zanim zaczniesz, przeczytaj `docs/ustalenia.md` i `docs/plan.md`.
Gdy w rozmowie zapadnie ustalenie, zapisz je od razu skillem `/zapisz-ustalenia`, bez czekania na prośbę.

## Stan projektu

- Etap: **0, przygotowanie repo**. Brak kodu.
- Stos (planowany): Java, Spring Boot, Maven (wielomodułowy), PostgreSQL, RabbitMQ, Redis, Docker Compose, Testcontainers.
- Konkretne wersje ustalamy przy pierwszym module i zapisujemy w ADR. Nie zakładaj wersji z pamięci, sprawdź aktualne.

## Struktura (docelowa)

```
contracts/            kontrakty pisane ręcznie (WSDL, OpenAPI)
erp-simulator/        udaje ERP: SOAP, regulowane opóźnienie i błędy
channel-simulators/   udają marketplace'y: własna kopia stanu, duplikaty zdarzeń
integration-service/  główna aplikacja
erp-adapter/          kolejka → SOAP do ERP, retry, DLQ
load-test/            scenariusz black-friday
docs/                 plan, ADR-y, agent-log, notatki z lektury, wyniki pomiarów
```

## Język

Zob. `docs/ustalenia.md`, U-001.
