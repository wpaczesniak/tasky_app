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

### String wieloliniowy

Potrójny cudzysłów (''' albo """) Oznacza w jezyku Dart:
„to ma być jeden String, ale z łamaniami linii dokładnie takimi jak w kodzie”.

```dart
var s1 = '''
You can create
multi-line strings like this one.
''';
```

### Raw string (r'...')

Prefiks r oznacza raw string, czyli:

- brak ucieczek

- brak interpretacji \n, \t, \uXXXX, itd.

```dart
var s = r'In a raw string, not even \n gets special treatment.';
```

Wykorzystuje sie je
gdy mamy:

- regexy (wyrazenia regularne)

- ścieżki plików (C:\Users\...)

- tekst z masą backslashy

- cokolwiek, gdzie `\` ma pozostać `\`

### compile-time constant
To znaczy:
wartość musi być znana zanim program w ogóle ruszy.
Kompilator musi być w stanie ją policzyć bez uruchamiania aplikacji.

**const String**

**String** jest stałą kompilacyjną, jeśli:

sam jest **const**

wszystko, co interpolujesz **($...)** też jest **const**

interpolowane wartości są: **null, num, bool, String** Natomiast List nie jest dozwolona w interpolacji bo ma to uniknac na pozwalanie na wstawianie innych rodzajów elementów różnego typu. 
Interpolacja to po prostu wkładanie wartości do tekstu, żeby nie sklejać wszystkiego ręcznie.

```dart
// These work in a const string.
const aConstNum = 0;
const aConstBool = true;
const aConstString = 'a constant string';

// These do NOT work in a const string.
var aNum = 0;
var aBool = true;
var aString = 'a string';
const aConstList = [1, 2, 3];

const validConstString = '$aConstNum $aConstBool $aConstString';
// const invalidConstString = '$aNum $aBool $aString $aConstList';

```

Interpolacja pozwala na uniknięcie sklejania 


```dart
var imie = 'Ania';
print('Cześć, mam na imię ' + imie + '.');
```

Z interpolacją

```dart
var imie = 'Ania';
print('Cześć, mam na imię $imie.');
```

### `const` a `final`

**const**
- wartość znana w czasie kompilacji
- obiekt jest całkowicie niezmienny
- kompilator może go współdzielić i optymalizować


**final**
- przypisujesz raz
- wartość ustalana w runtime
- obiekt może być mutowalny

Podsumowanie `const` i `final` 
- `const` = stała znana przed startem programu
- `final` = przypisana raz, ale dopiero po starcie

We Flutterze często zobaczymy widgety `const` ze względu na:
- widgety const nie są przebudowywane
- mniejsze zużycie pamięci
- szybszy rebuild

### Runa

Oznaczają punkt kodowy Unicode
Co to znaczy
- Tekst (String) to znaki.
- Unicode nadaje każdemu znakowi numer.