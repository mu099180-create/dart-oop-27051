# Dart OOP Assignment: Kigali Bus Card

**Name:** Mohamed Ahmed
**Student ID:** 27051

## My numbers
- D = 51, L = 1
- Starting balance = 1510 RWF
- Bus fare = 251 RWF
- Student discount = 11%

## Part 5
My prediction: the program prints 1 and then 5.

Why: For Bag a, add() makes _items 1. Then a.items = -5 is refused by the setter, because -5 is not >= 0, so _items stays 1 and it prints 1. For BigBag b, add() is overridden and calls super.add() two times, so every b.add() adds 2. Two calls make _items 4. Then b.items = b.items + 1 sets it to 5, because 5 is >= 0, so it prints 5.
