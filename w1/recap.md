# Week 1 Recap

<h3 id="contents">Contents</h3>
<ol>
    <li>
        <a href="#intro">JavaScript - First steps</a>
        <ol>
         <li>
            <a href="#getting-started">Getting started</a>
         </li>
         <li>
            <a href="#what-is-js">What is JavaScript? High-level vs. low-level, dynamic typing etc.</a>
         </li>
         <li>
            <a href ="#js-syntax"> Basic Syntax <a>
         </li>
         <li>
            <a href="#objects"> Objects </a>
         </li>
         <li>
            <a href="#loops"> Loops in JS </a>
         </li>
        </ol>
    </li>
    <li>
        <a href="#intro-to-git"> Introduction to Git </a>
        <ol> 
        <li> 
            <a href="#what-is-git"> What is git? </a>
        </li>
        <li>
            <a href="#basic-commands"> Basic git commands </a>
        </li>
        </ol>
    </li>
</ol>

<h2 id="intro"> JavaScript - First steps </h2>

```javascript
/**
 * Function to say hello!
 * @param { tutor, student } the tutor, and an array of students
 * @return {} nothing
 */
function helloClass(tutor, students) {
    for (student of students) {
        tutor.waveTo(student);
    }
    console.log("Hello!!");
}
```

**Welcome to JavaScript!**<br><br>
If this is your first time learning JS, not to worry, we'll be covering the language in detail and (hopefully) in a way that isn't too confusing ...

**This week's recap will assume that**:

-   You have done programming before, preferably in a low-level language such as C (those of you from UNSW will have taken COMP1511 and potentially COMP1521 / COMP2521 so no worries on that front)

<br>

<h3 id="getting-started"> Getting started </h3>

To run local JavaScript programs, you will need to have **Node.js** installed.
But what is 'Node.js'?

To put it simply (or not), **Node.js** is what we call a **_runtime environment_**. Essentially, it's what allows JavaScript to run outside of your browser (we will elaborate on this much later so don't worry about it :))

Feel free to set up however you like (using the tutorials on WebCMS), however I would definitely suggest that you work on everything **locally**. It is a bit more complicated at first but trust me it will save a lot of headache in the long run.

<br>

![Node.js Logo](static/node-logo.png)

<br>

<h3 id="what-is-js"> What is JavaScript? </h3>

If this is your first time dealing with JavaScript, then don't worry! We'll cover everything there is to know about the language, what it is capable of, and include some real-world examples of how we might use it in our own personal projects!

So, **what is JavaScript**?

Although its name implies differently, JavaScript is not at all similar to **Java**. This will become painfully clear when you have to take COMP2511.

