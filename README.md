
# inch
An easy-to-use user input validation library

## Example
Here is an example which showcases some of the features that `inch` provides

```cpp
// example.cpp

#include "inch.hpp"

int main() {
    // Ask a question
    inch::ask("What is your name");
    
    // Retrieve a number within a specific range
    inch::get(
        "Guess a number from 1 to 10",
        inch::checks::range(1, 10)
    );

    // Retrieve a password while masking the input
    inch::get<inch::Style::Masked>("Enter your password");

    // Present a choice
    inch::input<inch::Style::Instant>(
        "Download update? [Y / N] ",
        inch::checks::is("Y", "N")
    );

    return 0;
}
```

Compile...

```bash
g++ ./example.cpp -std=c++17
```

Run...

```
What is your name?
John Doe
Guess a number from 1 to 10: 50
Invalid input
Guess a number from 1 to 10: 2
Enter your password: ********
Download update? [Y / N] T
Invalid input
Download update? [Y / N] N
```

## 
## Input functions
`inch` has three basic functions for retrieving input, each of which differ slightly in the way the user gets prompted.

These three functions are as follows:

### `get(prompt, checks...)`
```
Prompt: <Response>
```
### `ask(prompt, checks...)`
```
Prompt?
<Response>
```
### `input(checks...)`
```
<Response>
```

## Checks
`inch` provides functions for constructing predicates called `Check`s, which can be passed into input functions to be used for validating inputs.

For reference, here is a list of all the `Check`s that `inch` currently provides:

### Checks
- `consists_of(str_of_chars)` - Consists of characters
- `is<case_sensitive>(values...)` - Specific value
- `length(len)` - Specific length
- `numeric<numeric_type>()` - Is numeric
- `range<numeric_type>(min, max)` - Within a numeric range
- `regex(exp)` - Matches RegEx

## Styles
`inch` allows each input function to be passed a `Style` as one of its template agruments, which determines how the user's input gets interpreted and printed

For reference, here is a list of all the `Style`s that `inch` currently provides:
- `Basic` - Regular user input
- `Instant` - Allows the user to input a single character
- `InstantSilent` - Same as `Instant`, but does not print the input
- `Masked` - Replaces the user's input with asterisks (*)