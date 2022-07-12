# Monty

<img src="https://camo.githubusercontent.com/b32fc84889b63b30d73d84553419e4190d552be0e75b28f106478bb3c1859798/68747470733a2f2f7777772e6765656b73756c74642e636f6d2f77702d636f6e74656e742f75706c6f6164732f323032302f30352f4d6f6e74792d537461636b732d5175657565732e6a7067" alt="Monty Logo">

### What is Monty?
Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.

#### Monty byte code files
Files containing Monty byte codes usually have the `.m` extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:

```
phantom@ubuntu:~/monty$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$
phantom@ubuntu:~/monty$
```

### Compilation & Output
The files are compiled this way:

```
$ gcc -Wall -Werror -Wextra -pedantic *.c -o monty
```

### How to use

1. Compile files.
2. Execute the interpreter:

    ```
    $ ./monty monty_byte_code_file_name.m
    ```

### Example of usage
```
phantom@ubuntu:~/monty$ cat bytecodes/12.m
push 1
push 2
push 3
pall
add
pall
phantom@ubuntu:~/monty$ ./monty bytecodes/12.m
3
2
1
5
1
```

-----------------

## Opcodes

### Push
The opcode `push` pushes an element to the stack.

* Usage: `push <int>`
    * where `<int>` is an integer

### Pall
The opcode `pall` prints all the values on the stack, starting from the top of the stack.

* Usage: `pall`

### Pint
The opcode `pint` prints the value at the top of the stack, followed by a new line.

* Usage: `pint`
* If the stack is empty, will print the following error message: `L<line_number>: can't pint, stack empty`

### Pop
The opcode `pop` removes the top element of the stack.

* Usage: `pop`
* If the stack is empty, will print the following error message: `L<line_number>: can't pop an empty stack`

### Swap
The opcode `swap` swaps the top two elements of the stack.

* Usage: `swap`
* If the stack contains less than two elements, will print the following error message `L<line_number>: can't swap, stack too short`

### Add
The opcode `add` adds the top two elements of the stack.

* Usage: `pop`
* If the stack contains less than two elements, will print the error message `L<line_number>: can't add, stack too short`

### Nop
The opcode `nop` doesn’t do anything.

* Usage: `nop`

-------------------

# Author ✒️
### Tony Kipchirchir
### Anthony Maiyo
Full stack software developer and AR / VR Student at [Alx africa school](https://www.alxafrica.com/).
