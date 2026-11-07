# Proces review

Każda zmiana przechodzi przez pull request i pętlę review, zanim trafi do `main`.

## Cykl

1. **Zmiana na osobnej gałęzi.** Jedna gałąź = jedno zadanie. Zmiana na tyle mała, żeby dało się ją przejrzeć w kilka minut.
2. **Testy przed PR.** Autor uruchamia testy i wpisuje wynik do opisu PR.
3. **Artefakt zmiany.** Przed otwarciem PR agent publikuje artefakt (stronę) dla człowieka z trzema częściami:
   - **co się zmieniło**: pliki i moduły, w jednym–dwóch zdaniach na każdy,
   - **w jaki sposób**: jak działa nowe zachowanie, z diagramem lub przykładem, gdy to pomaga zrozumieć,
   - **dowody**: uruchomione komendy i testy z wynikami, a przy zmianach w zachowaniu wynik prawdziwego uruchomienia.

   Link do artefaktu trafia do opisu PR. Jeśli narzędzie do artefaktów nie jest dostępne w sesji, agent mówi to wprost i pyta, gdzie przedstawić te informacje.
4. **Otwarcie PR** z opisem według szablonu poniżej.
5. **Review:** `/code-review low <numer PR>` albo `/code-review medium <numer PR>`.
   - `low`: zmiany mechaniczne lub małe, bez nowej logiki (konfiguracja, nazewnictwo, dokumentacja, szkielet).
   - `medium`: każda zmiana z logiką, a zawsze zmiana dotykająca zasad domenowych z `CLAUDE.md`.
   - Wyższych poziomów nie używamy.
6. **Poprawki.** Każda uwaga dostaje jedną odpowiedź: *poprawione* albo *odrzucone, bo …*. Nie pomijamy uwag po cichu.
7. **Ponowne review** tym samym poziomem na zaktualizowanym PR.
8. **Koniec pętli**, gdy zostały tylko małe uwagi.

Człowiek nie przegląda każdej zmiany ręcznie. Ocenia ją na podstawie artefaktu zmiany i dowodów.

## Co to jest mała uwaga

> Propozycja agenta, do potwierdzenia przez człowieka.

**Mała:** nie zmienia zachowania programu. Nazewnictwo, styl, drobne uproszczenie, komentarz.

**Nie jest mała:** wszystko, co może dać zły wynik albo utratę danych. Błąd logiki, współbieżność, brak obsługi błędu, brak timeoutu, naruszenie którejkolwiek zasady domenowej z `CLAUDE.md`, brakujący test dla nowej logiki.

Pozostałe małe uwagi można zostawić. Wtedy wpisz je w opisie PR jako świadomie pominięte.

## Limit rund

> Propozycja agenta, do potwierdzenia przez człowieka.

Jeśli po **3 rundach** nadal są uwagi, które nie są małe, zatrzymaj się i zapytaj człowieka. Zwykle oznacza to, że zadanie było źle podzielone albo kryteria były niejasne.

## Szablon opisu PR

```markdown
## Co
Jedno–dwa zdania. Link do artefaktu zmiany.

## Dlaczego
Link do zadania w docs/plan.md, ustalenia lub ADR.

## Dowód
Jakie testy uruchomiono i z jakim wynikiem.

## Niesprawdzone
Co zostało niezweryfikowane i dlaczego. „Brak”, jeśli wszystko.

## Skróty
Obejścia, wyłączone testy, TODO. „Brak”, jeśli nie ma.

## Historia review
- Runda 1 (medium): N uwag. Poprawione: … Odrzucone: … (powód)
- Runda 2 (medium): …
- Pozostawione małe uwagi: …
```

Historia review zostaje w PR. To dowód w portfolio, że zmiany były oceniane, a nie przyjmowane w ciemno.
