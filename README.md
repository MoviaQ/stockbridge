# Ostatnia sztuka

Sklep sprzedaje tę samą kurtkę w trzech miejscach: we własnym sklepie, na Allegro i na Zalando. Każdy z tych kanałów trzyma własną kopię stanu magazynowego i sprzedaje według niej. Gdy zostaje ostatnia sztuka, dwa kanały potrafią sprzedać ją jednocześnie.

Ten projekt to warstwa integracyjna między kanałami sprzedaży a systemem ERP. Ma sprawić, żeby:

- sprzedaż nieistniejącej sztuki zdarzała się rzadko,
- każdy taki przypadek był wykryty i obsłużony automatycznie,
- żadne zamówienie nie zginęło, nawet gdy ERP nie odpowiada.

Projekt jest edukacyjny. Marka i scenariusz są wymyślone.

## Status

Etap 0: przygotowanie repozytorium. Nie ma jeszcze kodu do uruchomienia.

Plan etapów: [docs/plan.md](docs/plan.md).

## Jak to jest budowane

Projekt powstaje we współpracy z agentem AI (Claude Code). Podział ról jest jawny:

- kontrakty (`contracts/`), decyzje architektoniczne (`docs/adr/`) i testy scenariuszy awarii piszę sam,
- agent implementuje według nich, a każda zmiana przechodzi pętlę review i musi mieć dowody: testy, pomiary, wyniki uruchomień,
- błędy agenta, które wykryłem, i to, jak je wykryłem, są w [docs/agent-log.md](docs/agent-log.md),
- zasady pracy agenta: [CLAUDE.md](CLAUDE.md) i `.claude/skills/`.

## Wyniki

Pomiary scenariusza „Black Friday” dla kolejnych wersji pojawią się w `docs/results.md`.
