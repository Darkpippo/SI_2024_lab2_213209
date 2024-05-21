# SI_2024_lab2_213209
Александар Пановски 213209

2. ![ControlFlowDiagram](ControlFlowDiagram.svg)
3. Цикломатска комплексност: Цикломатската комплексност на овој код е 6, истата ја добив преку формулата: V(B) = E - N + 2P, каде што Е е бројот на ребра и изнесува 20, N e бројот на јазли и изнесува 16, а P е бројот на предикатни јазли и во овој случај изнесува 1.
4. Тест случаи според критериумот Every branch:

- Случај каде allItems e null и не се задоволени барањата
assertThrows(RuntimeException.class, () -> SILab2.checkCart(null, 50));

- Случај каде item.name e null и не се задоволени барањата
items.add(new Item(null, "123456", 100, 0));
assertTrue(SILab2.checkCart(items, 100));

- Случај каде item без баркод
items.add(new Item("Item1", null, 100, 0));
assertThrows(RuntimeException.class, () -> SILab2.checkCart(items100));

- Случај каде item е со невалиден баркод
items.add(new Item("Item1", "123abc", 100, 0));
assertThrows(RuntimeException.class, () -> SILab2.checkCart(items, 100));

- Случај каде се проверува checkCart со валиден item
items.add(new Item("Item1", "123456", 100, 0));
assertTrue(SILab2.checkCart(items, 100));

- Случај каде item се проверува дали има валиден discount(float)
items.add(new Item("Item1", "123456", 100, 0.1f));
assertTrue(SILab2.checkCart(items, 90));

- Случај каде сумата на кошничката е помала од плаќањето
items.add(new Item("Item1", "123456", 100, 0));
assertFalse(SILab2.checkCart(items, 50));

- Случај каде одреден item има специјален discount
items.add(new Item("Item1", "012345", 400, 0.1f));
assertTrue(SILab2.checkCart(items, 360));

5. Multiple Condition

- Тест случај каде сите се true
Item item = new Item("Item1", "012345", 400, 0.1f);
assertTrue(checkCondition(item));

- Тест случај каде првиот услов е false другите се true
Item item = new Item("Item1", "012345", 200, 0.2f);
assertFalse(checkCondition(item));

- Тест случај каде вториот услов е false другите се true
Item item = new Item("Item1", "012345", 400, 0);
assertFalse(checkCondition(item));

- Тест случај каде третиот услов е false другите се true
Item item = new Item("Item1", "123456", 400, 0.1f);
assertFalse(checkCondition(item));

- Тест случај каде првиот и вториот услов се false а другите true
Item item = new Item("Item1", "012345", 200, 0);
assertFalse(checkCondition(item));

- Тест случај каде првиот и третиот услов се false а другите true
Item item = new Item("Item1", "123456", 400, 0.2f);
assertFalse(checkCondition(item));

- Тест случај каде вториот и третиот услов се false а другите true
Item item = new Item("Item1", "123456", 400, 0);
assertFalse(checkCondition(item));

- Тест случај каде сите се false
Item item = new Item("Item1", "123456", 200, 0);
assertFalse(checkCondition(item));