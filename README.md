# php topics

### How can we check a constant is defined or not?
we can use the "defined()" function to check constant is defined or not.It dosen't care about constants value.
```
Ex:
define('HOST',"localhost");
if(defined('HOST')){
echo "constant is existed";
}else{
echo "Not existed";
}
```

### How can we get all constants?
To get all constants including those created by PHP use the "get_defined_constants" function.
EX:
$constants = get_defined_constants(); 
var_dump($constants);

### array constants
```
define('VALUES',[2,3]);
echo VALUES[1]; //3
echo VALUES[0]; //2

plain constant:

const VALUES =[2,4];
print ANSWER[1] . ANSWER[0]; // 42
```

### difference between __METHOD__ and __FUNCTION__?

__FUNCTION__ returns only the name of the function whereas __METHOD__ returns the name of the class along with the name of the function.
```
class trick {
public function doit() {
echo __FUNCTION__; }
public function doitagain() {
echo __METHOD__; }
}
$obj = new trick();
$obj->doit(); // Outputs: doit 
$obj->doitagain(); // Outputs: trick::doitagain
```

### Type juggling

php is weakly typed language. It does not require explicit declartion of data types.Which means varaible data type conversion automatically.
Ex: $a = "2"   //string

### what is the use of Null Coalescing Operator(??)?

This operator is introduced in PHP7. It is used to replace the ternary operation in conjunction with isset() function. The Null coalescing operator returns its first operand if it exists and is not NULL; otherwise it returns its second operand.
```
<?php
   // fetch the value of $_GET['user'] and returns 'not passed'
   // if username is not passed
   $username = $_GET['username'] ?? 'not passed';
   print($username);
   print("<br/>");

   // Equivalent code using ternary operator
   $username = isset($_GET['username']) ? $_GET['username'] : 'not passed';
   print($username);
   print("<br/>");
   // Chaining ?? operation
   $username = $_GET['username'] ?? $_POST['username'] ?? 'not passed';
   print($username);
?>
```

### Spaceship Operator (<==>)?

PHP7 introduces new kind of operator, which can be used to comapre expressions. This operator will returns -1, 0 or 1 if the first expression is lessthan, equal to, or greater than the second expression.
```
// Integers
print (1 <=> 1); // 0 
print (1 <=> 2); // -1 
print (2 <=> 1); // 1
```
### difference between call by value and call by reference?

__call by value__ : call by value means passing the variable directly to a function. The called function uses the value in local variable.
If any changes made inside the functions are not reflected in actual function of parameters of caller.

```
<?php
function example($x){
  
  $x = $x + 10;
  echo $x;
}

$x= 20;
example($x); //30
echo $x; //20
```

__call by reference__ : While calling function, instead of passing the values of variables, we pass the address of varaibles. so any changes made inside the function that are actually reflected in actual parameters of caller.

Ex:
```
<?php
function example(&$x){
  
  $x = $x + 10;
  echo $x;
}

$x= 20;
example($x); //30
echo $x;  //30
```
### How can we check if key exists or not in an array?

we can use ```array_key_exists()``` or ```isset()``` or ```!empty()```

Ex:
```
$array =[
'id' => 1,
'name'=> 'raju',
];
array_key_exists('name', $array); // true
isset($array['name']);  //true
!empty($array['name']); //true
```
### How to validate array type?

use ```is_array()``` returns true if a variable is an array.

we can also use the ```gettype()``` function.
EX:
```$integer = 1337;
$array = [1337, 42];
gettype($integer) === 'array'; // false 
gettype($array) === 'array'; // true
```
### How to check if a value exists in an array?

The function ```in_array()``` returns true if an item exists in an array.

```
$fruits = ['banana', 'apple'];
$foo = in_array('banana', $fruits); //true
```
we can also use the function ```array_search()``` to get the key of a specific item in an array.
```
$array = ['sachin','gowtham','yuvi'];
$result = array_search('gowtham',$array);
echo $result; //1
```
In PHP5.5 and later we can you use ```array_column``` in conjuction with ```array_search()```

__checking if value exists in an associative array:___
```
$array =[
    [ 'name' => 'sachin',
     'score' => '102',
    ],
    [ 'name' => 'gowtham',
     'score' => '125',
    ],
    [ 'name' => 'yuvi',
     'score' => '98',
    ],
 ];
 $key = array_search(125, array_column($array, 'score')); //1
````
### Destructring array using list()

```list()``` assign variables as if they were an array.

```
$array = ['sachin', '103', 'cricketer'];
list($name, $score, $desg) = $array;
```
### array_reduce in php

```array_reduce``` reduces array into single value, The ```array_reduce``` will go through every item with the result from last iteration and produce new value to the next iteration.

Ex:
```
$result = array_reduce([1,2,3,4,5], function($carry, $item){
return $carry + $item;
});
echo $result; //15
```
__find the largest number in an array using array_reduce?__
```$result = array_reduce([1,2,3,4,5], function($carry, $item){
return $item > $carry ? $item : $carry;
});
echo $result;
```
### how can we exchange values with keys?

```array_flip()``` function will exchange the all keys with its elements.
```
$colors = array(
    'one' => 'red',
    'two' => 'blue',
    'three' => 'yellow',
);
array_flip($colors); //will output
array(
    'red' => 'one',
    'blue' => 'two',
    'yellow' => 'three'
)
```






