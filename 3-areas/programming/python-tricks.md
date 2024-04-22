+++
date = 2024-04-22T19:50:00-00:00
+++

A set of tricks in Python that makes DSA questions easier.

### Accessing the last value of an array

`arr[-1]` is the same as `arr[len(arr) - 1]` and is an easier way to retrieve the last value. You can access other values backward using negative indexes.

### The `%` operator

This is not "module of". It's the remainder of the division operation with the same signal of the divisor. If the divisor is positive, the result will always be positive or zero. In the case below, `-1 % 10` returns `9` because `-1` divided by `10` equals `0` with a remainder of `-1`. Since the remainder should be positive or zero, Python returns `9` as the result.

```python
test = -1 % 10
print(test) # 9
```

This allows iterate 0, 1, 2, ..., 9, 0, 1, ... using this operator. The code below turns number strings from "0000" to "9999" this way.

```python
# current = "2301", i = 2
for diff in (-1,1):
    new_digit = (int(current[i]) + diff) % 10
    number = current[:i] + str(new_digit) + current[i+1:]
    print(number)
# diff = -1: 2391
# diff = 1: 2311
```

### Number/char conversion

When you have numerical representations of characters, you can use the following operations.

```python
# Considering 0 to 27 representation of 'a' to 'z'
# Retrieve the ordinal of the characters using 'a' as the base value
e = 4 # [a(0), b(1), c(2), d(3), e(4)]
print(chr(e + ord('a'))) # e
```

### Reversed string

Simply do `string[::-1]`.

### Comparing strings

To get the smallest string in the alphabetical order you can do `min(string1, string2)`.
