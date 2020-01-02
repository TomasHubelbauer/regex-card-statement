# Regex for Payment Card Bank Statement Lines

This is a regular expression for credit or debit card bank statement lines in
Czech:

```regex
Nákup: (?<merchant>.+),  (?<address>.*), (?<zip>.*), (?<country>\w{3}), dne (?<day>[123]?\d).(?<month>1?\d).(?<year>2\d{3}), částka  (?<amount>\d+.\d{2}) (?<currency>\w{3})
```

- `Nákup: ` is a constant identifying a payment card statement line
- `(?<merchant>.+),  ` is the merchant provided name string
- `  ` two spaces separating the marchant provided name and address strings
- `(?<address>.*), ` is the merchant provided address string
- `(?<zip>.*), ` is the merchant provided postal code (free form)
- `(?<country>\w{3}), ` is a three-letter ISO country code
- `dne ` is a constant preceeding the date triplet
- `(?<day>[123]?\d).` day number limited to 0-39 to avoid false positives
- `(?<month>1?\d).` month number limited to 0-19 to avoid false positives
- `(?<year>2\d{3})` year number limited to the 2000's to avoid false positives
- `, částka  ` is a constant preceeding the amount and currency code
- `(?<amount>\d+.\d{2}) ` is the amount with two decimal places precision
- `(?<currency>\w{3})` is the three letter currency code
