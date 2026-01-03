```dart
// String -> int
var one = int.parse('1');
assert(one == 1);
​
// String -> double
var onePointOne = double.parse('1.1');
assert(onePointOne == 1.1);
​
// int -> String
String oneAsString = 1.toString();
assert(oneAsString == '1');
​
// double -> String
String piAsString = 3.14159.toStringAsFixed(2);
assert(piAsString == '3.14');
```
Jeśli chcemy zmienić łańcuch znaków na wartość liczbowa używamy metody `parse()` natomiast jak chcemy w drugą stronę używamy metody `toString()`.


W Dart działaja operacje bitowe 
```dart
assert((3 << 1) == 6); // 0011 << 1 == 0110
assert((3 | 4) == 7); // 0011 | 0100 == 0111
assert((3 & 4) == 0); // 0011 & 0100 == 0000
```

 `(3 << 1) == 6`
   
`3` to binarnie `0011`.
`<< 1` przesuwa bity w lewo o `1` pozycję:
`0011 → 0110`, czyli `6`.


`(3 | 4) == 7`

`3 = 0011`, `4 = 0100`.
`|` to OR bitowy:
bit = 1, jeśli którykolwiek bit jest 1.
`0011 | 0100 = 0111`, czyli `7`.

`(3 & 4) == 0`
`&` to AND bitowy:
bit = 1 tylko jeśli oba bity są 1.
`0011 & 0100 = 0000`, czyli 0.


Liczby zapisuje sie z separatora tysięcy `_`

```dart
var n1 = 1_000_000;
var n2 = 0.000_000_000_01;
var n3 = 0x00_14_22_01_23_45; // MAC address
var n4 = 555_123_4567; // US Phone number
var n5 = 100__000_000__000_000; // one hundred million million!
```


