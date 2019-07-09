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

###


