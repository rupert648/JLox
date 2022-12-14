# Lox Grammar Without Precedence
expression     → literal
| unary
| binary
| grouping ;

literal        → NUMBER | STRING | "true" | "false" | "nil" ;

grouping       → "(" expression ")" ;

unary          → ( "-" | "!" ) expression ;

binary         → expression operator expression ;

operator       → "==" | "!=" | "<" | "<=" | ">" | ">=" | "+"  | "-"  | "*" | "/" ;

# Precedence of Grammar
<table>
<thead>
<tr>
  <td>Name</td>
  <td>Operators</td>
  <td>Associates</td>
</tr>
</thead>
<tbody>
<tr>
  <td>Equality</td>
  <td><code>==</code> <code>!=</code></td>
  <td>Left</td>
</tr>
<tr>
  <td>Comparison</td>
  <td><code>&gt;</code> <code>&gt;=</code>
      <code>&lt;</code> <code>&lt;=</code></td>
  <td>Left</td>
</tr>
<tr>
  <td>Term</td>
  <td><code>-</code> <code>+</code></td>
  <td>Left</td>
</tr>
<tr>
  <td>Factor</td>
  <td><code>/</code> <code>*</code></td>
  <td>Left</td>
</tr>
<tr>
  <td>Unary</td>
  <td><code>!</code> <code>-</code></td>
  <td>Right</td>
</tr>
</tbody>
</table>

# Refined Lox Grammar With Precedence
program        → declaration* EOF ;

declaration    → funDecl | classDecl | varDecl | statement ;

classDecl      → "class" IDENTIFIER "{" function* "}" ;

funDecl        → "fun" function ;

function       → IDENTIFIER "(" parameters? ")" block ;

varDecl        → "var" IDENTIFIER ( "=" expression )? ";" ;

statement      → exprStmt | printStmt | block |  ifStmt | whileStmt | forStmt | returnStmt;

forStmt        → "for" "(" ( varDecl | exprStmt | ";" )
                expression? ";"
                expression? ")" statement ;

returnStmt     → "return" expression? ";" ;

parameters     → IDENTIFIER ( "," IDENTIFIER )* ;

whileStmt      → "while" "(" expression ")" statement ;

ifStmt         → "if" "(" expression ")" statement ( "else" statement )? ;

block          -> "{" declaration* "}";

exprStmt       → expression ";" ;

printStmt      → "print" expression ";" ;

arguments      → expression ( "," expression )* ;



expression     → assignment ;

assignment     → ( call "." )? IDENTIFIER "=" assignment | logic_or ;

ternary        → logic_or ( "?" ternary ":" ternary)*; 

logic_or       → logic_and ( "or" logic_and )* ;

logic_and      → equality ( "and" equality )* ;

equality       → comparison ( ( "!=" | "==" ) comparison )* ;

comparison     → term ( ( ">" | ">=" | "<" | "<=" ) term )* ;

term           → factor ( ( "-" | "+" ) factor )* ;

factor         → unary ( ( "/" | "*" ) unary )* ;

unary          → ( "!" | "-" ) unary | primary ;30k

call           → primary ( "(" arguments? ")" | "." IDENTIFIER )* ;

primary        → NUMBER | STRING | "true" | "false" | "nil" | "(" expression ")" | IDENTIFIER ;