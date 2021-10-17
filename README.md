
# inch
An easy-to-use user input validation library

## Basic usage
```cpp
// example.cpp

#include "inch.hpp"

int main() {
    std::cout << inch::get("Name") << std::endl;
    
    return 0;
}
```

Compile...

```bash
g++ ./example.cpp -std=c++17
```

Run, entering `John Doe` as our response

```bash
Name: John Doe
John Doe
```

## Validating input
`inch` provides a few functions for constructing predicates called `Check`s, which can be used for verifying inputs.
These `Check`s are passed into the input functions to be used as validation checks.

Here is an example which verifies that a user's input is a numeric value
```cpp
inch::get("Favourite number", inch::checks::numeric())
```

For reference, here is a list of all of the `Check`s that `inch` currently provides:
### Checks
- `is(values...)` - Specific value
- `regex(exp)` - Matches RegEx
- `length(len)` - Specific length
- `consists_of(str_of_chars)` - Consists of characters
- `numeric()` - Is numeric
- `range(min, max)` - Within a numeric range