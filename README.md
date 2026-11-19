# Dart OOP Assignment: Kigali Bus Card

**Name:** Mohamed Ahmed

**Student ID:** 27051

## My numbers
- D = 51, L = 1
- Starting balance = 1510 RWF
- Bus fare = 251 RWF
- Student discount = 11%

## Output of main.dart
```
Error: name too short
Owner: Mohamed | Balance: 1510 RWF
Owner: Mohamed Ahmed | Balance: 1510 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 251 RWF
Paid 251 RWF
Owner: Mohamed Ahmed | Balance: 3008 RWF
Student discount: 27 RWF
Paid 224 RWF
Owner: Mohamed Ahmed | Balance: 1286 RWF
Student card: 11% off
```

## Part 1: Why no setter for balance?
If balance had a setter, anyone could write card.balance = 1000000 and give themselves free money. Without a setter, the balance can only change through topUp, which accepts only 500 to 50000 RWF, and pay, which declines the payment when the fare is more than the balance. So the money on the card stays safe.

## Part 2: What does ~/ do?
The ~/ operator is integer division. It divides and cuts off the decimal part, with no rounding. print(237 * 17 / 100); prints 40.29 because normal division keeps the decimals. print(237 * 17 ~/ 100); prints 40 because ~/ keeps only the whole part.

## Part 4: Bug table

| Bug | The line | Why it is wrong | My fix |
|---|---|---|---|
| 1 | `String _brand;` and `int _battery;` | The fields have no starting value, and a String or an int cannot be null in Dart. | `String _brand = '';` and `int _battery = 0;` |
| 2 | `SmartPhone(String brand, int battery, String system) {` | The constructor does not build the parent Phone first, and Phone has no empty constructor. | Added `: super(brand, battery)` |
| 3 | `@override` above `void restart()` | @override only works if the parent has that method, and Phone has no restart(). | Removed `@override` |
| 4 | `p.battery = 100;` | Phone has a getter for battery but no setter, so the value cannot be changed. | Added `set battery(int value)` that accepts only 0 to 100 |
| 5 | `print(p.battery());` | battery is a getter, not a method, so it must not have brackets. | `print(p.battery);` |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | The word new is optional in Dart, so the line works with it or without it. | (none) |

## Part 5
My prediction: the program prints 1 and then 5.

Why: For Bag a, add() makes _items 1. Then a.items = -5 is refused by the setter, because -5 is not >= 0, so _items stays 1 and it prints 1. For BigBag b, add() is overridden and calls super.add() two times, so every b.add() adds 2. Two calls make _items 4. Then b.items = b.items + 1 sets it to 5, because 5 is >= 0, so it prints 5.

Real output:
```
1
5
```

Was I right? Yes, my prediction was right.
