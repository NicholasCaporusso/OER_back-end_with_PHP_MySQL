# Structures for flow control
Software programs consist of algorithms, that is, lists of operations that are executed in a sequential and deterministic order to accomplish an objective. While some tasks require actions to be realized in the same order as they were originally coded, other tasks might require to execute a set of instructions to be executed only if some conditions are met; also, some other tasks might require to  repeat the same set of operations several times, until a desired outcome is achieved, or a specific condition is met. As a result, when programs are launched, their instructions might be executed in a different sequence than the order specified in the source code.  

Control structures are the elements of programming languages that enable dynamically changing the flow of code execution depending on some conditions, and thus, they result in the capability of an algorithm of giving different responses (output) based on a different set of inputs. The ability to alter the flow of execution of the source code is one of the most basic yet powerful features of programming languages, as this enables developers to create programs that can automatically respond to different inputs or conditions, and take simple decisions or realize repetitive tasks iteratively.  Programming languages typically implement two fundamental control structures:
- *conditional statements*: realizing a different set of actions depending on some condition (if condition then action 1 else action 2)
- *iterative statements or loops*: reiterating a set of actions a number of times until a condition is verified (while condition do action)

The following flowchart diagrams explain the general behavior of conditional statements and loops. In a conditional statement, the program checks a condition and executes one block of code if the condition is verified, and a different block of code (if present) if the condition is not verified. In a loop block, the program will repeat a set of actions until a condition is verified, otherwise it will stop reiterating. In both cases, after the control structure, execution will continue with the next block.

Control structures are very similar across multiple programming languages: although their implementation might differ slightly in syntax, they mostly have the same behavior. As most of the more recent programming languages, PHP supports a number of different control structures.

## Conditional statements

### If
The simplest form of conditional statement is described by a condition and a set of actions that is executed if a condition is verified. In  case the condition is not verified, the block of actions will not be executed. In a way, conditional statement enable developers to write "intelligent" programs that can autonomously and automatically take decisions, though their behavior is programmed. 

In PHP, this is implemented using the syntax described by the following pseudo-code:
```
if(<condition>){
    <statement(s)>
}
```

The condition can be represented by any expression that has a boolean value as a result. Notice that the block of statements belonging to the control structure are enclosed in curly braces, and they can contain an arbitrary number of lines. By doing this, PHP can determine the instructions that will be executed if the condition is verified. 

