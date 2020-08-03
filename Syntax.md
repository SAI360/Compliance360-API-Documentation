# REST API - Syntax Reference

Below are [ANTLR](http://en.wikipedia.org/wiki/ANTLR) grammars used by the Compliance360 REST API calls.

## Selection

A comma separated list of field tokens used to select specific fields in retrieve operations.

### Syntax

selection<br>
: ( fieldToken ( COMMA fieldToken )* )? EOF<br>
;<br>
<br>
fieldToken         : NAME ;<br>
<br>
NAME               : (NAMECHAR)+ ;<br>
COMMA              : ',' ;<br>
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;<br>

### Sample

FirstName,LastName,HireDate

## Filter

A series of field tokens and values separated by operators grouped together into sequences of AND and OR terms.

### Syntax

filter<br>
: complexFilter? EOF<br>
;<br>
<br>
complexFilter<br>
: ( filterGroup | simpleFilter )<br>
(<br>
( andOperator | orOperator )<br>
( filterGroup | simpleFilter )<br>
)*<br>
;<br>
<br>
filterGroup<br>
: OPENPAREN complexFilter CLOSEPAREN<br>
;<br>
<br>
simpleFilter<br>
: (<br>
fieldToken<br>
(<br>
binaryOperator filterValue<br>
)?<br>
)<br>
| unaryOperator fieldToken<br>
;<br>
<br>
binaryOperator<br>
: EQ | NOTEQ | LESS | LESSEQ | GREATER | GREATEREQ | LIKE | NOTLIKE | STARTSWITH | ENDSWITH<br>
;<br>
<br>
unaryOperator<br>
: PLUS | MINUS<br>
;<br>
<br>
andOperator<br>
: AMP | SEMI<br>
;<br>
<br>
orOperator<br>
: PIPE<br>
;<br>
<br>
filterValue        : singleQuoteString | doubleQuoteString ;<br>
<br>
singleQuoteString  : '\'' ~('\'')* '\'' ;<br>
<br>
doubleQuoteString  : '"' ~('"')* '"' ;<br>
<br>
fieldToken         : NAME ;<br>
<br>
NAME               : (NAMECHAR)+ ;<br>
OPENPAREN          : '(' ;<br>
CLOSEPAREN         : ')' ;<br>
PLUS               : '+' ;<br>
MINUS              : '-' ;<br>
AMP                : '&' ;<br>
SEMI               : ';' ;<br>
PIPE               : '|' ;<br>
EQ                 : '=' ;<br>
NOTEQ              : '!=' ;<br>
LESS               : '<' ;<br>
LESSEQ             : '<=' ;<br>
GREATER            : '>' ;<br>
GREATEREQ          : '>=' ;<br>
LIKE               : '~' ;<br>
NOTLIKE            : '!~' ;<br>
STARTSWITH         : '=~' ;<br>
ENDSWITH           : '~=' ;<br>
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;<br>

### Sample

(FirstName=~'J';LastName="O'Malley")|(HireDate>'2010-01-01T00:00:00')

## Order

A comma separated list of field tokens used to specify ordering in retrieve operations.

### Syntax

order<br>
: ( orderTerm ( COMMA orderTerm )* )? EOF<br>
;<br>
<br>
orderTerm<br>
: ascendingTerm | descendingTerm<br>
;<br>
<br>
ascendingTerm<br>
: PLUS? fieldToken<br>
;<br>
<br>
descendingTerm<br>
: MINUS fieldToken<br>
;<br>
<br>
fieldToken         : NAME ;<br>
<br>
NAME               : (NAMECHAR)+ ;<br>
COMMA              : ',' ;<br>
PLUS               : '+' ;<br>
MINUS              : '-' ;<br>
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;<br>

### Sample

FirstName,-LastName,+HireDate

## Identifier

A token used to represent a unique object in the system.

### Syntax

identifier<br>
: moduleToken SLASH componentToken SLASH typeToken COLON id EOF<br>
;<br>
<br>
moduleToken         : NAME ;<br>
componentToken      : NAME ;<br>
typeToken           : NAME ;<br>
id                  : INT ;<br>
<br>
NAME               : (NAMECHAR)+ ;<br>
INT                : (INTCHAR)+ ;<br>
COMMA              : ',' ;<br>
COLON              : ':' ;<br>
SLASH              : '/' ;<br>
fragment NAMECHAR  : 'A'..'Z' | 'a'..'z' ;<br>
fragment INTCHAR   : '0'..'9' ;<br>

### Sample

EmployeeManagement/Employee/Default:20
