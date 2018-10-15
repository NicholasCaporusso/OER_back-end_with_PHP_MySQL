# Data types, variables, and constants

## Data types
Programming languages realize operations with data, such as, numbers, text, and other types of values that can be used to write information in a web page. For instance, data can be utilized to customize the title of a page, to display a table with values, and to process information sent using a web form. 

PHP supports working with different types of data:
- Basic (primitive) data types, which include:
  - *boolean*, such as true or false;
  - *integer*, for numbers;
  - *float*: decimal values;
  - *string*, that comprises different types of text;
- Complex (non-primitive) data types, that is:
  - *array*, that is, collections of elements
  - *object*: sophisticated, custom data types;
  - *resource*, such as, references to databases;
  - *NULL*, which represents a non-existing value.

This section will focus on the four primitive data types.

## Variables
In programming languages, variables are blocks of memory that that can be utilized as  containers for storing and retrieving pieces of data, such as, the title of a webpage, the email of a user, or the URL of a link. They are convenient because we can use them to temporary store information for later processing and use. Also, the name "variable" describes their behavior, because the content of a variable can change during the execution of a script.

Variables are typically identified by an arbitrary name (e.g., username, or password), so that programmers can use descriptive words instead of referring to the complex identifier that represents the corresponding memory location. For instance, `title` can represent the title of a page, or `email` can contain the e-mail address of a user. 

#### Naming conventions
In PHP, variable names are preceded by the symbol `$` (dollar). Variable names cannot contain any space, and can only consist of letters, numbers, and underscore. Moreover, they must begin with a letter or with the underscore symbol.

Also, by convention, variable names should be: 
- meaningful, to better represent the type of information that they contain; for instance, `$username` is a good example, compared to `$un`, which is harder to understand;
- written in lowercase (e.g., `$variable`) or in camel case (e.g., `$firstName` and `$lastName`).

#### Assigning a value to a variable
Variables are containers for data, and they can assume values belonging to any basic or complex data types, such as, numbers (e.g., `13` or `3.14`), strings (e.g., `'Los Angeles'`), booleans (e.g., `true`), the NULL type, and others. Also, they can contain the result of an expression (discussed later).

Variables can be created and used as needed in the script. Values can be assigned to variables by using the `=` symbol (assignment operator) as described in the following example. 

*Example: declaring and displaying a variable*
```php
<?php
$boolean=true;
echo $boolean; // 1
echo '<br />';

$integer=121;
echo $integer; // 121
echo '<br />';

$float=3.14;
echo $float; // 3.14
echo '<br />';

$text='Hello world';
echo $text; // Hello world
?>
```

#### Dynamic type conversion
PHP is very flexible in regards to variables: there is virtually no limit to the number of variables that can be utilized in a program. 

Moreover, PHP is a dynamically-typed language: as a result, the same variable can be assigned with values belonging to different data types, and it will automatically change its data type according to the value it will receive, as shown below.

*Example: declaring and displaying a variable*
```php
<?php
$variable=true;
echo $variable; // 1
echo '<br />';

$variable=121;
echo $variable; // 121
echo '<br />';

$variable=3.14;
echo $variable; // 3.14
echo '<br />';

$variable='Hello world';
echo $variable; // Hello world
?>
```

#### Displaying a variable content
As discussed earlier, the keyword `echo` can be utilized to write text in an HTML page. Alternatively, the short tags `<?=` and `?>` can be used (e.g., `<?= 'text' ?>`).

The same constructs can be utilized to output the content of variables, as demonstrated in the following example.

```php
<?php
$text='Hello world';
$number=14;
echo $text; // Hello world'
?>
<br />
<?= $number /* 14 */ ?>
```

In addition, the function `var_dump` can be utilized to display the type of a variable and its value. This is mainly utilized for debugging purposes and it should not be utilized as an alternative to `echo`.

```php
<?php
$text='Hello world';
var_dump($text);
?>
```

