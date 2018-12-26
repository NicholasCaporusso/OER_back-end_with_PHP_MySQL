# Functions
In programming languages, a function is a self-contained set of instructions that are designed to accomplish a specific task or objective, for instance, displaying a welcome message, calculating the total balance of a shopping cart, or checking if the username and password entered by the user correspond to an existing account. Although at first functions can seem confusing, we use functions in real life all the time, even if we don't realize it. For instance, when we send an e-mail, we implement a chain involving several steps: (1) click on the button that enables us to compose a new message, (2) specify the e-mail address(es) of the recipient(s), (3) write the subject and the message, (4) add any address in CC or BCC, and (5) click on the button that sends the message. Nevertheless, we refer to them as "sending an email" even if we actually realize a more complex sequence of multiple actions and we might do them a different way depending on the e-mail client or platform. This abstraction helps us simplify both work organization and team communication because we don't have to specify all the details of the task every time we approach it: we can simply tell our colleagues that we are sending an e-mail knowing that they will understand all the steps, assuming that they know how e-mail works.

The advantage of this approach is three-fold:
- after we learn how a task is realized, we can simply recall it and realize it with less effort; in a way, it becomes "automatic";
- we can use the same set of actions regardless of the elements that are involved in the operation: the tasks for sending an e-mail are the same regardless of the recipient, the subject, or the content of the message; 
- we can simplify the way we communicate about the actions by referring to them as "sending an e-mail", instead of going in the details of all the subtasks.

Functions work exactly in the same way in programming: they are a sequence of actions (blocks of code) identified by a name that realizes a specific operation. Typically, modern languages include several internal - or built-in - functions that are already defined and can be directly used. Conveniently, PHP provides developers with a large collection of built-in functions for working with data structures, files, date and time. We already utilized several of them, such as, `phpinfo`, `print_r`, and `var_dump`.

In addition, programming languages enable developers to create their own functions so that they can extend the features already given with additional actions. The main advantage of user-generated functions is that they enable developers to customize the capabilities of a programming language to their needs and, simultaneously, build a reusable repository of tools that can be spent many times across multiple different programs. Moreover, code reuse is one of the main benefits of writing functions: writing programs can result in several thousands of lines of code, many of which do the same thing (e.g., showing a list of elements), being able to leverage existing functions can result in less effort, faster development, and more reusable code. Functions are the cornerstone of the "Dont Repeat Yourself" (DRY) approach, which is crucial for programmers.

However, before a user-defined function can be utilized, it must be declared (or defined), that is, we need to explain how the function works. This is to make the environment aware of the existence of the function and of its operations. To this end, we need to specify:
- its name, so that we will be able to easily identify it and refer to its operations;
- how it works: this is done by writing the sequence of instructions that will be realized by the function;
- the elements that it will process: some operations (e.g., `phpinfo()`, which shows a summary of the environment variables) don't need any external input; others instead will utilize some data, for instance, `print_r($array)` will need the name of the array to be displayed.

In its simplest form, a user-defined function can be declared as shown in the following pseudo-code:

```php
function <name>(<parameters>){
	<instructions>
	return <return_value>;
}
```

Functions are introduced by the keyword "function" and have four main components: a name, a body consisting of statements, an optional set of parameters (or arguments), and an optional return value. 

The function name can be any string that is not already reserved by PHP (that is, any string that it not already used as a name for an in-built function). Function names must be unique in the entire program, otherwise PHP will issue an error when it will parse the source code. Function names in PHP must begin with a letter or underscore `_` and can consist of an arbitrary sequence of uppercase or lowercase letters, numbers, and the underscore symbol. Thus, they follow the same rules as variables, with the only difference that variables are preceded by the dollar sign `$`. They are case-insensitive, which means that sum, SUM, and Sum will refer to the same function, regardless of how it is initially defined. As in the case of variables, there are several  best practices for function names. By convention, PHP built-in functions are all written in lowercase. Conversely,  programmers write the name of user-defined functions using short and meaningful verbs and words that describe the purpose of the function,  in camel case with the first letter always being lower case (e.g., printMessage, verifyCredentials, or checkPassword). As for variable names, good coding practices suggest that function names should be descriptive: the purpose of the name of a function is to quickly identify the purpose of the function, so, it has to be short, easy to understand, and meaningful. Once a  function is defined, it can be utilized anywhere in the program by simply calling its name, as if it was part of the built-in operations that can be realized with the programming language.

The body of the function is enclosed in curly braces, and it consists of a sequence of statements, as in the block of code of a control structure. It can consist of an arbitrary number of lines of code, including variable declarations, statements for showing HTML code, and structures for flow control and loops.

