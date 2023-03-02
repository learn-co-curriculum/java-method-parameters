# Method Parameters

## Learning Goals

- Discuss method parameters.
- Show how to pass parameters to methods.

## Methods with Parameters

Let's continue the block party example we saw in the last lesson. Assume a
neighbor is walking around and asking each guest what they would like cooked on
the grill. Let's create a method to print out what someone would like cooked:

```java
public class MethodExample {

    public static void welcome() {
        System.out.println("Welcome neighbors!");
    }

    public static void announce() {
        System.out.println("Food will be served in 15 minutes.");
    }

    public static void farewell() {
        System.out.println("Thanks for coming neighbors!");
        System.out.println("See you next year!");
    }
    
    // New method
    public static void cook(String food) {
        System.out.println("Okay, I can cook " + food);
    }

    public static void main (String[] args) {
        welcome();
        cook("Hot dogs");    // Call the new method cook()
        farewell();
    }
}
```

In the above code, we created a new method called `cook()`. Let's take a
closer look at this method header:

![method-header](https://curriculum-content.s3.amazonaws.com/java-mod-1/methods-with-parameters/method-header-parameters.png)

The only difference between the `cook()` method and the other methods we have
been working with thus far is that the `cook()` method does take in a parameter.
We notice the `(String food)`. Since there is something between the parentheses,
we can say that this method _does_ take in parameters. When a method takes in
parameter(s), each parameter needs to have a data type and a name - just like
declaring a variable! This is because the parameters will act like local
variables in the method itself.

Let's step through the code and see what happens when we call the `cook()`
method:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=public%20class%20MethodExample%20%7B%0A%0A%20%20%20%20public%20static%20void%20welcome%28%29%20%7B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Welcome%20neighbors!%22%29%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20public%20static%20void%20announce%28%29%20%7B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Food%20will%20be%20served%20in%2015%20minutes.%22%29%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20public%20static%20void%20farewell%28%29%20%7B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Thanks%20for%20coming%20neighbors!%22%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22See%20you%20next%20year!%22%29%3B%0A%20%20%20%20%7D%0A%20%20%20%20%0A%20%20%20%20//%20New%20method%0A%20%20%20%20public%20static%20void%20cook%28String%20food%29%20%7B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Okay,%20I%20can%20cook%20%22%20%2B%20food%29%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20public%20static%20void%20main%20%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20welcome%28%29%3B%0A%20%20%20%20%20%20%20%20cook%28%22Hot%20dogs%22%29%3B%20%20%20%20//%20Call%20the%20new%20method%20cook%28%29%0A%20%20%20%20%20%20%20%20farewell%28%29%3B%0A%20%20%20%20%7D%0A%7D&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=6&heapPrimitives=nevernest&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

Notice when we click "Next >", the execution jumps to the `cook()` method. But
also note that the `food` variable is now set to `"Hot dogs"`. In the `main()`
method, we call the `cook()` method and pass in the argument "Hot
dogs". This value then gets copied when calling the `cook()` method and assigns
the parameter variable, `food` to "Hot dogs".

![method-parameter-passing](https://curriculum-content.s3.amazonaws.com/java-mod-1/methods-with-parameters/method-parameter-passing-visual.png)

Note: **Parameters** refers to the list of variables in a method declaration.
**Arguments** are the actual values that are passed in when the method is
invoked. When a method is invoked, the arguments used must match the
declaration's parameters in type and order.

`food` acts like a local variable now within the `cook()` method; meaning, the
`food` variable is only accessible within the `cook()` method. We would not be
able to access the value of `food` outside the `cook()` method.

If we continue to click "Next >" we'll see the new output of our block party
program:

```text
Welcome neighbors!
Okay, I can cook Hot dogs
Thanks for coming neighbors!
See you next year!
```

We can slightly modify the code as such:

```java
public class MethodExample {

    public static void welcome() {
        System.out.println("Welcome neighbors!");
    }

    public static void announce() {
        System.out.println("Food will be served in 15 minutes.");
    }

    public static void farewell() {
        System.out.println("Thanks for coming neighbors!");
        System.out.println("See you next year!");
    }

    // New method
    public static void cook(String food) {
        System.out.println("Okay, I can cook " + food);
    }

    public static void main (String[] args) {
        String hotDogs = "Hot dogs";    // Store "Hot dogs" in a local variable
        welcome();
        cook(hotDogs);    // Pass in the local variable
        farewell();
    }
}
```

This code will perform the same output as before. Except this time, we will pass
in a variable that holds the value "Hot dogs".

![call-method-cook-with-local-variable](https://curriculum-content.s3.amazonaws.com/java-mod-1/methods-with-parameters/java-visualizer-method-parameter-local-variable.png)

Notice the variable `hotDogs` sitting on the stack. When we call the `cook()`
method, the value of `hotDogs` will get "copied" into the `food` variable. Java
will proceed with the execution in the same way we saw prior.

Let's expand on our `cook()` method. Assume the neighbor taking food orders also
wants to know how much of each food every guest would want:

```java
public class MethodExample {

    public static void welcome() {
        System.out.println("Welcome neighbors!");
    }

    public static void farewell() {
        System.out.println("Thanks for coming neighbors!");
        System.out.println("See you next year!");
    }

    public static void cook(String food, int quantity) {
        System.out.println("Okay, I can cook " + quantity + " " + food);
    }

    public static void main (String[] args) {
        welcome();
        cook("Hot dogs", 2);    // Call the new method cook()
        farewell();
    }
}
```

Note: We removed the `announce()` method from this iteration of updates since
the `announce()` method was never called or being used.

The `cook()` method now takes in two parameters. When we want a method to take
in multiple parameters, we must separate each parameter definition with a comma,
`,`. The `cook()` method now takes in a `String` variable to hold the type of
food each neighbor would like and an `int` variable that describes how much each
guest would like of the described food.

<details>
    <summary>If we run this program now, what will the output be?</summary>

  <p>Answer: <br>
     <p>Welcome neighbors<br>Okay, I can cook 2 Hot dogs<br>Thanks for coming neighbors!<br>See you next year!</p>
  </p>

  <p>We pass in two parameters now to the <code>cook()</code> method when calling it from the <code>main()</code> method. Each value matches up with the parameter definitions in the method header for <code>cook()</code> and the values we pass in will be copied to the parameters <code>food</code> and <code>quantity</code>.</p>
  <img src="https://curriculum-content.s3.amazonaws.com/java-mod-1/methods-with-parameters/method-multiple-parameter-passing-visual.png">

</details>

## Comprehension Check

Consider the following code:

```java
public class GreetingExample {
    public static void greeting(String name) {
        System.out.println("Hello " + name);
    }
}
```

<details>
    <summary>Describe the method above by looking at the method header.</summary>

  <p>Answer: <br>
     <p>The <code>greeting()</code> method takes in one <code>String</code> parameter called <code>name</code>. It does not return anything.</p>
  </p>
</details>

<details>
    <summary>What is the output of this program?</summary>

  <p>Answer: <br>
     <p>Nothing. The method is never called.</p>
  </p>
</details>

<details>
    <summary>How would you call this method from the <code>main()</code> method given the name "Lizzie"?</summary>

  <p>Answer: <br>
     <p><code>greeting("Lizzie");</code></p>
  </p>

  <p>We call a static method by writing out the method name and its parameters where we want to execute the method's block statements.</p>
</details>

Consider the following code:

```java
public class SongExample {

  public static void verse(String animal, String noise)
  {
    System.out.println( "Old MacDonald had a farm" );
    System.out.println( "E-I-E-I-O" );
    System.out.println( "And on that farm he had a " + animal );
    System.out.println( "E-I-E-I-O" );
    System.out.println( "With a " + noise + "-" + noise + " here") ;
    System.out.println( "And a " + noise + "-" + noise + " there" );
    System.out.println( "Here a " + noise + ", there a " + noise );
    System.out.println( "Everywhere a " + noise + "-" + noise );
    System.out.println( "Old MacDonald had a farm" );
    System.out.println( "E-I-E-I-O" );
  }

  public static void main(String[] args)
  {
    verse( "cow" , "moo" );
  }
}
```

<details>
    <summary>What is the variable <code>animal</code> assigned to when we call the <code>verse()</code> method from the <code>main()</code>method?</summary>

  <p>Answer: <br>
     <p>cow</p>
  </p>

  <p>The first <code>String</code> value that is passed into the <code>verse()</code> method will be copied into the parameter, <code>animal</code>.</p>
  <p>The value of the first <code>String</code> parameter passed in is "cow".</p>
</details>

<details>
    <summary>What is the variable <code>noise</code> assigned to when we call the <code>verse()</code> method from the <code>main()</code>method?</summary>

  <p>Answer: <br>
     <p>moo</p>
  </p>

  <p>The second <code>String</code> value that is passed into the <code>verse()</code> method will be copied into the parameter, <code>noise</code>.</p>
  <p>The value of the second <code>String</code> parameter passed in is "moo".</p>
</details>

<details>
    <summary>What does this program output?</summary>

  <p>Answer: <br>
     <p>Old MacDonald had a farm<br>E-I-E-I-O<br>And on that farm he had a cow<br>E-I-E-I-O<br>With a moo-moo here<br>And a moo-moo there<br>Here a moo, there a moo<br>Everywhere a moo-moo<br>Old MacDonald had a farm<br>E-I-E-I-O</p>
  </p>

  <p>In this program, we call the <code>verse()</code> method from the <code>main()</code> method. This will take in the two parameters and execute all the statements within the <code>verse()</code> method's code block.</p>
  <p>See the link below to step through the code above:</p>
  <a href="https://pythontutor.com/visualize.html#code=public%20class%20SongExample%20%7B%0A%0A%20%20public%20static%20void%20verse%28String%20animal,%20String%20noise%29%0A%20%20%7B%0A%20%20%20%20System.out.println%28%20%22Old%20MacDonald%20had%20a%20farm%22%20%29%3B%0A%20%20%20%20System.out.println%28%20%22E-I-E-I-O%22%20%29%3B%0A%20%20%20%20System.out.println%28%20%22And%20on%20that%20farm%20he%20had%20a%20%22%20%2B%20animal%20%29%3B%0A%20%20%20%20System.out.println%28%20%22E-I-E-I-O%22%20%29%3B%0A%20%20%20%20System.out.println%28%20%22With%20a%20%22%20%2B%20noise%20%2B%20%22-%22%20%2B%20noise%20%2B%20%22%20here%22%29%20%3B%0A%20%20%20%20System.out.println%28%20%22And%20a%20%22%20%2B%20noise%20%2B%20%22-%22%20%2B%20noise%20%2B%20%22%20there%22%20%29%3B%0A%20%20%20%20System.out.println%28%20%22Here%20a%20%22%20%2B%20noise%20%2B%20%22,%20there%20a%20%22%20%2B%20noise%20%29%3B%0A%20%20%20%20System.out.println%28%20%22Everywhere%20a%20%22%20%2B%20noise%20%2B%20%22-%22%20%2B%20noise%20%29%3B%0A%20%20%20%20System.out.println%28%20%22Old%20MacDonald%20had%20a%20farm%22%20%29%3B%0A%20%20%20%20System.out.println%28%20%22E-I-E-I-O%22%20%29%3B%0A%20%20%7D%0A%0A%20%20public%20static%20void%20main%28String%5B%5D%20args%29%0A%20%20%7B%0A%20%20%20%20verse%28%20%22cow%22%20,%20%22moo%22%20%29%3B%0A%20%20%7D%0A%7D&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false">Browser-based Java Visualizer of SongExample</a>
</details>

## Writing Methods

Let's look at our `BikeExample` from the last lesson:

```java
public class BikeExample {

    public static void ride() {
        System.out.println("Whee! Look at me riding my bike!");
    }

    public static void main(String[] args) {
        ride();
    }
}
```

Consider we want to add a new method called `bikeColor` that takes in a `String`
parameter called `color` that describes the color of the bike. The method will
not return anything.

<details>
    <summary>What would the method header look like for this described method?</summary>

  <p>Answer: <br>
     <p><code>public static void bikeColor(String color)</code></p>
  </p>

</details>

<details>
    <summary>Where will we write method?</summary>

  <p>Answer: <br>
     <p>Outside the <code>main()</code> method and outside the <code>ride()</code> method.</p>
  </p>

  <p>This is so we can eventually call the method.</p>
</details>

We want this method to print a message that would look like: "The color of my
bike is red!"

<details>
    <summary>What would the body of this method look like?</summary>

  <p>Answer: <br>
     <p><code>System.out.println("The color of my bike is " + color + "!");</code></p>
  </p>

  <p>This one statement would go within the curly braces of the <code>bikeColor()</code> method.</p>
</details>

<details>
    <summary>How do we call our new method given the bike color is red?</summary>

  <p>Answer: <br>
     <p>We call it within the <code>main()</code> method.</p>
     <p>We'll write <code>bikeColor("red");</code> in the <code>main()</code> method to call the <code>bikeColor()</code> method.</p>
  </p>

  <p>We call a static method by writing out the method name and its parameters where we want to execute the method's block statements.</p>
</details>

Assume we want to first print the `ride()` message before printing the `bikeColor()` message.

<details>
    <summary>What does the final version of the program look like?</summary>

  <p>Answer: <br>
     <img src="https://curriculum-content.s3.amazonaws.com/java-mod-1/methods-with-parameters/bike-example-with-parameters.png">
  </p>

</details>
<details>
    <summary>What is the output when we run this program?</summary>

  <p>Answer: <br>
     <p>Whee! Look at me riding my bike!<br>The color of my bike is red!</p>
  </p>
</details>

## Conclusion

We now know how to read, call, and write methods that return nothing and take in
some parameters. We also better have a better understanding of how parameter
passing works. In the next lesson, we'll learn about reading, calling, and writing
methods with return types.

## Resources

- [Runstone Academy: Method Parameters](https://runestone.academy/ns/books/published/csjava/Unit5-Writing-Methods/topic-5-2-method-parameters.html?mode=browsing)
