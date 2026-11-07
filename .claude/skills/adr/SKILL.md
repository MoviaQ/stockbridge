---
name: adr
description: Przygotowuje szkic nowego ADR (Architecture Decision Record) w docs/adr/. Użyj, gdy pojawia się decyzja architektoniczna z realną alternatywą, np. wybór kolejki, strategia retry, gdzie trzymać stan, co cache'ować.
---

# Nowy ADR

ADR to krótki zapis jednej decyzji: kontekst, wybór, odrzucone opcje, konsekwencje. Decyzję podejmuje człowiek. Agent pomaga ją sformułować.

## Kroki

1. Ustal z człowiekiem:
   - jaki problem wymaga decyzji (1–2 zdania),
   - **co najmniej dwie realne opcje**. Jeśli jest tylko jedna, to nie jest decyzja do ADR,
   - którą opcję człowiek wybiera i dlaczego, jego słowami.

2. Znajdź najwyższy numer w `docs/adr/` i nadaj kolejny (4 cyfry). Nazwa pliku: `NNNN-krotki-opis.md`.

3. Wypełnij szablon z `docs/adr/0000-szablon.md`. Status: `Proponowany`.

4. W sekcji „Konsekwencje” wpisz też **koszty** wybranej opcji. Decyzja bez kosztów jest podejrzana.

5. Jeśli decyzję da się zweryfikować pomiarem (np. scenariuszem black-friday), wpisz w sekcji „Jak sprawdzimy” co i jak zmierzymy.

6. Pokaż szkic człowiekowi. Status zmienia się na `Przyjęty` dopiero po jego akceptacji.

## Czego nie robić

- Nie wybieraj opcji za człowieka.
- Nie dopisuj opcji-słomianych kukieł tylko po to, żeby było ich więcej.
