# 🇷🇴 Romanian Bond Market Data

Historical and daily trading data for bonds listed on the Bucharest Stock Exchange (BVB).

**Updated automatically** every business day.

---

## Available Data

| Path | Description | Updated |
|------|-------------|---------|
| `trading/YYYY-MM-DD.json` | Daily trading data (prices, volumes) | Mon-Fri ~18:30 EET |
| `bonds/{SYMBOL}.json` | Bond details + coupon schedules | Mon-Fri ~8:30 EET |
| `bonds-list.json` | Complete list of listed bonds | Mon-Fri ~8:00 EET |
| `index.json` | Data catalog (available dates, bonds) | Every update |

---

## Data Formats

### Trading Data — `trading/2026-02-05.json`

```json
{
  "date": "2026-02-05",
  "fetchedAt": "2026-02-05T17:05:00Z",
  "source": "BVB",
  "bondCount": 45,
  "bonds": [
    {
      "symbol": "R3512AE",
      "name": "MINISTERUL FINANTELOR",
      "market": "EREGT",
      "trades": 7,
      "volume": 40,
      "value": 20610.27,
      "open": 100.3389,
      "low": 100.3389,
      "high": 100.6979,
      "avg": 100.4585,
      "close": 100.6979,
      "refPrice": 100.3389,
      "changePercent": 0.36
    }
  ]
}
```

### Bond Details — `bonds/R3512AE.json`

```json
{
  "symbol": "R3512AE",
  "lastUpdated": "2026-02-09T08:00:00Z",
  "source": "BVB",
  "details": {
    "currency": "EUR",
    "couponRate": 5.0,
    "couponFrequency": 1,
    "faceValue": 1000,
    "maturityDate": "2035-12-17",
    "dayCountConvention": "ACT/ACT",
    "interestType": "fixed"
  },
  "couponDates": [
    { "date": "2026-12-17", "rate": 5.0, "number": 4 },
    { "date": "2027-12-17", "rate": 5.0, "number": 5 }
  ],
  "couponCount": 10
}
```

### Index — `index.json`

```json
{
  "lastUpdated": "2026-02-09T17:05:00Z",
  "tradingDates": {
    "count": 28,
    "first": "2026-01-02",
    "last": "2026-02-07"
  },
  "bondDetails": {
    "count": 85,
    "withCoupons": 72
  }
}
```

---

## Usage

### Raw URLs (GitHub)

```
https://raw.githubusercontent.com/florinc7474/ro-bond-history/main/trading/2026-02-05.json
https://raw.githubusercontent.com/florinc7474/ro-bond-history/main/bonds/R3512AE.json
https://raw.githubusercontent.com/florinc7474/ro-bond-history/main/bonds-list.json
https://raw.githubusercontent.com/florinc7474/ro-bond-history/main/index.json
```

### From code (Dart/Flutter)

```dart
final response = await http.get(Uri.parse(
  'https://raw.githubusercontent.com/florinc7474/ro-bond-history/main/trading/2026-02-05.json'
));
final data = jsonDecode(response.body);
```

---

## Data Source

All data comes from the [Bucharest Stock Exchange (BVB)](https://www.bvb.ro) with a 15-minute delay.

> ⚠️ This data is for informational purposes only. Not financial advice.

---

## License

Data sourced from BVB public feeds. This repository provides it in a structured JSON format for research and educational purposes.
