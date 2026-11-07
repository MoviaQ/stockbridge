---
name: zapisz-ustalenia
description: Zapisuje w docs/ ustalenia z bieżącej rozmowy, żeby nie przepadły między sesjami. Użyj zawsze i bez pytania, gdy człowiek podejmie decyzję, wybierze jedną z opcji, zaakceptuje propozycję, zmieni wcześniejsze ustalenie albo ukończy element planu. Użyj też przed zakończeniem dłuższej sesji, żeby sprawdzić, czy czegoś nie pominięto.
---

# Zapisz ustalenia

Agent nie pamięta poprzednich rozmów. Wie o projekcie tylko to, co jest w plikach. Ustalenie, które zostało tylko w rozmowie, następny agent zignoruje albo zrobi inaczej.

## Co jest ustaleniem

Zapisuj **tylko** to, co człowiek potwierdził:
- powiedział „tak”, „zgadzam się”, „robimy tak” na konkretną propozycję,
- sam podał decyzję lub wymaganie,
- wybrał jedną z przedstawionych opcji.

**Nie** zapisuj:
- własnych propozycji, na które człowiek nie odpowiedział,
- opcji, o których tylko rozmawialiście („może”, „rozważmy”, „zobaczymy”),
- swoich wniosków ani interpretacji, których człowiek nie potwierdził.

Jeśli nie wiesz, czy coś jest ustaleniem, zapytaj jednym zdaniem: „Czy mam to zapisać jako ustalenie: …?”

## Gdzie co zapisać

Każda informacja ma jedno miejsce. Nie powielaj jej w innych plikach.

| Rodzaj ustalenia | Miejsce |
|---|---|
| Drobna decyzja, konwencja, preferencja (np. nazewnictwo, język, narzędzie) | `docs/ustalenia.md` |
| Ukończony element planu | `docs/plan.md`: zaznacz checkbox |
| Nowy lub zmieniony element planu | `docs/plan.md` |
| Duża decyzja z co najmniej dwiema realnymi opcjami | nie zapisuj sam: zaproponuj `/adr` |

## Kroki

1. **Sformułuj ustalenie** w jednym lub dwóch zdaniach, jak najbliżej słów człowieka.

2. **Sprawdź, czy nie koliduje** z tym, co już jest w `docs/`. Przeszukaj pliki pod kątem tego samego tematu.
   - Jeśli koliduje: **zatrzymaj się i zapytaj**. Pokaż oba zapisy (stary z nazwą pliku i nowy) i zapytaj, który obowiązuje. Nie zmieniaj niczego, dopóki człowiek nie odpowie.
   - Jeśli nowe ustalenie świadomie zastępuje stare (człowiek to powiedział), oznacz stary wpis jako zastąpiony z odwołaniem do nowego. Nie usuwaj go.

3. **Sprawdź pliki, o których mowa.** Jeśli ustalenie wymienia plik lub katalog:
   - przy oznaczaniu czegoś jako zrobionego plik musi istnieć. Jeśli nie istnieje, nie zaznaczaj i powiedz o tym;
   - przy ustaleniu na przyszłość zapisz je jako planowane, nie jako stan obecny.

4. **Zapisz** w miejscu z tabeli. Format wpisu w `docs/ustalenia.md`:

   ```markdown
   ### U-NNN: <krótki tytuł>
   - **Data:** RRRR-MM-DD
   - **Ustalenie:** …
   - **Dlaczego:** … (powód podany przez człowieka; jeśli go nie podał, napisz „nie podano”)
   - **Status:** obowiązuje | zastąpione przez U-NNN
   ```

   NNN to kolejny numer po najwyższym istniejącym. Nowe wpisy na górze.

5. **Poinformuj** jednym zdaniem w odpowiedzi: co zapisałeś i w którym pliku. Na przykład: „Zapisałem U-004 (testy w JUnit 5) w docs/ustalenia.md.”

## Nie wolno

- Zmieniać przyjętych ADR-ów (`docs/adr/` ze statusem Przyjęty).
- Zmieniać wpisów w `docs/agent-log.md`.
- Zmieniać kontraktów w `contracts/`.
- Usuwać istniejących ustaleń. Można je tylko oznaczyć jako zastąpione.
- Dopisywać rzeczy, których człowiek nie powiedział, „żeby było pełniej”.
