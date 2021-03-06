# Two Sum III - Data structure design

Design and implement a TwoSum class. It should support the following operations: add and find.

* `add` - Add the number to an internal data structure.
* `find` - Find if there exists any pair of numbers which sum is equal to the value.

For example,
```
add(1); add(3); add(5);
find(4) -> true
find(7) -> false
```

**Solution:**
```java
public class TwoSum {
  private HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();

  public void add(int number) {
    if (map.containsKey(number)) {
      map.put(number, map.get(number) + 1);
    } else {
      map.put(number, 1);
    }
  }

  public boolean find(int value) {
    for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
      int key = entry.getKey();
      int idx = entry.getValue();

      int val = value - key;

      if (key != val && map.containsKey(val)) {
        return true;
      }

      if (key == val && map.get(key) > 1) {
        return true;
      }
    }

    return false;
  }
}
```