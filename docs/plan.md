# Plan projektu

## Problem

Każdy kanał sprzedaży (Allegro, Zalando, własny sklep) trzyma własną kopię liczby dostępnych sztuk i sam decyduje o sprzedaży. O sprzedaży dowiadujemy się po fakcie. Czas między sprzedażą w jednym kanale a aktualizacją pozostałych to **okno niespójności**. Każda sprzedaż w tym oknie może być oversellingiem.

Tego nie da się zablokować, bo decyzję o sprzedaży podejmuje kanał. Da się:

1. **skrócić okno**: szybciej dowiadywać się o sprzedaży i rozsyłać stany,
2. **nic nie zgubić**: zgubione zdarzenie = kanał nigdy nie dostanie aktualizacji,
3. **zostawić margines**: bufor bezpieczeństwa,
4. **wykryć i naprawić** to, co i tak się zdarzy.

Cel: overselling rzadko, zawsze wykryty, automatycznie obsłużony. Zero zgubionych zamówień.

## Wersje

Każda wersja kończy się pomiarem tym samym scenariuszem (`load-test/`) i wpisem w `docs/results.md`. Każda ma tag w gicie (`v1`, `v2`, `v3`).

### v1: naiwna (listopad – grudzień)
- [ ] Symulator ERP w SOAP: kontrakt WSDL, regulowane opóźnienie, procent błędów, wyłączenie
- [ ] Integration Service: odbiór zamówień przez REST, zapis w PostgreSQL, synchroniczne wywołanie ERP
- [ ] Symulatory kanałów: własna kopia stanu, sprzedaż według niej, duplikaty zdarzeń
- [ ] Synchronizacja stanów do kanałów co 15 minut
- [ ] Scenariusz black-friday i pierwszy pomiar

### v2: kolejka (styczeń)
- [ ] RabbitMQ: ack, retry z rosnącą przerwą, DLQ
- [ ] Outbox
- [ ] Idempotentność zdarzeń
- [ ] Rozsyłanie stanów do kanałów po każdej sprzedaży
- [ ] Test: ERP wyłączony na 60 s, żadne zamówienie nie ginie
- [ ] Pomiar

### v3: wykrywanie, bufor, cache (luty)
- [ ] Wspólny licznik z atomową aktualizacją + test współbieżny
- [ ] Wykrywanie oversellingu i automatyczna kompensacja
- [ ] Bufor bezpieczeństwa (decyzja w ADR)
- [ ] Redis: katalog z ERP, mapowanie SKU → oferta, token
- [ ] Okresowa synchronizacja z ERP i unieważnianie cache
- [ ] Pomiar

### Prawdziwy świat (marzec)
- [ ] Integracja z sandboxem Allegro (szczegóły API sprawdzić w dokumentacji Allegro)
- [ ] Metryki: Micrometer, Prometheus, Grafana
- [ ] Mutation testing (PIT), CI w GitHub Actions
- [ ] Porządki w README, ADR-ach, agent-log

### Opcjonalnie (kwiecień – czerwiec)
- [ ] Apache Camel albo Kafka
- [ ] Dopasowanie ofert do produktów z użyciem LLM, z zestawem testowym i pomiarem trafności

## Mierniki

| Miernik | Definicja |
|---|---|
| Oversell | Liczba sprzedanych sztuk ponad dostępny stan |
| Wykryte automatycznie | Odsetek oversellingów zauważonych przez system |
| Okno niespójności (p95) | Czas od sprzedaży do aktualizacji stanu w pozostałych kanałach |
| Utracone zamówienia | Przyjęte przez kanał, nigdy nie dotarły do ERP |
| Zdublowane zamówienia | To samo zamówienie w ERP więcej niż raz |
