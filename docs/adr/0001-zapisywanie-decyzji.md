# 0001: Zapisujemy decyzje architektoniczne jako ADR

- **Status:** Przyjęty
- **Data:** 2026-11-07

## Kontekst

Projekt powstaje z pomocą agenta AI. Agent nie pamięta wcześniejszych rozmów, a ja za kilka miesięcy nie będę pamiętał, dlaczego coś zrobiłem w dany sposób. Na rozmowie rekrutacyjnej muszę umieć uzasadnić każdą decyzję.

## Rozważane opcje

1. **Brak zapisu** – decyzje tylko w commitach i rozmowach. Szybko, ale uzasadnienie ginie.
2. **Jeden długi dokument architektury** – wszystko w jednym miejscu, ale trudno zobaczyć, kiedy i dlaczego coś się zmieniło.
3. **ADR: jeden krótki plik na decyzję** – łatwo dopisać, historia zmian widoczna, agent może je przeczytać.

## Decyzja

Wybieramy ADR (opcja 3). Szablon: `0000-szablon.md`. Szkic przygotowuje skill `/adr`, decyzję podejmuję ja.

## Konsekwencje

- Każda ważna decyzja ma uzasadnienie i listę odrzuconych opcji.
- Koszt: kilka minut pisania przy każdej decyzji. Ryzyko, że zacznę pisać ADR-y do drobiazgów. Zasada: ADR tylko wtedy, gdy są co najmniej dwie realne opcje.

## Jak sprawdzimy

Po etapie v1: czy potrafię na podstawie samych ADR-ów wyjaśnić architekturę komuś, kto nie zna projektu.
