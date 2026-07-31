# Dane syntetyczne pod raporty Power BI Desktop

Wygenerowane 2026-07-31, gotowe do importu, żeby zbudować właściwe raporty
(`.pbix`) na podstawie mockupów w `docs/powerbi-mockups/*.html`. Wszystkie
liczby są syntetyczne (seed=42, powtarzalne) — nie ma tu żadnych prawdziwych
danych pracodawców ani prawdziwych osób.

## Equity Compensation / Vesting

- **`equity_participants.csv`** (480 wierszy) — uczestnicy planów: firma, kraj,
  data zatrudnienia.
- **`equity_vesting_events.csv`** (1900 wierszy) — pojedyncze zdarzenia
  vestingu: uczestnik, firma, typ planu (RSU/ESPP/SAYE), data, liczba akcji,
  cena, wartość, status (vested/upcoming).

Sugerowane wizualizacje w Power BI (odpowiadające mockupowi):
- Karty KPI: `SUM(value_usd)` filtrowane po `status` i dacie (ostatnie 12 mies. = odblokowana, upcoming = w oczekiwaniu)
- Wykres liniowy: skumulowana wartość odblokowana w czasie (`vest_date` na osi X)
- Wykres słupkowy: suma `value_usd` wg `plan_type`
- Tabela: top firmy wg `SUM(value_usd)`, nadchodzące zdarzenia (`status = upcoming`, sortowane po `vest_date`)

## Portfolio nieruchomości komercyjnych

- **`realestate_assets.csv`** (34 wiersze) — aktywa: typ, miasto, powierzchnia,
  wartość, obłożenie.
- **`realestate_leases.csv`** (~83 wiersze) — najmy per aktywo: najemca,
  czynsz roczny, data startu/końca (do harmonogramu wygaśnięcia).
- **`realestate_occupancy_trend.csv`** (12 wierszy) — trend obłożenia portfela
  w ostatnich 12 miesiącach.

Sugerowane wizualizacje:
- Karty KPI: `SUM(value_eur)`, `SUM(area_sqm)`, średnie `occupancy_pct`, liczba `lease_end` w najbliższych 12 mies.
- Wykres słupkowy: `SUM(value_eur)` wg `asset_type`
- Wykres liniowy: `occupancy_trend.csv` wprost
- Wykres słupkowy: `SUM(annual_rent_eur)` z `leases.csv` pogrupowane wg roku `lease_end`
- Tabela: top aktywa wg `value_eur`

## Jak zaimportować

Power BI Desktop → **Get Data → Text/CSV** → wskaż plik. Dla par plików
(`assets`+`leases`, `participants`+`vesting_events`) połącz je relacją po
kluczu (`asset_id`, `participant_id`) w widoku **Model**.
