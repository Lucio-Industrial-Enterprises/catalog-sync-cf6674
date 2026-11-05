# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in dollars. Zones are `local` and `regional`; weights must be positive.

| Service    | Local base | Regional base | Express surcharge |
|------------|-----------|---------------|-------------------|
| `standard` | $5.00     | $8.00         | —                 |
| `express`  | $5.00     | $8.00         | +$7.00            |

Rate = base + $1.50 × weight\_kg (+ $7.00 for express).

The CLI accepts an optional `--service` flag:

```
python -m warehouse.cli 2 local                    # $8.00
python -m warehouse.cli 2 local --service express  # $15.00
```
