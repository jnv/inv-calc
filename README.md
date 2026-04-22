# Investiční modelář

## Query parametry URL

Aplikace ukládá stav formuláře do URL query stringu. Parametry:

- `modelName` - Název modelu. Formát: `text (string)`.
- `initial` - Počáteční investice. Formát: `číslo (Kč)`.
- `monthly` - Měsíční vklad. Formát: `číslo (Kč)`.
- `years` - Horizont. Formát: `číslo (roky)`.
- `fee` - Roční poplatek. Formát: `číslo (% p.a.)`.
- `buyFee` - Nákupní poplatek. Formát: `číslo (%)`.
- `inflation` - Inflace. Formát: `číslo (% p.a.)`.
- `tax` - Daň při výběru ze zisku. Formát: `číslo (%)`.
- `timing` - Připisování měsíčního vkladu. Formát: `výběr (start | end)`.
  - `start` - Příspěvek se připíše na začátku měsíce.
  - `end` - Příspěvek se připíše na konci měsíce.
- `kickbackPct` - Kickback. Formát: `číslo (%)`.
- `kickbackEveryYears` - Perioda kickbacku. Formát: `číslo (roky)`.
- `kickbackBase` - Základ kickbacku. Formát: `výběr (fees | contributions | portfolio)`.
  - `fees` - Kickback se počítá z uhrazených nákupních poplatků za dané období.
  - `contributions` - Kickback se počítá z nominálních vkladů za dané období.
  - `portfolio` - Kickback se počítá z aktuální hodnoty portfolia v okamžiku připsání.
- `rate1` - Konzervativní scénář výnosu. Formát: `číslo (% p.a.)`.
- `rate2` - Střední scénář výnosu. Formát: `číslo (% p.a.)`.
- `rate3` - Optimistický scénář výnosu. Formát: `číslo (% p.a.)`.
- `withdrawals` - Jednotlivé výběry. Formát: více řádků `měsíc,částka` (částka je čistý výběr v Kč po dani):

  ```text
  měsíc,částka
  měsíc,částka
  ```

- `recStart` - Opakované výběry od měsíce. Formát: `číslo (měsíc)`.
  Měsíc je pořadí v celé simulaci (`1..N`), ne kalendářní měsíc `0..11`.
- `recEvery` - Interval opakovaných výběrů. Formát: `číslo (měsíce)`.
- `recAmount` - Čistý opakovaný výběr. Formát: `číslo (Kč)`.
- `recEnd` - Opakované výběry do měsíce. Formát: `číslo (měsíc)`.
  Měsíc je pořadí v celé simulaci (`1..N`), ne kalendářní měsíc `0..11`.

Příklad URL:

```text
?modelName=Muj+scenar&years=30&monthly=10000&timing=end&withdrawals=60%2C50000%0A120%2C200000
```
