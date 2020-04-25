

## Python: Simple Interpreter Build (Calculator)

### Introduction
Many programming languages exists. Compliers and Interpreters form the foundation of program language interoperability.

#### What do compliers and interpreters do?
While similar, an important distinction exists between compilers and interpreters. Compilers translate a software program's code into a machine language physical devices understand. While interpretors simply processing the software program's code directly to a physical device.

#### Project Breakdown
1. Build a simple Pascal language interpreter utilizing Python 3 as the implementation language
2. Build a source-level debugger

### Building the Interpreter
(Note: The following code creates a simple calculator interpreter.)

Save the following in a GitHub repository file as:

```
calc1.py
```

The .py file type indicates a Python file.

```
# Token types
#
# EOF (end-of-file) token is used to indicate that
# there is no more input left for lexical analysis
INTEGER, PLUS, EOF = 'INTEGER', 'PLUS', 'EOF'


class Token(object):
    def __init__(self, type, value):
        # token type: INTEGER, PLUS, or EOF
        self.type = type
        # token value: 0, 1, 2. 3, 4, 5, 6, 7, 8, 9, '+', or None
        self.value = value

    def __str__(self):
        """String representation of the class instance.

        Examples:
            Token(INTEGER, 3)
            Token(PLUS '+')
        """
        return 'Token({type}, {value})'.format(
            type=self.type,
            value=repr(self.value)
        )

    def __repr__(self):
        return self.__str__()


class Interpreter(object):
    def __init__(self, text):
        # client string input, e.g. "3+5"
        self.text = text
        # self.pos is an index into self.text
        self.pos = 0
        # current token instance
        self.current_token = None

    def error(self):
        raise Exception('Error parsing input')

    def get_next_token(self):
        """Lexical analyzer (also known as scanner or tokenizer)

        This method is responsible for breaking a sentence
        apart into tokens. One token at a time.
        """
        text = self.text

        # is self.pos index past the end of the self.text ?
        # if so, then return EOF token because there is no more
        # input left to convert into tokens
        if self.pos > len(text) - 1:
            return Token(EOF, None)

        # get a character at the position self.pos and decide
        # what token to create based on the single character
        current_char = text[self.pos]

        # if the character is a digit then convert it to
        # integer, create an INTEGER token, increment self.pos
        # index to point to the next character after the digit,
        # and return the INTEGER token
        if current_char.isdigit():
            token = Token(INTEGER, int(current_char))
            self.pos += 1
            return token

        if current_char == '+':
            token = Token(PLUS, current_char)
            self.pos += 1
            return token

        self.error()

    def eat(self, token_type):
        # compare the current token type with the passed token
        # type and if they match then "eat" the current token
        # and assign the next token to the self.current_token,
        # otherwise raise an exception.
        if self.current_token.type == token_type:
            self.current_token = self.get_next_token()
        else:
            self.error()

    def expr(self):
        """expr -> INTEGER PLUS INTEGER"""
        # set current token to the first token taken from the input
        self.current_token = self.get_next_token()

        # we expect the current token to be a single-digit integer
        left = self.current_token
        self.eat(INTEGER)

        # we expect the current token to be a '+' token
        op = self.current_token
        self.eat(PLUS)

        # we expect the current token to be a single-digit integer
        right = self.current_token
        self.eat(INTEGER)
        # after the above call the self.current_token is set to
        # EOF token

        # at this point INTEGER PLUS INTEGER sequence of tokens
        # has been successfully found and the method can just
        # return the result of adding two integers, thus
        # effectively interpreting client input
        result = left.value + right.value
        return result


def main():
    while True:
        try:
            # To run under Python3 replace 'raw_input' call
            # with 'input'
            text = raw_input('calc> ')
        except EOFError:
            break
        if not text:
            continue
        interpreter = Interpreter(text)
        result = interpreter.expr()
        print(result)


if __name__ == '__main__':
    main()
```

(Note: The above code includes limitations that help keep the program simple. The program only recognized single digit integrers, addition, and does not recognize whitespace between characters in the calculation. Violating any of the limitations results in an exception.)

Now run the calc1.py file from your computer's system command line as follows:

```
$ python calc1.py
```

Test the calculator with enteries such as that follow on the command line:

```
calc> 1+1
```
Hit the "return" key and the number "2" should return. Feel free to try out more calculations using the calc> command. Example:

```
calc> 5+4
```

Hit the "return" key and the number "9" should return.

#### How the Calcuator Works
When you enter an expression 1+1 on the command line your interpreter gets a string “1+1”. In order for the interpreter to understand what to do with the string it first needs to break the input “1+1” into components called tokens.

A __token__ is an object that has a type and a value. For example, for the string “1” the type of the token is an INTEGER and the corresponding value is integer 1.

The process of breaking the input string into tokens is called __lexical analysis__. First the interpreter needs to read the input of characters and convert the input into a stream of tokens. The lexical analyzer (aka: lexer, scanner, tokenizer) completes the intiger to token conversation.

The method get_next_token of the Interpreter class is the lexical analyzer. Every time you call it, you get the next token created from the input of characters passed to the interpreter.

#### The Calculator's Lexical Analysis Code (Reference)
```
>>> from calc1 import Interpreter
>>>
>>> interpreter = Interpreter('3+5')
>>> interpreter.get_next_token()
Token(INTEGER, 3)
>>>
>>> interpreter.get_next_token()
Token(PLUS, '+')
>>>
>>> interpreter.get_next_token()
Token(INTEGER, 5)
>>>
>>> interpreter.get_next_token()
Token(EOF, None)
>>>
```

Now that the interpreter accesses token streams generated from integer inputs, the interpreter needs recognize the structure in the flat stream of tokens it gets from the lexer get_next_token. The interpreter expects to find the following structure integer+integer (The interpreter attempts to find a sequence of tokens integer followed by a plus sign followed by an integer.)

The method responsible for finding and interpreting that structure is __expr__. The expr method verifies the token sequence corresponds to the expected sequence of tokens (i.e., integer+integer). After confirming the structure, the interpreter generates the result by adding the value of the token on the left side of the PLUS and the right side of the PLUS, thus successfully interpreting the arithmetic expression passed to the interpreter.

The expr method itself uses the helper method eat to verify that the token type passed to the eat method matches the current token type. After matching the passed token type the eat method gets the next token and assigns it to the current_token variable, thus effectively “eating” the currently matched token and advancing the imaginary pointer in the stream of tokens. If the structure in the stream of tokens doesn’t correspond to the expected INTEGER PLUS INTEGER sequence of tokens the eat method throws an exception.

#### Interpreter Functions

1. The interpreter accepts an input string (e.g., 1+1)
2. The interpreter calls the expr method to find a structure (i.e., integer+integer) in the stream of tokens returned by the lexical analyzer get_next_token. After confirming the structure, the intepreter interprets the input by adding the values of two integer tokens.
