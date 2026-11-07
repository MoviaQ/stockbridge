# Ustalenia

Drobne decyzje i konwencje ustalone w rozmowach. Duże decyzje z alternatywami są w `docs/adr/`.

Wpisy dodaje skill `/zapisz-ustalenia`. Najnowsze na górze. Wpisów się nie usuwa, tylko oznacza jako zastąpione.

---

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
