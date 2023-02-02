# TYPE SCRIPT
 1. What is TypeScript
    Java script superset. Building up on java script, add new features + advantages to JavaScript an Browser can't execute it => so compiler will complite type script to java script and browser will work with Java script.
 2. Why is TypeScript?
    Mitigation Strategies - add if check ti add function validate & sanitize user input -> help develop write the better code
    **convert a string to number in javascript by add + to string - example +'5' -> 5**
    ***minimal thing*** type script check syntax type in complite time

## Install
 >> npm install -g typescript
 
 check by use **tsc** got get current type script information

## Overview
TypeScript adds 
 - Types
 - Non-Javascript Features like Interface or Generic
 - Next-gen Java Script features(complited down for older browers)
 - Meta-Programing Features like Decorators
 - Rich Configuration Options
 - Modern tooling that helps even in non-TypeScript Projects.

## Core Syntax & Features of type script
 #### Core types.
  - number  Eg: 1, 5.3, -10 - all numbers
  - string  Eg: 'hi', "hi", `hi` - all text values
  - boolean Eg: true, false
 #### Best pactice
   ```ts 
      let number1:number;
      let number2:number = 5;
   ```
   if we write like that there are no reassign with incorrect type to variable
   or you can without type in decleration by use const because can not reassign or change the value of a const variable.
   ```ts 
   const number = 5 
   ```
   
 #### Object type
   ```ts
    let person: object = {};
    //or
    let preson: {name:string} = {name: 'Thanh'};
    //or
    const person: {name: 'Thanh'};
   ``` 
  ***We can have Nested Objects & Types***
 #### Array types
   ```ts
    let hobbies: string[];
    //or
    let hobbies: string[] = ['Sports', 'Cooking'];
    //or
    const hobbies: ['Sports', 'Cooking'];
   ```
 #### Tuples
    The lengh was be defined and deatail type inside of array - we call it is tuples.
   ```ts
    let role: [number, string]; 
    //or
    let role: [number, string] = [1, 'admin'];
    role[0] = 'Thanh' //error - position is requited number
    role[1] = 1 //error - position is requited string
    rolde.push('Thai') //replace the exsited string value
  ```
 #### Enums
   ```ts
    enum Role {ADMIN, READ_ONLY, AUTHOR}; //default value equals with name
    //or
    enum Role {ADMIN=0, READ_ONLY=1, AUTHOR=2}; //can assign value 
   ```
 #### any type
   **same as javascript provided so we need to avoid it because it quited flexible so can lead to error in running time**
   ```ts
    let a:any;
   ```
 #### Union Types
   Declare multiple type of value. It can help our function accepts 2 different variable
   ```ts
    function combine(input1: number|string, input2: number|string) { //Union type
        return (typeof input1 === 'number' && typeof input2 ==='number')  ? input1 + input2 : input1.toString + input2.toString;
    }
   ``` 
 #### Literal Types
   Declare direct one or more than one specific value to a variable and it become posible value and can't be assigned by value which out of decleration values.
   ```ts 
    let value: 'text-1' | 'text-2';
   ```
 #### Type aliases


## Function return type & "void"
 ```ts
  function add(n1:number, n2:number) : number { return n1 + n2;}
  function print() { console.log("Thanh"); }
 ```
 ### function as type
 ``` ts 
 function add(n1:number, n2:number) : number { return n1 + n2;}
 let combine: Function = add; //now we can call combine as function
 combine(1, 2);
 ```
 **Recommend**: You can declare the function type by specific kind of function with inputs and return type. 
 ```ts
 const combine: (n1: number, n2: number) => number;
 ```
 ### Function type and callback
 ```ts
  function addAndHandle(n1: number, n2: number, callback: (n:number) => number) => void {
      let value = n1 + n2
      callback(value);
  }
 ```
  With the void return type - It means doesn't force return something if they don't want
 ### unknown type
  ```ts
   let value: unknown;
   value = 'Thanh';
   let userName: string;
   userName = value; //error because compiler doesn't know what type in value so we
                     // have to check typeof value is string before assign value to userName
   ```
   unknow type can be assigned all value, same any but it's better than any type because It was supported checking from compiler 
### never type
  Never type is never function return anything
  E.g:
  ```ts
   function generateError(messages:string, code:number): never {
    throw {message: messages, errorCode: code}; //this is never type
   }
  
  ```

# Type Script Compiler (and it's configuration)
 1. TS will be complite to js file. We can do it by manually but when code with multiple files should have a way to complite it by automation, never be rerun the command tsc file.ts by:
 ```
  tsc file.ts -w
 ```
 2. How to do it for multiple files.
  ```
    tsc --init
  ```
  After run this command it will crate type script project so all of the folder are using type script and we have tsconfig.json file which config our target
 3. Include & Excluding files.
  Go the last of tsconfig.json and add
  ```json
    {
      //default content
    },
    "exclude": [
      "node_modules",
      "*.env"
    ],
    "files": [ //optional and use in some special case default it in our ts project, it applied.
      "app.ts"
    ]

  ```
 4. Set complilation target
  There are many option in "compilerOptions" depends on you strategy - You can active or inactive it.
  E.g:
  ```json
  {
    "compilerOptions": {
      "target": "es6", //use es6 to complite source ts to es6 js
      ...
    }
  ```
  5. Core libs
   Because we set in **4. Set complilation target** so the ts auto import the default library from javascript es6
   but we also can config specific default libs by this option in tsconfig.json file
   ```json
    "lib": [
      "dom",
      "es6",
      "dom.interable",
      "scripthost"
    ]
   ```
   6. Some more configuration & Compilation Options.
    We can follow the comment in tsconfig.js end enable anything which you want.
   7. Working with **Source Map**
    Help us in debuging and development so we should ennable ``` "sourceMap" :true ``` 
   8. rootDir and outDir
    The default will complite to jso file in same folder with ts file, it's not good
    so the config should be ``` "ourDir:"./dist", rootDir": "./src" ```
    and also should remove the comment when complite to js by ``` "removeComments" : true ```
   9. Stop emitting files on compilation errors.
    Doesn't complite the file which have compilation errors ``` "noEmitOnError": true ```
   10. Strict
    It is check some the condition if we open strict parent all strict options in config will enable.

### Debug with Visual Studio code
.....
###

