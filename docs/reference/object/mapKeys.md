# mapKeys

Creates a new object with the same values as the given object, but with keys generated by running each own enumerable property of the object through the `getNewKey` function.

## Signature

```typescript
function mapKeys<T extends Record<PropertyKey, any>, K extends PropertyKey>(
  object: T,
  getNewKey: (value: T[keyof T], key: keyof T, object: T) => K
): Record<K, T[keyof T]>;
```

### Parameters

- `obj` (`T extends Record<PropertyKey, any>`): The object to iterate over.
- `getNewKey`: (`(value: T[keyof T], key: keyof T, object: T) => K`): The function invoked per own enumerable property.

### Returns

(`Record<K, T[keyof T]>`): The new mapped object.

## Examples

```typescript
const obj = { a: 1, b: 2 };
const result = mapKeys(obj, (value, key) => key + value);
console.log(result); // { a1: 1, b2: 2 }
```

## Performance Comparison

|                   | [Bundle Size](../../bundle-size.md) | [Performance](../../performance.md) |
| ----------------- | ----------------------------------- | ----------------------------------- |
| es-toolkit        | 138 bytes (99.1% smaller)           | 2,844,013 times (11% faster)        |
| es-toolkit/compat | 1,124 bytes (93.2% smaller)         | 2,899,524 times (13% faster)        |
| lodash-es         | 16,649 bytes                        | 2,559,949 times                     |
