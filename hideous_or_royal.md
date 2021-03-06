### syntax parser
### execution context
   * Creation and Hoisting ` Sets up the functions and variables in the memory`
   * Code Execution        `Runs your code line by line`
### lexical environment
### single threded


------
> In javaScript when you create a variable or a function and you are not inside a function those variables and functions get
attached to the global object.

```
var a = 10;

function b() {};

a // 10
window.a //10
```

### call by reference vs. by value
  1. Primitive type variable like string,number are always pass as pass by value.
  2. Array and Object is passed as pass by reference or pass by value based on these two condition.
     - if you are changing value of that Object or array with new Object or Array then it is pass by Value.
         ```
        object1 = {item: "car"};
          array1=[1,2,3];
          ```

        here you are assigning new object or array to old one.you are not changing the value of property of old object.so it is pass by value.
        
      - if you are changing a property value of an object or array then it is pass by Reference.
        ```
        object1.item= "car";
          array1[0]=9;
          ```


        here you are changing a property value of old object.you are not assigning new object or array to old one.so it is pass by reference.
        
Example
1.
```

    function passVar(object1, object2, number1) {

          object1.key1= "laptop";
          object2 = {
              key2: "computer"
          };
          number1 = number1 + 1;
    }

    var object1 = {
        key1: "car"
    };
    var object2 = {
        key2: "bike"
    };
    var number1 = 10;

    passVar(object1, object2, number1);
    console.log(object1.key1);
    console.log(object2.key2);
    console.log(number1);

Output: -
    laptop
    bike
    10
```
Example
2.
```
function changeParam(x, y, z) {
  x = 3;
  y = "new string";
  z["key2"] = "new";
  z["key3"] = "newer";

  z = {"new" : "object"};
}

var a = 1,
    b = "something",
    c = {"key1" : "whatever", "key2" : "original value"};

changeParam(a, b, c);

console.log(c)
// 

{key1: "whatever", key2: "new", key3: "newer"}
```

- Basic explanation
  ```
  // by value (primitives)
  var a = 3;
  var b;

  b = a;
  a = 2;

  console.log(a);
  console.log(b);
```

```
    // by reference (all objects (including functions))
    var c = { greeting: 'hi' };
    var d;

    d = c;
    c.greeting = 'hello'; // mutate

    console.log(c);
    console.log(d);

    // by reference (even as parameters)
    function changeGreeting(obj) {
        obj.greeting = 'Hola'; // mutate   
    }

    changeGreeting(d);
    console.log(c);
    console.log(d);

    // equals operator sets up new memory space (new address)
    c = { greeting: 'howdy' };
    console.log(c);
    console.log(d);```


## Arguments object
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments


```
function greet(firstname, lastname, language) {
 
    language = language || 'en';
    
    if (arguments.length === 0) {
        console.log('Missing parameters!');
        console.log('-------------');
        return;
    }
    
    console.log(firstname);
    console.log(lastname);
    console.log(language);
    console.log(arguments);
    console.log('arg 0: ' + arguments[0]);
    console.log('-------------');
    
}

greet();
greet('John');
greet('John', 'Doe');
greet('John', 'Doe', 'es');

// in ES6 I can do:  function greet(firstname, ...other)
// and 'other' will be an array that contains the rest of the arguments
```