Let's declare our first user-defined function, called `helloWorld`. Its purpose is to simply show a welcome message. As you can see, the body of the function consists of one statement only. The function has no parameters and does not return any value: this is why the parentheses are empty, and there is no return keyword.

```php
<?php
function sayHelloWorld(){
	echo 'Hello world';
}
?>
```

Functions are different than structures for flow control or other statements: their instructions are not executed automatically when the function is declared. You can verify it: launching the script in the previous example will not produce any message. This is because when we declare a function, we are just making the program aware of a new component that can be utilized. PHP will add it to the set of operations that can be launched, as if it was an in-built function. To actually execute it, we need to call it as we do with in-built functions. To this end, we can use the function name as described in the last statement of the following example:
```php
<?php
function sayHelloWorld(){
	echo 'Hello world';
}

sayHelloWorld();
?>
```

So, functions live in two stages: function declaration (i.e., when a function is defined for the first time), and function invocation, that is, when a function is utilized.

The body of a function can call other functions, as described below.
```php
<?php

function sayWelcomeMessage(){
	sayHelloWorld();
	sayTagline();
}

function sayHelloWorld(){
	echo 'Hello world!';
}
function sayTagline(){
	echo 'This is an example of how to use functions within functions';
}

sayWelcomeMessage();
?>
```

Note that the function can be called before it is defined: this is because PHP parses the entire file before running the program, so it will be aware of the definition of the function by the time it is called in the script. [VERIFICARE]

As another example, a function can be utilized to display the header or the footer of a webpage.

Typically, functions have one exit point, only.

A function ends its task when it reaches the end of its block or the keyword return.

The return keyword is used to return a value from the function.
The return value is the value that a function returns when it completes its task.
 

A function may or may not return a value, when it does, it can return a value of any the available data types.

Values returned by functions can be assigned to values or used in a statement.

