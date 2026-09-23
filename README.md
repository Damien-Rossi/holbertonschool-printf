

# _printf


**Group Project — Holberton School / ALX**  
Repository: `holbertonschool-printf`

## Presentation
`_printf` produces formatted output to the standard output (`stdout`) and returns the number of characters printed (excluding the terminating null character).  
This project allows you to master:
- variadic functions (`va_start`, `va_end`, `va_arg`, `va_copy`)
- manual parsing of a format string
- number conversion in different bases
- low-level output using `write`

---

## Supported Specifiers
| Specifier | Description |
|---:|---|
| `%c` | Character |
| `%s` | String |
| `%%` | Literal percent |
| `%d` / `%i` | Signed integer (base 10) |
| `%u` | Unsigned integer (base 10) |
| `%!` | Literal percent followed by an exclamation mark |
| `%K` | Literal percent followed by the letter K |

> According to the project requirements: **no** handling of flags, width, precision, or length modifiers.

---

## Prototype
```c
int _printf(const char *format, ...);
````

---

## Technical Constraints

* Allowed editors: `vi`, `vim`, `emacs`
* Compilation (Ubuntu 20.04):

```bash
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 -Wno-format *.c
```

* Strict Betty style (`betty-style.pl`, `betty-doc.pl`)
* No global variables
* Maximum of 5 functions per file
* All prototypes in `main.h` (with include guard)
* Allowed functions:
  `write`, `malloc`, `free`, `va_start`, `va_end`, `va_copy`, `va_arg`

---

## Suggested Project Structure

```
.
├── main.h           # prototypes and includes
├── _printf.c        # main function
├── function.c       # %c, %s, %d, %i, %u
├── utils.c          # helpers and conversions
├── _putchar         # putchar function
├── get_func         # structure
├── struct.h         # structure types
└── tests/
    └── printf_test.c
```

---

## Usage Example

```c
#include "main.h"

int main(void)
{
    int len = _printf("String : %s\n", "Hello world");
    _printf("Character : [%c]\n", 'H');
    _printf("Negative integer : %d\n", -762534);
    _printf("Unsigned : %u | Octal : %o | Hex : %x | HEX : %X\n",
            4294967295u, 255, 255, 255);
    _printf("Pointer : %p\n", (void*)&main);
    _printf("Percentage : %%\n");
    _printf("Total length : %d\n", len);
    _printf("%!\n");
    _printf("%K\n");
    return (0);
}
```

Compilation:

```bash
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 -Wno-format *.c -o printf_test
./printf_test
```

> `-Wno-format` is tolerated only for tests (prevents warnings when comparing with the real `printf`).

---

## Recommended Tests and Edge Cases

* `%s` with `NULL` → display `(null)`
* Handling of `INT_MIN`, `INT_MAX`
* Unsigned values greater than `INT_MAX`
* `%%`, `%!`, and `%K` → do not consume any argument
* Correct return of the number of printed characters
* Memory verification with `valgrind` if `malloc` is used

---

## Compliance Checklist

* [ ] No warnings (except `-Wno-format` for tests)
* [ ] No memory leaks
* [ ] No global variables
* [ ] Betty style OK
* [ ] Maximum 5 functions per file
* [ ] All prototypes in `main.h`
* [ ] All specifiers implemented
* [ ] Tests validated on edge cases

---

## Implementation Notes

Use a mapping structure such as:

```c
typedef struct spec {
    char specifier;
    int (*f)(va_list);
} spec;
```

Start with the simplest ones (`%c`, `%s`, `%%`, `%!`, `%K`), then implement integers.

---

## Authors

* AMBLARD Alison — `@Ali731-Amb`
* ROSSI Damien — `@DaRKkem`

---

## License

Internal project — Holberton School / ALX
Educational use only.

> Made with passion ☕🚀

```
```