![Example: if then ese](https://nicholascaporusso.github.io/OER_back-end_with_PHP_MySQL/chapter_4/if.png)]

An example of this control structure is the case of a cafeteria offering blueberry scones only on Monday morning. As a result, the owner will post a sign only if it is monday.  

We can implement it in PHP using the following code
```php
<?php
$day='monday';
if($day=='monday'){
echo 'Try our blueberry scones! They are available on Monday, only';
}
?>
```

If you change the content of the variable $day in the first statement, the block enclosed in the curly braces will not be executed.

### If ...else
Moreover, conditional statements can be utilized to execute two different blocks of instructions. This can be implemented in PHP using the following syntax pseudo-code 
```
if(<condition>){
    <action if condition is true>
}else{
    <action if condition is false>
}
```

An example is an age verification system that enables only people who are 18+ to vote, which can be implemented in PHP as follows

```php
<?php
$age=19;
if($age>=18){
	echo 'You are allowed to vote';
}
else{
	echo 'You are not allowed to vote, because you are not 18 yet';
}
?>
```

  As you can see from the figure, if the condition is true, the block of instructions on the left will be executed. Conversely, if the condition is false,  the program will realize the actions defined by the block on the right. Intuitively, this gives two alternatives, and consequently, the software will behave in a different way and, potentially, produce different outputs. Conditional statements involve  just a set of instructions: code execution continues normally (sequentially) after the conditional statement.


As conditions take the form of statements that can be true or false, multiple expressions can be combined using logical operators. For example, an authentication system will check if both the email and the password entered by the user are the same as the values stored;
```php
<?php
$stored_email
$stored_password
$entered_email
$entered_password
if($stored_email==entered_email && $stored_password==$entered_password){
echo 'you are authenticated';
}else{
echo 'You entered the wrong credentials;
}
?>
```
Parentheses can be utilized to create more complex expressions that combine multiple conditions that include AND and OR operators in the same expressions, as in the following case:

```php
<?php
if(isWarmOutside AND (isHoliday OR isSunday)){
    echo 'I can go to swim!';
} else{
    echo 'I have to go to work';
}
?>
```

Conditional statements can be nested within one another. For instance, if we want to check if a user is omnivore, vegetarian or vegan, we could use the following code.

```php
<?php
if(eatMeat){
    echo 'is omnivore'
}else{
 if(eatEgg && eatMilk){
    echo isVegetarian
}else{
    echo is vegan
}
}
?>
```

If the block of code contains one statement only, curly braces can be omitted. For instance, the code from the above example could be written as follows:

```php
<?php
if(eatMeat) echo isOmnivore
else{
	if(eategg &&eatMilk) echo is vegearian
	else echo is vegan
}
?>
```
Please note that we could skip the parentheses in the first block because it consists of one statement only. When the block of code involves multiple statements, braces are necessary.


### If..elseif..else
In some cases, conditions might involve more than two choices. In this case, control structures can be utilized to check multiple alternatives using the elseif keyword. The PHP syntax is the following.
```
if(condition){
action if condition is true for alternative 1
}elseif(condition){
action if condition is true for alternative 2
}else{
action(s) if condition is something else;
}
```

Each of the elseif block will verify a different condition and will execute a different block of code. If none of the elseif conditions will be verified, the else block will be executed, as it will catch any other alternatives. Please note that the else block at the end can be omitted. 

For instance, we could design a museum ticketing system that applies a different discount to kids under 12, or to people who are aged 65+. We could realize it as follows

```php
<?php
$age=45;
if($age<12){
$discount=20%;
}elseif(age>65){
$discount=15%;
}else{
$discount=0%
}
echo 'Based on your age, your discount is '. $discount.
?>
```

This code is equivalent to the following, which demonstrates that the else block at the end can be omitted.

```php
<?php
$age=45;
$discount=0%
if($age<12){
$discount=20%;
}elseif(age>65){
$discount=15%;
}
echo 'Based on your age, your discount is '. $discount.
?>
```

PHP supports an unlimited number of elseif evaluations. However, adding too many of them will make your code harder to read and maintain. This is why the switch statement (discussed later in this chapter) is a better choice.

### Ternary operator or Shorthand if..else
Conditional structures are realized more often than one may think. Several times, this happens for executing two different sets of instructions. However, if else statements are utilized to assign a different value to a variable, or output a different value, based on a condition. Think about the example of the voting system: we just needed to print a different message depending on the age of the individual. The ternary operator is very useful in this circumstance, as it returns a different value based on the condition. It is called the ternary operator because it takes three operands - a condition, a result for true, and a result for false. 

Its syntax is the following
```
(condition) ? value if true : value if false
```

As you can see, the statement will not execute instructions. Instead, it will just produce a different value based on the condition. Then, the value can be stored in a variable or printed in the html page. For instance, we can implement the example from the voting system as foillows
```php
<?php
$age=19;
 echo ($age>18) ? 'You can vote' : 'You cannot vote';
?>
```

When used with simple conditions, the ternary logic is very effective because it results in simpler and more compact code, which is also easier to maintain. Moreover, as the  if..else, ternary operators can be nested with one another using parentheses. For instance,  we could implement the example from the discount at the museum as follows

<?php
($age)
?>

As you can see, while one operator makes our programs less verbose, nesting multiple operators affects the readability of our code, and makes them harder to maintain. This is why it is not recommended to nest more than 2-3 shorthand if..else operators. Despite its apparent complexity, ternary logic is extremely useful, and it is one of the most favorite constructs of experienced developers. Just remember that this statement can be utilized only in situations in which the if..else block returns a value. Its main difference with the regular if..else is that it cannot be utilized to realize two different types of instructions.

If you don't feel confident in using it yet, keep calm and use the standard if..else. If you want to learn to use, the best way to practice is to write an if..else block and then to convert it into ternary logic. The following examples are the two more common cases (the third one involves the return keyword and it is utilized in functions, which will be discussed in the next chapters).

```php
<?php
/* another basic usage */
$message = 'Hello '.($user->is_logged_in() ? $user->get('first_name') : 'Guest');
/* shorthand usage */
$message = 'Hello '.($user->get('first_name') ?: 'Guest');


/* echo, inline */
echo 'Based on your score, you are a ',($score > 10 ? 'genius' : 'nobody'); //harsh!

/* a bit tougher */
$score = 10;
$age = 20;
echo 'Taking into account your age and score, you are: ',($age > 10 ? ($score < 80 ? 'behind' : 'above average') : ($score < 50 ? 'behind' : 'above average')); // returns 'You are behind'

/* "thankfully-you-don't-need-to-maintain-this" level */
 $days = ($month == 2 ? ($year % 4 ? 28 : ($year % 100 ? 29 : ($year %400 ? 28 : 29))) : (($month - 1) % 7 % 2 ? 30 : 31)); //returns days in the given month
?>
```

### Switch...case
The elseif keyword is very useful you have multiple conditions to check for. However, in case you have to check for 4 or more alternatives, it becomes verbose and makes code harder to read and to maintain. The switch-case structure is an efficient alternative to the if-elseif-else statement: it tests a variable against a series of values until it finds a match, and then executes the block of code corresponding to that match. Its syntax is the following:
```
switch (expression)
  {
  case value1
     code to be executed if the expression is equal to value1;
     break;
  case value2
     code to be executed if the expression is equal to value2;
     break;
  case value3
     code to be executed if the expression is equal to value3;
     break;
  default
     (optional) code to be executed if none of the above conditions are true.
     break;
  }
?>
```
The keyword switch precedes the variable to be tested, whereas the keyword "case" introduces the possible values that the variable might have. Intuitively, the first case behaves similarly to the if part of an if..elseif structure whereas the others are equivalent to the elseif parts. The keyword "default" addresses the situation in which the variable does not match any of the cases tested earlier, and it is equivalent to the else block of an if..else/if...elseif..else structure in the sense that it catches cases not explicitly mentioned. It is optional.
There is a fundamental difference between the switch-case statement and the if-elseif-else statement: the if..elseif..else statement creates a different execution path for every block, whereas the switch statement evaluates cases sequentially and executes instructions line by line. As a result, if a case is verified, PHP will automatically execute all the following lines of code, including any subsequent case statements (even if they are not verified) until it reaches the end of the switch block. To prevent this from happening, the keyword break is added to the end of each case block. The break statement is utilized to exit from the current block and to continue execution after the end of the structure in which the execution flow is currently in. As a result, the break statement at the end of each case will prevent PHP from automatically executing all the statements following a the block of a case that verifies a condition. 

Example with restaurant menu
```php
<?php
$day='monday';
switch($day){
	case 'monday': $menu=
}
?>
```
The switch..case structure is the most  efficient way for working with conditions that involve the status of an entity, such as a user, an order, or a post, as in the example below. 

```php
<?php
switch($status)
	case -2: 
	case -1: canceled
	
	case 0:
		'created'
		
	case 1:
		'paid'
	case 4:
		delivered
?>
```

In case multiple alternative correspond to the same code, cases can be listed after one another, as shown in the next example
[example with case case]


One of the main differences between the switch..case and the if..elseif..else structure is in the type of comparison operators supported by the statement. By default, the switch..case checks if a variable is equal to any of the options presented in each case, whereas the if..elseif...else block enables making more types of comparisons. For instance, using the switch..case structure for comparing if the value of a variable is less than a given value requires some tweaking, as shown in the following example. 

```php
<?php
switch (true) {
    case $count <= 20:
        $priority = 'low';
        break;

    case $count <= 40:
        $priority = 'medium';
        break;

    case $count <= 60:
        $priority = 'high';
        break;

    default:
        $priority = 'severe';
        break;
}
?>
```

### Which conditional statement do I use?
The if..else block alone is powerful enough to serve most of the cases, and elseif statements can be introduced whenever there are more than 2 conditions to check. The switch ..case is the best choice for comparing a variable that has more than 3 possible alternative values. 
Whenever each of the two blocks of an if..else statement contains one instruction only, and it is used to output or assign a value, it can be replaced with the ternary operator to make the code shorter.
As the purpose of conditional statements is very clear,  choosing the most appropriate conditional statement usually is very straightforward. Instead, one of the trickiest aspects is optimizing our code to avoid nesting too many if..else statements: stacking more than 3 levels of if..else blocks can result in a source code that is very hard to read and maintain. To this end, designing an algorithm properly before implementing it is crucial for writing cleaner code; nevertheless, you can always identify ways to optimize your scripts after writing a version that works, though this might require completely rewriting several lines. Moreover, functional programming (described later) will help divide complex algorithms into smaller blocks and conquer their complexity, in addition to making them easier to write and maintain. 

## Loops
Conditional statements is taking decisions automatically and choosing between two options without the supervision of a human, which is pretty powerful. Instead, loops enable iterating over sequences of actions a number of times if a condition is verified. Therefore, they are particularly useful in realizing operations, such as, tedious tasks, repeatedly, or even indefinitely. For instance, loops are utilized to send e-mails to all the users registered to a website, to check for new e-mail at certain interval, to display a list of articles, or to realize complex calculations. If you combine this feature with the capability of conditional statements and with the speed of execution of a computer, the magic is done! 

Typically, the loop evaluates a condition that will determine whether the execution will iterate over a block of instructions or not. If the condition is verified, a set of statements will be executed repeatedly as long as the condition will give the same boolean result. When the value of the expression in the condition will change, it will not be verified, and the program will exit the loop and continue its execution after the loop.

Although there are mainly 4 types of loops (and all of them are implemented in PHP), they all serve the same purpose, though their behavior is slightly different:
- while verifies a condition and executes a block of code indefinitely, until the condition changes
- do while, executes a block of code and verifies if the condition has changed to decide whether to iterate again
-for repeats a block of code a predefined number of times
-foreach loops over a specified list of items and executes a block of code as many times as the number of items in the list

### While 
The while loop is the simplest type of loop, as it checks for the condition and executes a block of statements until the condition is false.  Its syntax is the following
```
while(expression){
	
}
```

The while loop will test if the expression within parentheses is verified. If the condition is false, the program will simply skip the instructions enclosed in curly braces. Conversely, if the expression is true, the program will enter the block of code enclosed in curly braces and it will execute it. Then, the program will go back to the beginning of the while loop, and the condition will be checked again. If the expression will result true, the block will be repeated, otherwise, execution will continue after the block of the while. Depending on how the algorithm is designed, the statements in the while loop will be skipped or they will be executed 1 or more times (and they can even be repeated an indefinitely).

As for control structures, the condition is specified within parentheses after the keyword while. Also, the block of instructions is identified by curly braces.

```php
<?php
$a=4;
$b=0;
while($b<$a){
	echo 'a: ;.$a;
	echo 'b: '.$b ;
	$a++
}
?>
```

The previous example will check whether b is smaller than a, if so, it will loop. The program will continue looping until the condition is false, that is, b will be equal to a. This will happen after 5 loops.

An important step in using the while loop is initializing the variable that will be utilized in the expression that checks whether the condition is verified. Omitting the statement, or failing to initialize the variable will result in an error, or in a loop that will never be executed.

As shown for the if conditional statement, curly braces  can be omitted only if it consists of a single line.

$i=0
while($i<5) echo $i++;

Conditions play a crucial role in structures for flow control, and specifically in loops: they determine the exit condition for the loop. Failing to define an exit condition properly will result in a loop that either will never execute, or will never terminate its iteration. For instance, if we replace the  condition in the example above with while($i>5), the program will never enter in the block of code defined in the while. Also, increment or decrement operations that affect the exit condition are crucial: if we omitted the increment operation, or if we replaced it with echo $i, the loop will never verify its termination condition, thus, forcing the program in the block forever. This type of errors can cause the web server to crash, because they will keep it constantly engaged in a never-ending process.

The value of expressions in a condition must be of boolean type. As a result, the boolean values true and false can be utilized in condition. This will produce interesting results: intuitively, in the following code the block of instructions in the loop will never be executed. As it does not make sense to write code that will never be utilized, the following example is completely useless
  
while(false){
}

On the contrary,  the following code will be executed forever, because the expression in the condition will never become false. Although this might also seem useless, it is very common in programs that are always active. Examples are web servers, services of the Operating System, or loops for rendering scenese in video games. By keeping execution in an infinite iteration, we will prevent it to reach the end of the program and to terminate its processing: as a result, the program will stay alive and repeat a set of operations.   

```php
<?php
while(true){
checkMail()
delay()
}
?>
```

In the previous example, the code is deliberately designed to force the program to repeatedly execute the same operations over and over again. 

### Do..while
The do..while loop is very similar to the while loop and it is utilized very rarely, compared to the while. Its syntax is the following

```
do{

}while(condition);
```

As you can see, the main difference between the while and the do...while loop is in that the sequence of instructions in the block of the loop appears before the condition is evaluated. As programming languages execute statements sequentlially,  the program will execute the statements in the block, and then it will verify whether the condition is true. As a result, the block will be executed at least one time, even if the condition is false. Then, it will be repeated if the condition is verified. 

Let's write the previous examples in a do...while form, so that we can see the difference between the two loops.

```php
<?php
$a=4;
$b=0;
do{
	echo 'a: ;.$a;
	echo 'b: '.$b ;
	$a++
}while($b<$a)
?>
```

Indeed, the code looks very similar to the previous example, as the only change (in addition to the "do" keyword) is the condition, which now is at the end of the loop. However, the result will be different in that it will loop one less time. The second example about the while loop, when translated using the do..while (shown below), will produce similar behavior. We could make them work in exactly the same way as their while counterparts by tweaking the exit condition, or by initializing the variables differently.

$i=0
do{
echo $i++
}while($i<5);

The do..while loop might seem useless, at this point. However, it can be suitable for some applications, as shown below. Nevertheless, programmers prefer to use the while loop. In the following example the do..while loop is utilized to calculate the factorial of a number.

```php
<?php
$number=5;
$i=0;
do{
$factorial*=$number;
$i++;
}while($i<$number);
echo $factorial;
?>
```

### For
As demonstrated by all the examples so far, the use of loops typically involves three steps: initializing a variable that will be utilized to verify the exit condition, testing the exit condition, and changing the value of the variable, so that the exit condition will be reached, at some point. 

Although there are exceptions, such as, the example involving generating a new string, the exit condition of most of the loops involves an integer variable that is (1) initialized, (2) tested, and then (3) manipulated, that is, incremented or decremented. In these situations, the for loop is the most convenient choice, as it enables to incorporate the three steps described above in a single expression. Its syntax is the following

```
for(initialization;test;manipulation){
actions
}
```

As for the while loop, a keyword introduces the block. Then, in parentheses, there are three expression. The first is used to initialize the variable that will be used in the loop, and it's executed the first time the program encounters the for. The second expression is executed at the beginning of every loop, and if it evaluates to true, the statements in curly braces will be executed, otherwise they will be skipped. The third expression will be executed at the end of every loop, after all the instructions in the block have been executed. In general, the third expression alters the the value of the variable that is utilized in the second expression, so that the condition will not be verified anymore, at some point.

We can combine the switch case and the for loop to print the whole calendar for a specific  year: also, the following code shows how conditional statements and loops can be nested within one another to realize a more sophisticated behavior.

[example with for, leap and if]

[example combining leap year and printing all the days] 

For instance, if we want to implement a traffic light in PHP, we can use the following code, which allows us to represent the current color and the transition to the next color:

$lightColor='green';
if($lightcolor=='green'){
echo '<span style='color:"'' THe traffic light is Green;
$lightColor='yellow';
} elseif($lightColor='red'){
echo '<span style='color:"'' THe traffic light is red;
$lightColor='green'
} else{
the traffic light is yellow.
$lightColor=red
}

In general, when utilized to loop through arrays, the for structure is not expected to add or remove elements, as it might produce errors. In the previous two examples, the function count(array) is utilized to get the length of the array. Although it could be incorporated in the definition of the loop, this would cause the program to calculate the length of the array at every loop, when the condition is evaluated. However, as the length of the array is not expected to change during the loop, this would just be a waste of processing resources, which could be significant if the array is very large. By calculating the length of the array before the loop, we can optimize the performance of our code.

### Foreach
The fourth type of interative structure implemented in PHP is the foreach loop, which is utilized primarily for navigating arrays and enumerable structures (e.g., properties of objects and resoruces). The syntax of this type of loop is different than the previous ones, with specific regard to its exit condition, which does not involve any variable comparison. The general structure of a foreach loop is defined by the following pseudo-code:
```
foreach(set as element){
	instructions
}
```
The statement in  parentheses has two main components, set and element. The former is the variable that contains a set of elements, that is, the array or recordset we want to loop through. The latter is a variable name that will contain each of the elements of the array. When this block is encountered the first time, the program will evaluate if the set contains any elements; if so, the variable specified in the element will be assigned with the first element of the array, so that it will be available within the loop. Then, the block of instructions will be executed, and it will have access to the element of the array via the variable. After the block and at the beginning of every loop, the program will go back to the condition evaluation, and it will check if there's another element. If so, the variable specified in element will be overweritten, otherwise the loop will terminate. The foreach block will naturally end its operation when all the elements of the array have been considered.

An implementation of the foreach loop is the following.
$beatles=['John Lennon','Paul McCartney','George Harrison','Ringo Starr'];
foreach($beatles as $member){
	echo $member;
	echo '<br />';
}

As you can see from the example, the first element of the condition is the name of the array to be considered (i.e., $beatles), whereas the second element is a new arbitrary variable name ($member). The content of the second variable will change at every iteration. Intuitively, the main advantage of the foreach loop in comparison with the other types of iteration structuresis  in that we don't have to manually deal with the length of the array and we don't have to worry about the exit condition: the program will automatically stop iterating when there will be no more elements in the array.

As in other  structures for flow control, curly braces that define the block can be omitted if there is only one instruction. 
$months[];
foreach($months as $month) echo $month;

The following example implements  the foreach loop to display every month in a year.

As mentioned previously, the foreach loop automatically assigns the value of the element to a variable. Therefore, in case of an associative array, we need to use a slightly different syntax to access the key of the element, together with its values, as described in the pseudo-code below:
```
foreach(set as key=>value){
actions
} 
```
Intuitively, at every loop the foreach structure will conside a new element: key is the name of the variable that will contain the key of the element, whereas value is the name of the variable that will receive the value of the elmement. The following example will display the name of the month and the days in every month

$months=['January','February','March'];
foreach($months as $month=>$days){
}

As in the example with indexed arrays, the variables that will be assigned with the key and value of the element can be named arbitrarily. As foreach loops greatly simplify working with arrays, they are typically preferred to for loops. However, there is a main difference between the two constructs: at each iteration the foreach loop makes a copy of the element (or of its key and value) and assigns it to the variable (or to the variables) specified in the parentheses. As a result, any change to the variable will not affect the content of the array. Consider the following example

$days_of_week=
$index=0;
foreach($days_of_week as $day) {
$day='day'.$i++;
echo $day;
}
print_r $days_of_week;

Although the assignment statement in the block of the loop changes the value of the variable day, it will not modify the content of the corresponding element of the array $days_of_week, because $day will contain  a copy of each of the elements of the array. Instead, the for loop does not suffer from this limitation, as the elements of the array will be accessed by their index, directly from within the array itself.  Let's implement the previous example using a for loop and let's analyze the difference

$days_of_week=
$index=0;
for($index=0l$days_of_week as $day) {
$day='day'.$i++;
echo $day;
}
print_r $days_of_week;

In this case, the integer variable is utilized to access the element of the array $days_of_week by its index. As a result, the assignment instruction in the block of the loop will access and change the content of the array $days_of_week. Using a for loop is the only way to iterate through the elements of an array to modify their content.  Unfortunately, the for loop cannot be utilized to directly access the elements of an associative array, because it does not necessarily have numeric and sequential keys. Nevertheless, we can use the function array_keys to access the indexed array containing the keys of the array, and then we can use a foreach loop to access each element of the array by its key as follows.

$days_of_week=['monday'=>'first day'...
$keys=array_keys($days_of_week)
foreach($keys as $key){

}

The following code has exactly the same behavior of the example above, though it uses a for loop instead of foreach.

for(i...).


Foreach loops can be utilized in combination with other types of data structures, such as, objects and resources, as discussed in the next chapters. 




### Nesting loops
As for conditional statements, loops can be nested to one another. This can be useful in several cases, such as the following:
-  to loop through the elements of a matrix (that is, a multidimensional array), we can use two nested for loops, one for looping through the rows, and one for looping through columns (see example below).
-  to read the list of files in each of the directories of the current folder: to this end, we can use two nested loops, one that explores each of the the directories, and one that lists all the files (see example in the chapter about working with files).  
- to read all the lines and all the fields of a text file formatted according to the comma separated value (CSV) format (see example in the chapter about working with files).
- to read or insert multiple related records in a database (see example in the chapter about databases).
There are many other circumstances in which it is necessary to nest loops within one another, and all of them involve multi-dimensional problems that can be reduced to simple one-dimensional algorithms thanks to the use of functional programming (discussed in the next chapter).

Example with while

Example with for

Example with foreach

### Break and continue
The break and continue keywords are two very useful tools for working with loops, despite they are employed very rarely. 

As described in the section about the switch...case conditional statement, the  "break" keyword enables exiting the switch..case block, thus preventing the execution of the statements following the instructions of a case whose condition is verified. When used in a loop, the break keyword has a similar behavior, in that it stops the execution of the next statements in the block of code and it exits the for loop completely. This can be very useful when we are searching a string for a character, or when e are looping througharray to find a specific element: after we find the string or the element that matches our criteria, we don't want to continue evaluating the next elements. To this end, we can use the break keyword after the match is found, to exit the loop and continue the execution of the program after the end of the block. 

In the following example, a foreach loop is utilized to iterate over an associative array containing a set of users to verify if the email and password entered by the user match the credentials stored in the system. Once a match is found, the break keyword prevents from considering the subsequent elements.

$users
foreach($users as $username=>$password){
if($username==$entered_username && $password){
$match=true;
break;
}
} 
echo $match ? 'Welcome to our website' : 'The username or password does not match'

The continue statement is similar to break in that it prevents the program from executing the next lines in the block of the loop. However, break will completely exit the loop, whereas continue will  return to the condition evaluation. As a result, the program will stay in the loop and it will test the expression in the exit condition: if it is verified, the block of instructions will be executed again, otherwise the program will exit the block. This can be useful if we want to match more than one elements: by using continue instead of break, we will continue looping after the first match. In the following example, we want to display all the orders that are waiting to be shipped.  

$orders=[id...status
foreach($orders as $id=>$status){
if($username==$entered_username && $password){
$match=true;
break;
}
} 
echo $match ? 'Welcome to our website' : 'The username or password does not match'

The keywords Break and continue can be utilized with any type of loop. Moreover, in case of nested loops, they have effect on the innermost structure, only.


### Alternative syntax
TO BE DEFINED

### Which loop do I use?
As described in this chapter, there are 4 types of loops in PHP.  Especially at the beginning,  it might be difficult to choose which one to use for solving a problem. The decision can be simplified by reasoning by exclusion:
1. the foreach loop is utilized mainly for looping through the elements of an array, when we need to access their content but don't need to modify it; if you don't need to access the elements of the array at all (e.g., if you need to execute a loop a number of times defined by the length of the array) or if you need to modify the content of the elements of the array, then you can use the for loop.
2. the for loop works at its best when utilized  to execute a loop a specific number of times (e.g., based on the length of an array or a string, or a defined number): especially if the code in the block contains several lines, the  compact structure of the for helps maintaining the code short and easy to read.
3. the while loop can be utilized for most of the remaining cases, including those that will work best with a do...while loop. Typically, it will be utilized for loops that don't involve numeric conditions, such as verifying the content of a string, reading a file, or looping through the rows of a recordset (discussed later)
4. the do...while is the least utilized, and it will serve very specific purposes; you can always write a while loop and then optimize it with a do...while. 