### Boolean variables
Boolean data types can have only two values: *true* or *false*. They typically represent values within logical expressions.

Boolean values are directly written in PHP as `true` or `false` (lowercase or uppercase).

*Example: using a boolean variable*
```php
<?php
$value=true;
echo $value; // 1
echp '<br />';

$value=false;
echo $value; // nothing will be displayed
?>
```
The boolean values `true` and `false` have an equivalent in other data types. Specifically, `false` is represented also by:
- the integer 0 (zero) or by the float 0.0 (zero);
- an empty string or the string "0";
- an array with zero elements;
- the type NULL, which includes unset or unassigned variables. 

All other values are considered as equivalent to `true`.

### Integer variables
Integer data is consists of positive and negative natural numbers, such as, -2, -1, 0, 1, and 2. The minimum and maximum values depends on the architecture of the platform and on the amount of bits reserved for storing integer values (i.e., 32 or 64 bit). The minimum and maximum values are represented by the constant `PHP_INT_MAX`.

*Example: using an integer variable*
```php
<?php
$value=5;
echo $value;
echo '<br />';

$value=PHP_INT_MAX;
echo $value;
?>
```

### Float variables
Floating point data types can be utilized to represent positive and negative decimal numbers (e.g., 3.14). Please note that the character `.` (dot) is utilized as a decimal separator. 
As for the integer type, the minimum and maximum values depend on the architecture. Typically, float variables support up to about 14 digits after the decimal point.

*Example: using a float variable*
```php
<?php
$value=5.55;
echo $value;
echo '<br />';

$value=-14.31231;
echo $value;
?>
```

### String variables
The string data type can be utilized to write text, that is, a set of characters, such as, `Hello world`. This data type can be utilized to represent e-mails, URLs, and other types of text.

In PHP, strings are collections of characters (i.e., arrays). It is not necessary to specify the number of characters that the variable will contain: PHP will automatically allocate sufficient space depending on th econtent of the string.

A string must be enclosed by two delimiters: to this end, the character `'` (single quote) or the character `"` (double quote) can be utilied. The delimiter used at the beginning of a string must be used to indicate its end.

```php
<?php
$text='Hello world with single quote';
echo $text;
echo '<br />';

$text="Hello world with double quotes";
echo $text;
?>
```

Strings are extremely important in PHP, as they can contain simple text, values submitted via a web form (e.g., username and password), HTML code, Regular expressions and MySQL statements (discussed later).

```php
<?php
$title='<h1>This is the title of the page</h1>';
$content="<p>This is the content of the page</p>";
?>
<html>
<head></head>
<body>
<?php
echo $title; // <h1>This is the title of the page</h1>
echo $content; // <p>This is the content of the page</p>
?>
</body>
</html>
```

#### Escaping special characters
As single quote or double quotes are utilized as separators.

Let's consider the following string. As the single quote character is utilized as a separator, PHP will consider as a string the words `dos and don`, and it will generate an error because it will try to interpret the remaining characters (i.e., `ts of programming`) as part of the PHP language.
```php
$text='Dos and don'ts of programming';
```
Similarly, the following syntax will generate an error, because PHP will consider `Welcome to ` as a string, and it will get "confused" with the rest of the statement.
```php
$text="Welcome to "Los Angeles", the largest city in California;
```

