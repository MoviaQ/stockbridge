---
name: agent-log
description: Dodaje wpis do docs/agent-log.md, gdy agent popełnił błąd, który człowiek wykrył. Użyj, gdy człowiek wskaże błąd agenta lub gdy test/pomiar ujawni wadę w kodzie napisanym przez agenta.
---

# Wpis do dziennika błędów agenta

Dziennik to najważniejszy dowód w portfolio, że człowiek umie oceniać pracę agenta. Wpis musi być konkretny i uczciwy.

## Kroki

1. Zbierz fakty. Jeśli czegoś nie wiesz, zapytaj człowieka, nie zgaduj:
   - co agent zrobił (plik, fragment, krótko),
   - dlaczego to było złe (jaki scenariusz to psuje),
   - **jak to wykryto**: przegląd kodu, który test, który pomiar, z liczbami, jeśli są,
   - co zmieniono: kod, test, instrukcja w `CLAUDE.md` lub skillu.

2. Sprawdź, czy podobny błąd już jest w dzienniku. Jeśli tak, to jest drugi raz: zaproponuj **mocniejsze zabezpieczenie** niż kolejna linijka tekstu (test, reguła statyczna, skrypt). Kolejność siły: typy i struktura kodu → testy → skille i skrypty → tekst w CLAUDE.md.

3. Dopisz wpis na **początku** listy w `docs/agent-log.md`, w formacie:

```markdown
### AL-NNN: <krótki tytuł>
- **Data:** RRRR-MM-DD
- **Etap:** v1 / v2 / v3 / …
- **Co zrobił agent:** …
- **Dlaczego to błąd:** …
- **Jak wykryto:** …
- **Poprawka:** …
- **Zabezpieczenie na przyszłość:** test / reguła / zmiana w CLAUDE.md (link do pliku lub commita)
```

Numer NNN to kolejny po najwyższym istniejącym.

4. Pokaż wpis człowiekowi do akceptacji przed zapisem.

## Czego nie robić

- Nie łagodź opisu. „Agent zgubił idempotentność” jest lepsze niż „drobna nieścisłość”.
- Nie wpisuj błędów, których nikt nie wykrył w praktyce. Dziennik zawiera tylko rzeczy, które się wydarzyły.
