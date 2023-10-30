# Javascript Interview Guide

# A simple guide for javascript if you are preparing for javascript interviews.

# Closure
    
Closure is one of the most confusing topics but I will try to explain this in a very simple way.
    
A closure is a feature that allows inner functions to access scope or variables of the outer functions.
    
    Example

    function outer(){
      function inner(){
        console.log("Mohit")
        }
        inner()
    }
    
    outer()

In the above example, there is an "outer" func and an "inner" func. When we are invoking the "outer" func, we are getting the output as Mohit. This means we      are able to invoke the 'inner' func by an "outer" func.

    Example 2

    function outer(name, age){
      const myAge = age;
        function inner(){
          console.log(`${name} - ${age}`)
        }

      return inner
    }

    // 2 different ways

    outer("Mohit", 21)() // Mohit - 21

    const mohit = outer("Mohit", 21)
    mohit() // Mohit - 21

    
In the 2nd Example, there are 2 ways to call the function
    
1 -> By calling the outer function followed by bracket.

2 -> By calling the outer function stored in a variable. This is more common than the other.

Real Magic of closure

As you can see myAge variable is defined within the scope of the outer function but the mohit variable is able to access this.

This is due to closure that we are able to access myAge outside the scope of outer function.

# Hoisting

- Hoisting is one of the most common questions asked in the interviews.
- Hoisting makes some types of variables accessible in the code before they are actually declared.
- Variables are lifted to the top of their scope due to hoisting.

Normal use case

- We mostly use the functions in the following way.
  
      function name(){
          console.log("Mohit");
      }
  
      name() // Mohit

Func declarations

- Function declarations are always hoisted i.e we can use them before defining them.

      age()
  
      function age(){
          console.log(21)
      }

      // 21

Function Expressions

- Function expressions are not hoisted i.e you can use them before declaring.

      age()
        
      const age = function(){
          console.log(21)
      }

      // Uncaught ReferenceError : Cannot access age before initialization

Var Variables

- Var variables are hoisted but it comes with a downside. You can access the var variables declaration but not the value i.e it returns undefined.

      console.log(age) // undefined
      console.log(city) // undefined

      var city = "Jaiput"
      var age = 21

Let Variables

- Let variables are not hoisted

      console.log(name)
      // Uncaught ReferenceError : Cannot access name before initialization
    
      let name = "Mohit"

Const Variables

- variables defined with const are also not hoisted.

      console.log(age)
      // Uncaught ReferenceError : Cannot access name before initialization

      const age = 21


# Template Literals

- Template literals allow us to use strings or variables in the form of string.
- The introduction of template literals is one of the most loved features of ES-6
- Before ES-6, we use single or double quotes to wrap a string literals and it offers limited function.

Before Template literals

    const name = "Mohit";
    const age = 21;

    const info = "My name is " + name + " and my age is " + age;

    console.log(info)
    // My name is mohit and my age is 21

After Template literals

    const name = "Mohit";
    const age = 21;

    const info_new = `My name is ${name} and my ${age} is age`;

    console.log(info_new)
    // My name is mohit and my age is 21


# This Keyword

- The 'this' keyword is a reference variable that refers to the object that is executing the current piece of code.

      const mohit = {
          name: "Mohit",
          age: 21,
          info(){
              console.log(`My name is ${this.name}`)
          }
      }
      mohit.info()
      // My name is Mohit

Different values

The 'this' keyword has different values depending upon its use.

- Used Alone
- Used in Regular Function
- Used in Object Method
- Regular function in strict mode

1. Used Alone

- Whenever 'this' keyword is used alone, it always refers to the global window object.
     
       console.log(this);
       /* Window { window: Window, self: Window,
          document: document, name: '', location: Location..., ...}

2. Used in Regular Function

- In the case of a regular function the 'this' keyword also refers to the global window object.

        function mohit(){
              console.log("Mohit")
              console.log(this)
        }

        mohit();

       // mohit
       /* Window { window: Window, self: Window,
          document: document, name: '', location: Location..., ...}

3. Used in Object Method

- Function within an object is called Method. In such a case, the 'this' keyword refers to the object itself.

        const about = {
          name: "Mohit",
          age: 21,
          more(){
              const country = "India"
              console.log(country);
              console.log(this);
          }
       }

       about.more()

       // India
      // { name: 'Mohit', age: 21 }

4. Regular Function Strict Mode

- If you are using strict mode, the 'this' keyword used in the regular function will be undefined.

          "use strict"

          function mohit(){
              console.log("Mohit")
              console.log(this)
          }

          mohit()