Therefore, to execute the function of the previous example, we need to type the function name (either before or after the declaration of the function.

helloWorld();

For instance, we can design a function for displaying a sign in form, 

## Return value
A function may return a value so that the calling script can communicate with it.
The return keyword can be utilized to return any variable or value you want, of any data type (e.g., a simple variable, such as, an integer or a string, or a complex data type, such as an object or database connection). The only constraint is that the return value must be one one and one only. As a result of a return statement, the program will immediately exit the block of the function. 

The return keyword can be utilized alone in a statement,You can also just use "return;", which means "exit without sending a value back."


## Scope
One of the most important characteristics of functions is that they are self-contained, that is, they do not depend on other parts of the program (unless they call other user-defined functions or they use objects from classes defined in the program). If well-written, a function will encapsulate all the details of its implementation.
As a result, they can be copied from one program and utilized in another piece of code and they would behave in exactly the same way. 
In many programming languages, including PHP, functions create.

In programming languages, the word scope refers to the area of the program in which variables are visible. In PHP there are two types of scopes: global and local. Any variable  declared outside of a function is within this global scope, that is, they are visible in all the scripts. Instead, functions have their own scope in PHP: variables outside the body of the function are not visible from inside the body of the function, as well as variables defined in the function are not visible outside. Let's consider the following example:

```php
<?php
$username
function sayHello(){
	$fromName=
	echo 'This is '.$fromName
	echo 'Hello '.$username;
}

sayHello();
echo $username;
echo $fromname;
?>
```
The variable $username is defined in the global scope. Thus, it will be visible from the program, but it will not be accessible by the function. Also, fromName is defined in the function, which is local to the function itself, and it is not accessible to the rest of the program.
Consequently, the code will generate two errors, one in the execution of the function, because the username is undefined, and one in the last statement, when it  will try to print fromname.

Moreover, each function creates its own local scope.

This is why functions are said to be 'self-contained': they don't have access to information from the outside program. Also, what is defined in their body stays within them, and it does not propagate in the rest of the program. Although this might seem counter-intuitive, it is actually what makes functions reusable, portable, and very convenient: because they don't share any information with the rest of the program, we can copy them from one project to another without any trouble. Dealing with the apparent limitation given by the difference between global and local scope may seem annoying, but limiting variable visibility to the local scope only is essential to programming complex applications.

If every variable had global scope and it would be available from everywhere else inside your application, functions wouldn't be as portable, as there could be conflict in variable names: in a small application, you would have to check if a variable name was already used it, and rename it to make sure your variables are unique and that you're not changing the wrong variable from the wrong piece of code. In very large applications consisting of thousands of lines of code, tracking variable names would just be impossible, given their number, and the only way to prevent overwriting or conflicts would be to resort to really complicated naming schemes, which, in turn, would make the code really hard to read and maintain.

So how can a function communicate and exchange information with the rest of the program? Seen from the oudside, a function is a so-called 'black box': the outside program cannot see anything inside the function. In addition to preventing variable overwriting, this helps to keep the complexity of the operation of the function within the function itself. Nonetheless, functions can have multiple inputs, called parameters and one output, that is, a result. The only components that are visible to the program are: the name, its input paramters, and its output - or return value.
[TODO: drawing black box input output]

## Parameters (or arguments)
As described in the previous section, functions are isolated from the rest of the code (global scope), to make sure that they do not have any dependancy so that they can be used in many programs. As a result, variables defined outside of a function are not visible in its body (with some exceptions, such as, global variables and superglobals, as discussed later), and variables in the local scope are not accessible from the rest of the source code. Some functions do not need to receive any information with the rest of the program, such as, the function for printing the sign in form. As a result, they will not need any inputs. Nonetheless, other  functions might require some information from the outside. For instance, if we want to design a function to greet the users who sign, we need to know their name.

Function parameters - or arguments - are the only way in which a function can receive input from the external program, that is, the global scope, or from another context, such as, a different function. Parameters - if present - must be defined in the parentheses just after the function name, as shown in the following pseudo-code.
```php
function functionName(<parameter>){
	actions
}
```
Parameters are variable names that will receive values from the outside program, so that the global scope can communicate with the local scope of the function, whenever the function will be called, as shown by the following pseudo-code.  
```
functionName(value);
```
As a result of a function invocation, PHP will evaluate the parameters and will assign the value passed within parenthesis to the variable name specified, that is, PHP will automatically realize the operation parameter=value; before running the code belonging to the function.
For instance, we can implement a function for greeting the users who sign in as described in the previous section as follows:
```php
<?php
function sayHello($username){
	echo 'Hello '.$username;
}

sayHello('Albert Einstein');
?>
```
The function will use one parameter, called $username. When the function will be called, PHP will assign the value passed in the brackets to the variable named $username, so that it can be utilized in the function. Please note that $username has local scope and it will be visible only within the function. Also, it can be assigned with any value, being it directly a string, or a variable in the global scope, as described in the example below, whch will have an identical behavior.
```php
$name='Albert Einstein';
sayHello($name);
```
As a result, they can be utilized in the body of the function. 
Parameters  are an important part of the declaration of the function, beca

Functions can have at most one return value, but they can have 0 or many input parameters. They must be listed within parentheses in the declaration of the function, and they must be separated by a comma as shown in the pseudo-code below.
```php
function functionname(parameter1, parameter 2, .., parameterN){
	actions
}
```
[TODO: example]


### Default parameters


### Parameters by value


### Parameters by reference
By default, all the arguments of a function are passed by value.
[diagram:https://www.mathwarehouse.com/programming/passing-by-value-vs-by-reference-visual-explanation.php]


### Functions with multiple parameters
As discussed, functions can have zero, one, or many parameters, depending on the purpose of the function and on the application. This would work in most of the cases. However, let's assume we want to build a function that creates a movie with an arbitrary number of actors. As we don't know in advance the number of actors, we will not know how many parameters we will need to specify. 

If we exclude the use of global variables, there are four options:
- using an array
- using the function
- using the operator ...
- using the iterable type hint

#### Using an array
Arrays would work in most of the cases, as we can a number of elements. However, if we have one actor only, we will have to pass it via an array to the function.

#### Using func_get_args
Another possibility consists in using the fun
func_get_args returns an array with all arguments of the current function


#### Using the operator ...
If you use PHP 5.6+, you can now do this:
```php
<?php
function sum(...$numbers) {
    $acc = 0;
    foreach ($numbers as $n) {
        $acc += $n;
    }
    return $acc;
}

echo sum(1, 2, 3, 4);
?>
```
#### Using type hinting and iterable
Alternatively, as of PHP 7.1, the language supports the use a type hint called iterable as shown below
```php
<?php
function f(iterable $args) {
    foreach ($args as $arg) {
        // awesome stuff
    }
}
?>
```
Also, it can be used instead of Traversable when you iterate using an interface. As well as it can be used as a generator that yields the parameters.

func args
iterable

### Parameters and type hinting
PHP is a loosely-typed language. However, in the newest versions of PHP (that is, after version 5), the type of parameters can be specified.This technique, called type hinting,  allows a function to force parameters to belong to a specific type, such as, arrays, objects of a particular class or interfaces (discussed later).  This is helpful to share the requirements of the function with other. 
Type hinting cannot be used with scalar values (e.g., strings or integers), or traits (discussed later).

## Accessing variables in the global scope

## Static variables

## Anonymous functions

## Recursive functions
