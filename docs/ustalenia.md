# Ustalenia

Drobne decyzje i konwencje ustalone w rozmowach. Duże decyzje z alternatywami są w `docs/adr/`.

Wpisy dodaje skill `/zapisz-ustalenia`. Najnowsze na górze. Wpisów się nie usuwa, tylko oznacza jako zastąpione.

---

### U-008: Nazwa projektu Stockbridge i szerszy zakres
- **Data:** 2026-11-10
- **Ustalenie:** Projekt nazywa się Stockbridge (repo `MoviaQ/stockbridge`). System to warstwa integracyjna z pięcioma obszarami odpowiedzialności (`docs/plan.md`, „Zakres systemu”), a overselling jest głównym scenariuszem testowym, nie całym zakresem.
- **Dlaczego:** „Ostatnia sztuka to nie jest jakaś fajna nazwa”; system nie mówi tylko o oversellingu.
- **Status:** obowiązuje

### U-007: Zakaz komentarzy w kodzie
- **Data:** 2026-11-07
- **Ustalenie:** Modele nie piszą żadnych komentarzy w kodzie. Zasada w `CLAUDE.md`, sekcja „Komentarze w kodzie”.
- **Dlaczego:** nie podano
- **Status:** obowiązuje

### U-006: Zawsze dowody pracy
- **Data:** 2026-11-07
- **Ustalenie:** Właściciel chce mieć zawsze przedstawione dowody pracy agenta. Zasada w `CLAUDE.md`, sekcja „Raportowanie”.
- **Dlaczego:** nie podano
- **Status:** obowiązuje

### U-005: Człowiek nie przegląda każdej zmiany; artefakt zmiany przed PR
- **Data:** 2026-11-07
- **Ustalenie:** Człowiek nie przegląda ręcznie każdej zmiany. Przed otwarciem PR i pierwszymi rundami `/code-review` agent generuje artefakt: co się zmieniło, w jaki sposób, z dowodami. Szczegóły: `docs/review.md`, krok 3.
- **Dlaczego:** „W dzisiejszych czasach to nie ma sensu.”
- **Status:** obowiązuje

### U-004: Delegowanie kodowania do subagentów według trudności
- **Data:** 2026-11-07
- **Ustalenie:** Zadania z kodowania agent deleguje do subagentów na modelu `haiku` albo `sonnet`, zależnie od trudności zadania. Szczegółowe zasady: `CLAUDE.md`, sekcja „Delegowanie kodowania do subagentów”.
- **Dlaczego:** nie podano
- **Status:** obowiązuje

### U-003: Review przez PR i pętlę /code-review
- **Data:** 2026-11-07
- **Ustalenie:** Zmiana idzie jako PR do review. Review robi `/code-review` na poziomie `low` albo `medium`, nic wyżej. Po poprawkach review się powtarza, dopóki nie zostaną tylko małe uwagi. Szczegóły: `docs/review.md`.
- **Dlaczego:** nie podano
- **Status:** obowiązuje

### U-002: Agent zapisuje ustalenia sam, ale zatrzymuje się przy sprzecznościach
- **Data:** 2026-11-07
- **Ustalenie:** Agent sam zapisuje ustalenia z rozmowy w `docs/`, bez pytania o zgodę. Gdy nowe ustalenie koliduje z istniejącym zapisem, zatrzymuje się i pyta. Nie zmienia przyjętych ADR-ów, dziennika błędów agenta ani kontraktów.
- **Dlaczego:** Żeby informacje z rozmów nie ginęły między sesjami.
- **Status:** obowiązuje

### U-001: Język dokumentacji i kodu
- **Data:** 2026-11-07
- **Ustalenie:** Dokumentacja po polsku. Kod, nazwy klas, metod, tabel i commity po angielsku.
- **Dlaczego:** nie podano (założenie agenta, zaakceptowane bez sprzeciwu)
- **Status:** obowiązuje
