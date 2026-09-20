# WinOLS Log Analysis Session Status

## Source log

- `2026-09-19-231734.csv`
- Location: this directory
- Delimiter: semicolon (`;`)
- 8,824 data rows plus header

## Main identified pull

The requested second full-throttle pull is:

- Source data rows: file lines 734–902 inclusive
- Time: `75625`–`92703` ms (`77.2`–`92.7` s)
- Driver wish: approximately `99.9927%`
- Engine speed: `1562.9`–`3942.94` rpm
- Actual injection quantity: `STAT_EINSPRITZMENGE_AKTUELL_WERT`
- Air mass per cycle: `STAT_LUFTMASSE_PRO_HUB_WERT`
- Actual boost: `STAT_LADEDRUCK_WERT`
- Turbo-vane value: `STAT_PCR_rBPA_WERT`

## Generated files

- `2026-09-19-231734-second-100pct-driver-wish-run-to-4000rpm-with-transients.csv`
  - 100 data rows before the pull
  - 169 pull rows
  - 100 data rows after the pull
  - 369 data rows total
- `2026-09-19-231734-calculated-afr-smoke-risk.png`
  - Whole-log AFR, boost, air mass, and RPM plot
  - Red shading marks calculated AFR <= 16.5
- `2026-09-19-231734-second-pull-AFR-below-16.5.csv`
  - 154 rows from the second pull with calculated AFR < 16.5

## Calculations

Calculated AFR:

```text
AFR = STAT_LUFTMASSE_PRO_HUB_WERT / STAT_EINSPRITZMENGE_AKTUELL_WERT
```

Assumed smoke-free threshold: `AFR = 16.5`.

For lambda using diesel stoichiometric AFR approximately `14.5`:

```text
lambda = calculated AFR / 14.5
```

Air-mass plausibility used 500 cc per cylinder per cycle for the 3.0 L six-cylinder engine, ideal-gas comparison against logged absolute boost pressure and intake temperature.

## Key findings

- Maximum actual rail pressure in the saved fragment: `742.778`.
- Maximum actual rail pressure in the full log: `764.781`.
- Maximum rail-pressure requested/Soll value in the second pull: `674.967`.
- Minimum calculated AFR in the second pull: `14.772`.
- Minimum AFR occurs at:
  - Time: `78219` ms
  - RPM: `2028.91`
  - Injection: `78.3294` mg/cycle
  - Air mass: `1157.11` mg/cycle
  - Actual boost: `2533.92` mbar absolute
  - Driver wish: `99.9927%`
- Second pull AFR remains below `16.5` from approximately `1805` rpm through `3943` rpm, with a brief earlier threshold crossing at `1805` rpm.
- Long-pull AFR is generally approximately `15.9–16.1` after the 2,100 rpm transient.
- The air-mass data is broadly plausible for the engine; the data points more strongly toward a low smoke margin/overfueling or transient fueling issue than a clearly proven major intake leak.

## Important interpretation note

The logged air-mass and injection quantities are treated as comparable mg-per-cylinder-cycle values. AFR here is a calculated proxy, not a measured exhaust lambda value. Boost values are logged absolute pressure in mbar, not gauge pressure.

## Resume commands

Use the source CSV and generated files in this directory. The second pull can be selected with:

```text
time >= 75625 and time <= 92703
```

Relevant columns:

```text
STAT_MOTORDREHZAHL_WERT
STAT_EINSPRITZMENGE_AKTUELL_WERT
STAT_LUFTMASSE_PRO_HUB_WERT
STAT_LADEDRUCK_WERT
STAT_LADEDRUCK_SOLL_WERT
STAT_PCR_rBPA_WERT
STAT_FAHRERWUNSCH_PEDAL_WERT
STAT_LADELUFTTEMPERATUR_WERT
STAT_RAILDRUCK_WERT
STAT_RAILDRUCK_SOLL_WERT
```
