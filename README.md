# Regex for Payment Card Bank Statement Lines

This is a regular expression for credit or debit card bank statement lines in
Czech:

```regex
(Nákup|Kredit|Výběr z bankomatu): (?<merchant>.+), (?<country>\w{2,3}), dne (?<day>[123]?\d).(?<month>1?\d).(?<year>2\d{3}), částka  (?<amount>\d+.\d{2})( (?<currency>\w{3}))?
```

- `(Nákup|Kredit|Výběr z bankomatu): ` is a constant identifying a payment card statement line
- `(?<merchant>.+), ` is the merchant provided string (name, address, postal code)
  - *Sometimes*, the name and address are separated with two spaces
- `(?<country>\w{2,3}), ` is a two- or three-letter ISO country code
- `dne ` is a constant preceeding the date triplet
- `(?<day>[123]?\d).` day number limited to 0-39 to avoid false positives
- `(?<month>1?\d).` month number limited to 0-19 to avoid false positives
- `(?<year>2\d{3})` year number limited to the 2000's to avoid false positives
- `, částka  ` is a constant preceeding the amount and currency code
- `(?<amount>\d+.\d{2}) ` is the amount with two decimal places precision
- `(?<currency>\w{3})` is the three letter currency code

## To-Do
