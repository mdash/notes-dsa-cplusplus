## Hash tables
- hash table goal is key to value mapping (fast and efficient)
- e.g. dictionary in python or JS
- Create a function that matches every possible input to a fixed size output
- three things required
    - hash function that maps input to fixed sized output
    - array that stores the actual data 
    - what to do for collisions (different keys point to the same value)
## Good hash functions
- Ideal hash function maps every single key to value (mathematically onto function)
- A hash function should work well for all key spaces
- A hash function has 2 parts
    - A Hash: transform input to integer value
    - Compression: Fit it into a finite space. e.g. using mod operator
- 3 components
    - Should run in Constant time to compute hash
    - Should be deterministic 
    - Satisfy SUHA: given 2 values a and b, P(h(a) = h(b)) = 1/N (uniformly distributed and not bunched up in certain output spaces)
- Easier to use established hash functions because it's very easy to satisfy every possible expected value in the user space during runtime 
## Collision
- Separate chaining
    - Just keep adding to the same key in linked list 
    - Where to insert it into the linked list as quickly as possible? - insert at beginning - since O(1) time complexity
    - Problem is if you want to find something in the linked list, it will run in O(n) time
- Probe based hashing
    - Store in Array instead of linked list
    - Probe ahead until you find an empty slot
    - For **linear probing** (if k is full, keep looking at k+1 until you find an empty slot), Primary clustering is a problem - cluster of dense points may form, making probing more expensive
    - Another strategy: **Double hashing**
        - E.g. if `h1(k) = k % 7` is the first hash function, for probing, `h(k,i) = (h1(k) + i*h2(k)) % 7` where i is the ith probe ahead   
    - Worst case insertion is bad

- Which is better? Depends on the use case
    - For big data, go for separate chains
    - For structure speed, double hashing

## Load factor
- Denotes how much data is stored vs how much space is available in the table. $\alpha$ = n/N
- if load factor = 1.0, exactly as many elements as there is space in the table
- The runtime of hash insertion depends on the load factor "$\alpha$", as it increases, the performance degrades 
- If we manage "$\alpha$", the run times are usually fast (mostly if "$\alpha$" less than 0.6)
- Resizing the array (always want to double)
    - Need to do rehashing - since we still want it to be uniformly distributed

### C++ implementation
- std::map is a dictionary often implemented as a "red-black tree." A red-black tree is another kind of balanced tree that has similar performance to an AVL tree.
    - Trees are good for range finding (upper bound, lower bound) and nearest neighbors e.g. O(logn)
- std::unordered_map is an implementation of hash table
    - Hash tables are the fastest for lookups (but very slow for nearest neighbors etc.)
    - ::operator[], ::insert, ::erase, ::load_factor(), ::max_load_factor(ml) -> sets the max load factor
    
