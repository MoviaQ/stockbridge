# Stockbridge

Warstwa integracyjna między starym systemem ERP a kanałami sprzedaży (własny sklep, Allegro, Zalando).

Co robi:

1. **Przyjmuje zamówienia ze wszystkich kanałów i dostarcza je do ERP.** Bez gubienia i bez duplikatów, także wtedy, gdy ERP nie odpowiada.
2. **Rozsyła stany magazynowe do kanałów.** Szybko, z buforem bezpieczeństwa.
3. **Tłumaczy między systemami.** REST i JSON po stronie kanałów, SOAP i XML po stronie ERP, numery ofert na SKU i odwrotnie.
4. **Pilnuje spójności danych.** Wykrywa rozjazdy między systemami i reaguje na nie.
5. **Jest odporny na awarie.** Ponawia operacje, odkłada nieudane wiadomości do DLQ, udostępnia metryki.

Najtrudniejszy scenariusz, na którym system jest mierzony, to **overselling**. Każdy kanał trzyma własną kopię stanu i sprzedaje według niej. Gdy zostaje ostatnia sztuka, dwa kanały potrafią sprzedać ją jednocześnie.

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
