You can use the following formula to give sortable IPV4 addresses in Excel (or similar)

```
=join(".", arrayformula(text(split(A2, "."), "000")))
```
