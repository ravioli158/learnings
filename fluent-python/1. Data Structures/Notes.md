# Python Data Model 

## What is it?
- The API that makes objects work with Python's idiomatic features
- Framework for how Python internally organizes and processes data
- Key to writing "Pythonic" code

## Core Concept
- Python uses special methods (dunder methods) with `__name__` format
- Interpreter automatically calls these methods for specific operations
- Example: `len(obj)` → calls `obj.__len__()` internally

## Why len(collection) not collection.len()?
- **Consistency**: Works uniformly across all types
- **Efficiency**: Optimized for built-in types
- **Flexibility**: Custom objects can implement `__len__()` to work with `len()`

## Common Special Methods

### Container Operations
- `__len__()` - Called by `len(obj)`
- `__getitem__(key)` - Called by `obj[key]`
- `__setitem__(key, value)` - Called by `obj[key] = value`
- `__contains__(item)` - Called by `item in obj`
- `__iter__()` - Called by `for item in obj`

### Arithmetic Operations
- `__add__(other)` - Called by `obj + other`
- `__sub__(other)` - Called by `obj - other`
- `__mul__(other)` - Called by `obj * other`

### String Representation
- `__str__()` - Called by `str(obj)` and `print(obj)`
- `__repr__()` - Called by `repr(obj)` (developer-friendly representation)

### Comparison Operations
- `__eq__(other)` - Called by `obj == other`
- `__lt__(other)` - Called by `obj < other`

## Key Benefits
1. **Consistency**: Custom objects behave like built-in types
2. **Intuitive**: Users can apply familiar operations to your objects
3. **Integration**: Objects work seamlessly with Python's syntax and built-in functions
4. **Expressiveness**: Creates clean, readable code

## Example
```
class MyCollection:
    def init(self, items):
    self.items = items

    def __len__(self):
        return len(self.items)

    def __getitem__(self, index):
        return self.items[index]

my_col = MyCollection()​
print(len(my_col)) # Works! Calls len()
print(my_col) # Works! Calls getitem()​

for item in my_col: # Works! Uses getitem()
print(item)
```

## Remember
- You don't need to call special methods directly (use `len(obj)` not `obj.__len__()`)
- Implement only the special methods you need
- The Data Model makes Python feel consistent and elegant