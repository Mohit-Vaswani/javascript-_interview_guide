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
