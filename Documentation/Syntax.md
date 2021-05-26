# API - Syntax Reference

Below are [ANTLR](http://en.wikipedia.org/wiki/ANTLR) grammars used by the Compliance360 API calls.

## Selection

A comma separated list of field tokens used to select specific fields in retrieve operations.

### Syntax
```
selection
    : ( fieldToken ( COMMA fieldToken )* )? EOF
    ;

fieldToken         : NAME ;

NAME               : (NAMECHAR)+ ;
COMMA              : ',' ;
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;
```
### Sample
```
FirstName,LastName,HireDate
```
## Filter

A series of field tokens and values separated by operators grouped together into sequences of AND and OR terms.

### Syntax
```
filter
    : complexFilter? EOF
    ;

complexFilter
    : ( filterGroup | simpleFilter )
      (
          ( andOperator | orOperator )
          ( filterGroup | simpleFilter )
      )*
    ;

filterGroup
    : OPENPAREN complexFilter CLOSEPAREN
    ;

simpleFilter
    : (
        fieldToken
        (
            binaryOperator filterValue
        )?
      )
    | unaryOperator fieldToken
    ;

binaryOperator
    : EQ | NOTEQ | LESS | LESSEQ | GREATER | GREATEREQ | LIKE | NOTLIKE | STARTSWITH | ENDSWITH
    ;

unaryOperator
    : PLUS | MINUS
    ;

andOperator
    : AMP | SEMI
    ;

orOperator
    : PIPE
    ;

filterValue        : singleQuoteString | doubleQuoteString ;

singleQuoteString  : '\'' ~('\'')* '\'' ;

doubleQuoteString  : '"' ~('"')* '"' ;

fieldToken         : NAME ;

NAME               : (NAMECHAR)+ ;
OPENPAREN          : '(' ;
CLOSEPAREN         : ')' ;
PLUS               : '+' ;
MINUS              : '-' ;
AMP                : '&' ;
SEMI               : ';' ;
PIPE               : '|' ;
EQ                 : '=' ;
NOTEQ              : '!=' ;
LESS               : '<' ;
LESSEQ             : '<=' ;
GREATER            : '>' ;
GREATEREQ          : '>=' ;
LIKE               : '~' ;
NOTLIKE            : '!~' ;
STARTSWITH         : '=~' ;
ENDSWITH           : '~=' ;
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;
```
### Sample
```
(FirstName=~'J';LastName="O'Malley")|(HireDate>'2010-01-01T00:00:00')
```
## Order

A comma separated list of field tokens used to specify ordering in retrieve operations.

### Syntax
```
order
    : ( orderTerm ( COMMA orderTerm )* )? EOF
    ;

orderTerm
    : ascendingTerm | descendingTerm
    ;

ascendingTerm
    : PLUS? fieldToken
    ;

descendingTerm
    : MINUS fieldToken
    ;

fieldToken         : NAME ;

NAME               : (NAMECHAR)+ ;
COMMA              : ',' ;
PLUS               : '+' ;
MINUS              : '-' ;
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;
```
### Sample
```
FirstName,-LastName,+HireDate
```
## Identifier

A token used to represent a unique object in the system.

### Syntax
```
identifier
    : moduleToken SLASH componentToken SLASH typeToken COLON id EOF
    ;

moduleToken         : NAME ;
componentToken      : NAME ;
typeToken           : NAME ;
id                  : INT ;

NAME               : (NAMECHAR)+ ;
INT                : (INTCHAR)+ ;
COMMA              : ',' ;
COLON              : ':' ;
SLASH              : '/' ;
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;
fragment INTCHAR   : '0'..'9' ;
```
### Sample
```
EmployeeManagement/Employee/Default:20
```