There are three ways to overcome the problem:
1. using double quotes as delimiters for strings that contain single quotes (e.g., Dos and don'ts);
2. using single quotes as delimiters for strings that contain dobule quotes (e.g., Welcome to "Los Angeles");
3. using a backslash character to "escape" a delimiter (tell PHP that this is not to be considered as a delimiter): the sequence `\'` can be utilized to display a single quote, the sequence `\"` can be utilized to display a double quote, and the sequence the sequence `\\` can be utilized to display a backslash, as explained in the following example

```php
<?php
$text="Dos and don'ts"; // Method 1
echo $text;
echo '<br />';

$text='Welcome to "Los Angeles", the largest city in California'; // Method 2
echo $text;
echo '<br />';

$text='Dos and don\'ts of programming'; // Method 3: escaping a single quote
echo $text;
echo '<br />';

$text="Welcome to \"Los Angeles\", the largest city in California"; // Method 3: escaping a double quote
echo $text;
echo '<br />';

$text="Click on the submenu File\\Save as"; // Method 3: escaping a backslash
echo $text;
?>
```

#### Difference between single and double quotes
As shown in the previous examples, single and double quotes can be utilized almost interchangeably as delimiters. However, PHP will consider strings enclosed in single quotes as containing only text, and it will not evaluate their content. 

Instead, PHP will try to evaluate the content of strings enclosed in double quotes: if strings enclosed in double quotes contain variable names, PHP will replace the variable name with its content variable. The following example shows how the string A variable name can be $text is interpreted differently depending on whether it is enclosed in single or double quotes. 

```php
<?php
$text='Hello world';
$myString='A variable name can be $text'; // with single quotes
echo $myString; // A variable name can be $text
echo '<br />';

$myString="A variable name can be $text"; // with double quotes
echo $myString; // A variable name can be Hello world
?>
```

#### Concatenating and displaying multiple variables
In PHP, the concatenation operator (discussed later, also) can be utilized to unify two or more values (or variables) together. This is covenient for showing messages that consist of text defined statically (i.e., as values) and dynamically (i.e., within variables), as described in the following example:
```php
<?php
$beginning='My name is ';
$name='Nicholas';
$dateOfBirth=1981;

echo $beginning.$name.' and I was born in '.$dateOfBirth; // My name is Nicholas and I was born in 1981
?>
```
This is equivalent to the following, which uses double quotes as delimiters.
```php
<?php
$name='Nicholas';
$yearOfBirth=1981;
$string="My name is $name and I was born in $yearOfBirth";
echo $string; // My name is Nicholas and I was born in 1981
?>
```

## Constants
As shown in the previous examples, the content of a variable can change during the program. Instead, in programming languages, *constants* are containers for data that are not expected to change during the execution of the program. Constants are typically defined at the beginning of a script, and their value will be the same throughout the script. Constants are useful for specifying the application settings (e.g., the name of our web application). Differently than variables, which are preceded by the symbol `$` (dollar), constants are not preceded by anything.

In PHP, constants are defined using the `define` construct (shown below). The first element of the define statement is the name of the constant as a string (within single or double quotes), the latter specifies its value, which can be defined using any of the primitive data types.

By convention, constant names are typically written in uppercase (with words separated by an underscore), to distinguish them from variables. Consants are visible in the program in which they are defined, that is, their *scope* is *global* (discussed later).

```php
<?php
define('SHOW_TITLE',true);
echo SHOW_TITLE; // 1
echo '<br />';

define('POSTS_PER_PAGE',10);
echo POSTS_PER_PAGE; // 10
echo '<br />';

define('PI',3.14);
echo PI; // 3.14
echo '<br />';

define('CONSTANT_NAME','My constant');
echo CONSTANT_NAME; // My constant
?>
```

#### Verifying if a constant has been defined
The function `defined` can be utilized to check if a specific constant has been defined. The name of the constant to be evaluated must be specified in parenthesis, as a string. The function returns the boolean value `true` if the constant is defined, and `false` otherwise.

```php
<?php
define('NEW_CONSTANT','My constant');
echo defined('NEW_CONSTANT'); // will print 1 (true), because the constant is not defined

echo '<br />';
echo defined('CONSTANT_NAME'); // will not print anything (false), because the constant is not defined
?>
```

#### Listing all the defined constants
The function `get_defined_constants()` can be utilized to retrieve all the constants defined in the current script.
```php
<?php
define('NEW_CONSTANT_1','My constant 1');
define('NEW_CONSTANT_2','My constant 2');
var_dump(get_defined_constants());
?>
```