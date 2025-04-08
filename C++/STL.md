### Vector

- `for (int i : v)` << 迭代 v.size() 次，i 是第 n 個元素本人

### Map

- map 的 value 會有初始值，根據 type 而定，比如 integer 就是 0

### Sort
- ```
``` c++ = 
std::sort(vector.begin(), vector.end(), \[\](auto &a, auto &b) { return a > b })
```
- lambda 寫法，a 是前面的元素，所以就看要大的在前面還小的在前面