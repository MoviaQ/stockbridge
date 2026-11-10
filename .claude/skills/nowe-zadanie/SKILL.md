---
name: nowe-zadanie
description: Rozpoczęcie nowego zadania w projekcie Stockbridge. Użyj na początku każdej nowej funkcji, modułu lub poprawki, zanim powstanie jakikolwiek kod. Ustala kryteria poprawności, zanim agent zacznie implementację.
---

# Nowe zadanie

Cel: zanim powstanie kod, człowiek i agent zgadzają się, **po czym poznamy, że jest dobrze**.

## Kroki

1. **Opisz zadanie własnymi słowami** w 2–3 zdaniach. Zapytaj, czy dobrze rozumiesz.

2. **Sprawdź kontrakt.** Czy zadanie dotyczy interfejsu z `contracts/`? Jeśli tak, a kontraktu brakuje lub jest niepełny, zatrzymaj się: kontrakt pisze człowiek. Możesz zaproponować szkic, ale wyraźnie oznaczony jako propozycja.

3. **Ustal kryteria akceptacji** jako listę konkretnych, sprawdzalnych zdań, np.:
   - „Dwa równoległe zamówienia na ostatnią sztukę dają licznik -1, a nie 0.”
   - „To samo zdarzenie wysłane dwa razy tworzy jedno zamówienie.”
   - „Gdy ERP nie odpowiada przez 60 s, żadne zamówienie nie ginie.”

   Dla każdego kryterium zapytaj: **co się stanie, gdy coś padnie w połowie?** (sieć, baza, kolejka, restart aplikacji). Jeśli odpowiedź nie jest oczywista, to jest brakujące kryterium.

4. **Ustal, kto pisze które testy.** Testy scenariuszy awarii i współbieżności pisze człowiek albo przynajmniej zatwierdza ich treść przed implementacją. Zaproponuj, jak taki test mógłby wyglądać (opis, nie gotowy kod), jeśli człowiek o to poprosi.

5. **Podziel pracę na kroki** po maksymalnie ~100 linii zmian każdy. Każdy krok kończy się czymś, co da się uruchomić lub przetestować.

6. **Wskaż, czego człowiek się tu nauczy**: jedno pojęcie lub mechanizm, który warto zrozumieć (i gdzie o nim przeczytać, jeśli to temat z DDIA, patrz `docs/notes/README.md`).

7. Podsumuj ustalenia w jednym bloku i **poczekaj na akceptację**, zanim zaczniesz implementację.

## Czego nie robić

- Nie zaczynaj pisać kodu w tym samym kroku, w którym ustalasz kryteria.
- Nie wymyślaj kryteriów, które da się spełnić bez sprawdzania czegokolwiek („kod jest czytelny”).
