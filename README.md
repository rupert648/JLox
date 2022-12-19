# JLox
Java Interpreter for the lox programming language.
### The Lox Programming Language
For more information on the Lox programming language, please refer to the [Crafting Interpreters Book](https://craftinginterpreters.com)
### This Project
This project is a Java based implementation for an interpreter of the Lox programming language.
Much of this work is derived from reading and workign through the [Crafting Interpreters Book](https://craftinginterpreters.com) by Robert Nystrom.

### Running the Project
The binaries for this project are already built in the `target` folder, therefore the program can be ran using the following command.
```
java -classpath ./target/classes com.craftinginterpreters.lox.Lox
```
To run the program with an input file, simply specify the input file as a command line argument.
```
java -classpath ./target/classes com.craftinginterpreters.lox.Lox test.lox
```