JavaScript is a **high-level**, **dynamically typed**, **Just-in-time (JIT) compiled** programming language. You might have heard of it alongside **HTML and CSS**, as one of the core programming languages to learn Web-development. In fact, according to [Wikipedia](https://en.wikipedia.org/wiki/JavaScript), it is used in 98.9% of websites!

But what do those terms actually mean?

<br>

-   **High-level**: A language is considered 'high-level' if it contains a high amount of **abstraction** from what the computer does behind the scenes. This generally means that the code tends to be more readable and resembles **Human** instructions a lot more. Things like memory management are what you would see in a low-level language. **C** is an example of a **low-level** language.

    -   **Advantages**: High-level programming languages are often a lot easier to write with, read and can be used to easily create extremely complex programs.
    -   **Disadvantages**: Because a lot of the stuff you write is not micro-managed, high-level languages often lack execution speed.

-   The two code snippets below do the same thing:

```C
// Sorting an Array in C - LOW LEVEL
// src: https://www.geeksforgeeks.org/bubble-sort/

void swap(int* xp, int* yp) {
    int temp = *xp;
    *xp = *yp;
    *yp = temp;
}

// An optimized version of the bubble sort algorithm
void sort(int arr[], int n) {
    int i, j;
    bool swapped;
    for (i = 0; i < n - 1; i++) {
        swapped = false;
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(&arr[j], &arr[j + 1]);
                swapped = true;
            }
        }
        if (!swapped)
            break;
    }
}

int main(void) {
    int arr[] = { 64, 34, 25, 12, 22, 11, 90 };
    int n = sizeof(arr) / sizeof(arr[0]);
    sort(arr, n);
    return 0;
}
```

```javascript
// Sorting an array in JS - HIGH LEVEL
const arr = [64, 34, 25, 12, 22, 11, 90];
arr.sort((a, b) => a - b);
```

(Advanced) As it turns out, these two are actually _not_ the same. For those familiar with Big O notation (in 2521), JS sorts with an **O(nlogn)** algorithm whereas the algorithm in the C snippet (bubblesort) is **O(n^2)**.

Moving on...

<br>

-   **Dynamically typed**: As opposed to **statically-typed**, dynamically typed languages don't require us to specify types when we write programs. The program instead **infers** the type **at runtime** (ie. when the program actually executes)

    -   **Advantages**: Makes it less tedious to micro-manage and ensure type-safety for every variable in the program.
    -   **Disadvantages**: This does make the program more prone to bugs, however.

-   Notice the subtle changes in the two code snippets below:

```C
// An example function to take in two numbers to multiply them in C
int multiply(int a, int b) {
    return a * b;
}

int main(void) {
    int a = 5;
    int b = 4;
    char char1 = 'h';
    long superInt;

    // etc.

    int result1 = multiply(a, b); // No error, types check out!

    return 0;
}
```

```javascript
// The same example but in JS
function multiply(a, b) {
    return a * b;
}

const a = 5; // infers it is a number at runtime
const b = 4; // infers it is a number at runtime
const char1 = 'h' // infers it is a char at runtime
const superInt;

const result1 = multiply(a, b); // should be ok!
const result2 = multiply(a, char1) // what would happen here!?
```

<br>

<h3 id="js-syntax"> Basic Syntax </h3>

As you might have noticed in the above examples, JavaScript programs do not require a `main` function. This is because as opposed to C, JavaScript programs are **interpreted line by line**.

Let's revisit the example in this week's tutorial:

```javascript
// welcome.js

//declaring variables & printing
const message = "Welcome to COMP1531!";
console.log(message);

// declaring arrays
const number_array = [1, 9, 2, 8, 3, 7, 4, 6, 5, 0];

// for loop
for (let i = 0; i < number_array.length; i++) {
    if (number_array[i] % 2 === 0) {
        console.log(`[${i}] EVEN: ${number_array[i]}\n`);
    } else {
        console.log(`[${i}] ODD: ${number_array[i]}\n`);
    }
}

// fctn declaration
function multiply(a, b) {
    return a * b;
}

console.log(multiply(3, 4)); // prints 12
```

Here's a summary of the important aspects of JS syntax:

-   **Variable declaration**: There are two (excluding `var`) keywords for declaring variables in JS. These are `const` and `let`. Any variable declared with these keywords can be of **any** type; numbers, strings, objects, etc. - `const` is for declaring constants, ie. when you declare a variable as a `const` you **cannot** reassign its value. eg:

    ```javascript
    const number1 = 5;
    number1 = 7; //Throws an error - cannot reassign const!
    ```

    -   `let` is for declaring non-constants:

    ```javascript
    let number1 = 5;
    number1 = 9; // OK
    number1 = "this is a string?"; // OK! JS is dynamically typed!
    ```

    -   Something important which may be confusing later on is that although you cannot reassign `const` variables, **you can mutate them** ie. change their internal properties. An example is with arrays:

    ```javascript
    const arr = [1, 2, 3, 4, 5];
    arr = [4, 5, 6, 7, 8, 9]; // not ok, reassigning a const!

    arr.push(6); // pushes the number 6 onto the end of the array
    console.log(arr); // prints [1,2,3,4,5,6]
    ```

<br>

-   **Printing**: Printing to the terminal in JS is extremely simple, simply call `console.log()`. Notice how in the example above, we do not need to specify the **type** of what we're printing. JS infers this itself and prints it accordingly. Very useful!
    -   Notice how we print values inside the for loop. The stuff inside the `console.log()`'s are called **string literals**. These are special types of strings that allow us to print values as a part of the string, which are inferred from variables.
    -   String literals are written using ' ``' characters rather than ' "" ', and if we want to add a value inside, we wrap the variable with`${}`.

<br>

-   **Operations**: Operation syntax is pretty much the same as C; adding, multiplying, dividing, subtracting all use the same symbols. We also have access to the new `**` operator which denotes 'to the power of'.

    -   **Comparisons**: Notice how in the example we use `===` instead of `==`. This is extremely important! In short, `===` compares the two values **and** their types. This is the comparison you should use basically all the time. `==` only checks for values but does **not** check type similarity.

        Here's an example:

        ```javascript
        // Fun fact - you can assign variables to be the true/false result of expressions!
        const result1 = 1 === 1; // result1 = true
        const result2 = 1 === "1"; // result2 = false
        const result3 = 1 == "1"; // result3 = true
        ```

        This example makes it pretty clear that using `==` can lead to a lot of unwanted bugs!

<br>

-   **Arrays**: You will be doing a lot of work with arrays, so best to be familiar with some basics ASAP! They're pretty similar to arrays in C, with a lot of bonus quality of life features as well.

    -   **'length'** attribute: In C, we must keep track of array sizes due to memory constraints. However, in JS, each array stores its length as part of the variable! We call this a property or an attribute.

        As seen above, we access these attributes by using a `.`. To get the length of an array, we can use `arr.length`, which gives us a number. Hence, no need for array size constants!

    -   **Indexing**: Indexing into an array is the same as in C.

<br>

-   **Functions**: Much like in C, we can declare functions in JavaScript as follows:

    ```javascript
    // example
    function doSomething(input1, input2) {
        return input1 + input2;
    }
    ```

    -   Although JS is interpreted line by line, and is executed line by line, the compiler does not execute anything within a function block **unless** the function is called.

    ```javascript
    // Function declaration (nothing happens)
    function printHelloWorld() {
        console.log("Hello world!");
    }

    printHelloWorld(); // program prints "Hello world!"
    ```

    -   Note: we do not specify the type of the return value, nor do we specify the types of the inputs. These are automatically inferred at runtime!

<br>

<h3 id="objects"> Objects in JS </h3>

In JavaScript (and many other high-level programming languages) we have access to create and manipulate a type of variable called an _Object_. It looks something like this:

```javascript
const myObject = {
    property1: 1, // a property can be a number
    property2: "string", // or a string, or anything really
    property3: [
        {
            id: 1,
            name: "bob
        },
        {
            id: 2,
            name: "steve"
        }
    ] // it can even be an array, which might store more objects!
}
```

Objects are extremely versatile, and we can structure them to store information in many ways. Say for example, we wanted to store information on a person, we can represent that person as an object:

```javascript
const person = {
    zId: "z5421324",
    nameFirst: "Jun",
    nameLast: "McPhee",
    age: 20,
};
```

To use the values, or _properties_ of objects, we can deference them using the `.`. For example:

```javascript
const zId = person.zId;
const firstName = person.nameFirst

if (person.age > 20) {
    ...
}

// and so on....
```

<br>

<h3 id="loops"> Loops in JS </h3>

Loops in JS are a little different to those in C. Although C syntax works perfectly fine with JavaScript, at times it can be a bit clunky and annoying to read.

To solve this, JS has two types of **for loops** which we can use to make things a lot easier:

-   **'For-of'**: For-of loops are probably the loops you will use the most. By using the keyword `of` when referring to a `thing of array`, JS automatically loops through every single element in an array.
    ```javascript
    const arr = [1, 2, 3, 4, 5, 6];
    for (const number of arr) {
        console.log(number);
    }
    // prints 1,2,3,4,5,6 on each new line
    ```
    -   This is of course the same as:
    ```javascript
    const arr = [1, 2, 3, 4, 5, 6];
    for (const i = 0; i < arr.length; i += 1) {
        console.log(arr[i]);
    }
    ```
-   **'For-in'**: For-in loops are a little different. The variable that you specify `in` (eg. `variable in array`) actually wont have to do with the elements within the array, but instead will evaluate to the respective **index**.
    ```javascript
    const arr = [1, 4, 56, 3, 2, 34, 6, 7, 3];
    for (const variable in arr) {
        console.log(variable);
    }
    // prints 0,1,2,3,4,5,6 ...
    ```
    -   Take care however, as the type of `variable` in the above code snippet is actually a `string`!!

<br>

<h2 id="intro-to-git"> Introduction to Git </h2>

The second part of this week is our introduction to Git! This will probably be the first time you have used git and so it might seem a little daunting at first, but don't worry, you'll get used to it fairly quickly!

![Git logo](static/git-logo.png)

<br>

<h3 id="what-is-git"> What is git? </h3>

**Git** is what we call a **version-control system**. It enables us to collaborate with other programmers to work on projects together.

The power behind git is that your codebase is stored **online**, and subsequent versions can be accessed at whatever time a user wants.

The base folder where your code is contained is referred to as a **repository**. There are several online service providers which center around storing repositories, such as **GitHub** and **GitLab**.

<br>

<h3 id="basic-commands"> Basic Git Commands </h3>

Here are some basic git commands that you will be using a lot throughout your project work!

-   `git clone (...)`: The command to 'clone' or copy a remote repository (the `(...)` bit is where a specified URL would go) into your local system.
-   `git status`: Will show the status of the files in the repository you have cloned. If git detects differences between a file locally, and the same file remotely, it will show up as red. This indicates we need to 'stage' the changes to push them to our remote repository.
-   `git add (filename)`: This will add the specified file / directories into the git staging area. This essentially tells git that you want to push the changes on this file to the remote repository.
-   `git commit -m "(message)"`: This is the next stage of publishing our changes. When we are happy with a file we have added into the staging area, we 'commit' all files and tell git that we are set on these changes and are about to publish them. It is important we add a meaningful message which tells other collaborators what exactly has been changed in this commit.
-   `git push`: Pushes the changes to the remote repository. Any updates that were included in the final commit are reflected remotely, and the repository updates.
-   `git pull`: To update your local repository (your cloned repository) with any changes that might have been made to the remote one. Essentially updating your local repository with what's latest on the cloud. NOTE: THIS WILL NOT OVERRIDE YOUR CURRENT FILE CHANGES!
