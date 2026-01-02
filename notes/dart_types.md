```dart
// Prosty program w Dart
void main() {
  var user = User(name: 'Adrian', age: 25);
  user.greet();
}

class User {
  final String name;
  final int age;

  User({required this.name, required this.age});

  void greet() {
    print('Cześć, mam na imię $name i mam $age lat.');
  }
}
```
dsajfkdsjf