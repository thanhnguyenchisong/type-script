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
# SOME THING ELSE
### Const and let

### Arrow function

### Default function params.
```ts
  const add = (a: number, b: number = 1) => a + b; //default b value = 1
  add(5)// => result = 6
```
other case
```ts
  const add = (a:number = 1, b:number) => a + b; //default a value =  1
  add(5); // => error because if we send a agument only -> get a = 5
```
### The Spread Operator
```ts
 //push array
 const arr = ['Sports', 'Cooking'];
 const arr1 = ['Hiking'];
 arr1.push(...arr); // attract all value of a arr and push to arr1
 
 //copy a object
const person: {name!:string, age!: number} = {
  name: 'Thanh',
  age: 30
}
const thanh = {...person}; // attract all values of person and assign to thanh variable.
```

### Rest parameter
```ts
const add = (...numbers: number[]) => { //this is rest parameter
  numbers.reduce((curResult, curValue) => {
    return curResult + curValue;
  }, 0);
}

console.log(add(5, 4, 5)); //value is 14;

```
### Array & Object destructuring
```ts
 const hobbies = ['Sports', 'Cooking'];
 //destructure the  hobbies become some variable - with position 0 -> hobby1, 1-> hobby2
 //and remain data -> remainingHobbies
 const [hobby1, hobby2, ...remainingHobbies] = hobbies;
 console.log(hobb1, hobbly2, remainingHobbies); 
 const person: {name!:string, age!: number} = {
  name: 'Thanh',
  age: 30
}
 //destructure person object by key name -> name and map to username, age -> age
 // variable so we have 2 variable username and age
 const {name: useraname, age} = person; 
 console.log(username, age, person);
```
# CLASSES & INTERFACE
## Classes
### 1.What is class ? 
 Class is a blueprints for objects - template to create a object, define how objects look like, properoties and method and class make creation of multiple siminlar objects much esasier, alternative to using object literals.
 Beside class - object is a instance of class. 
### 2. Create a first class
```ts
 class Department {
  // private id: string; //this is old way
  // name: string; //this is old way
  private employees: string[] = []; //make sure a way to access this property by addEmployee method.

  //Shorthand initailization - this constructor creates the property and also create initial value of this class with the same name
  constructor(private readonly id: string, public n: string) { //
    // this.name = n;
  }

  describe() {
    console.log('Department: ' + this.name);
  }

  addEmployee(employee: string) {
    this.employees.push(employee);
  }

  printEmployeeInfomation() {
    console.log(this.employees);
  }
 }

 let department = new Department('Accounting'); //Have to create department by Department with constructor.
 department.describe();

 let departmentCopy = {describe: department.describe};
 departmentCopy.describle(); // value is undefine because we copy the method only so this.name in method is departmentCopy's this so it is undefine.

//correct it
departmentCopy = {name: department.name, describe: department.describe}

 ```
### 3. Inheritance
```ts
 class ITDepartment extends Department { //auto recieved everything from Department
  constructor(id: string, public admins: string[]) {
    super(id, "IT");
  }
 }
 
 const itdepartment = new ITDepartment("223", ["admin"]);
 console.log(itdepartment.describe());
 ```
### 4. Overriding Properties and "protected" modifier
 private is accessable inside of class, but child also would like to use it so we use protected
 ```ts
 //parent class
  .....
   protected employees: string[] = [];
  .....

 //overriding in ITDepartment
 addEmployee(employee: string) {
   if(employee === 'MAX') return;
   this.employees.push(employee);
 }
```
### 5. Getter and setter function
 It is a method to get and set the private property, ecapsulate the properties
```ts
 private report:string;
 get report() {
  return this.report ? this.report : throw new Error('No report here');
 }
 set report(r: string) {
  this.report = r ? r : throw new Error('Invalid report value');
 }
```
### 6. Static Method & Properties
Static properties can't be access directly in constructor be cause it isn't instance property but you can access by ClassName.staticProperty.
```ts
private static instance: ITDepartment = undefined;
private ITDepartment();
private constructor(id: string, public admins: string[]) {
    super(id, "IT");
}
static buildITDepartment() { //singletons pattern and private contructor always stay together
  instance ? instance : new buildITDepartment('ITDepartment', ['admin']);
}

//from outside of ITDepartment class
const itdepartment = ITDepartment.buildITDepartment();
```
### 7. Abstract class
You would like to force override some methods for childent, you can use the abstract, abstract class can't be instantiated
```ts
abstract class Department {
  abstract describe(this: Department): void;
}
```
 all of class extends Department, have to implement describe method.

### 8. Interface
- Just use to describe the structure of a object and make sure all object use this interface must to use this structure
- Don't allow init value and implementation at all in interface
- About my experience - Interface defines behaiviors of a objects and can share many type of objects.
- Can use readonly only interface
-  Extends in 2 interfaces.
- Interface can't be instantiated and are not compliled
```ts
interface Named {
  readonly name?: string; //optional property
}

interface Greetable extends Named { //extends in 2 interface allowed
  great(pharse: string): void;
}

interface Person extends Greetable {
  age: number;
}

class Student implement Person {
  name?: string; //Optional property
  agre: 30;

  constructor(n?: string) { //optional parameter
   if(n) this.name = n;
  }

  greet(phrase: string) {
    console.log("Hello student : "+ phrase);
  }
}
```
1. Interface as a function types
```ts
//type AddFn = (a: number, b: number) => number;
interface AddFn {
  (a: number, n: number): number;
}
```

# Advanced Types
- Intersection types
- Type Guards
- Discriminated Unions
- Type Casting
- Function overload

### 1. Intersection Type
 Allow combine other types.
 ```ts
type Admin = {
  name: string;
  privileges: string[];
}

type Employee = {
  name: string;
  startDate: Date;
}

type ElavatedEmployee = Admin & Employee;
const e1: ElavatedEmployee = {
  name: 'Thanh',
  privileges: 'server',
  startDate: new Date();
}

//example 2
type Combinable = string | number; //union
type Numeric = number | boolean; // union
type Universal = Combinable & Numberic;
```
If you use interface for that code you can use the extends.
### 2. Type Guards
Code pattern where you check for a certain type fore before you try to do something with it at runtime.
```ts
class Car {
  driver() {
    console.log('Driving ...');
  }
}

class Truck {
  driver() {
    console.log('Driving truck ...');
  }

  loadCargo(anmount: number) {
    console.log('Load cargo...' + number);
  }
}

type Vehicle = Car | Trunk;

const v1 = new Car();
const v2 = new Trunk();

function useVehicle(v : Vehicle) {
  v.drive();
  if('loadCargo' in v) { // I really don't like this way to check because can miss the name this is Type Guards
    v.loadCargo(1000);
  }
}

useVehicle(v1); //run without loadCargo
useVehicle(v2); // run with Truch and have loadCargo
```

### 3. Discrimanated Unions
```ts
class Car {
  type = 'Car';
  driver() {
    console.log('Driving ...');
  }
}

class Truck {
  type = 'Truck'
  driver() {
    console.log('Driving truck ...');
  }

  loadCargo(anmount: number) {
    console.log('Load cargo...' + number);
  }
}

type Vehicle = Car | Trunk;

const v1 = new Car();
const v2 = new Trunk();

function useVehicle(v : Vehicle) {
  switch(v.type) { //this is the way to Discrimanated the Unions to get correct class.
    case 'Car': { //Me: don't like to set a fixed source code here humzzzzz. Don't like this way
      v.driver();
    },
    case 'Truck': {
      v.driver();
      v.loadCargo(1000);
    }
  }
}

useVehicle(v1); //run without loadCargo
useVehicle(v2); // run with Truch and have loadCargo
```
### 4. Type Casting
```ts
 const taxi = .... as Car; // cast a taxi object to Car type becasue it is Car type, accessable Car function after this cast.
```
### 5. Index properties
```ts
interface ErrorContainer {
  [prop: string]: string;
}

const errorBag: ErrorContainer {
  email: 'Not a valid email',
  username: 'Must start with capital character !'
}
```
### 6. Function overloads
```ts
 //Overload example, if a and b is number, then return type = number and if a is tring, b is tring then return type = string
 function add(a: number, b:number): number;
 function add(a: string, b:string) : string;
 function add(a: Combination, b: Combination) {
 }
```

### 7. Optional Chaining
```ts
 person?.job?.title; //help us check the variable is available
```
### 8. Nullish Coalescing
```ts
const input = null;
const storeInput = input || 'DEFAULT'; //take Default value because input == null or undefined.
input = '';
storeInput = input ?? 'DEFAULT'; //check not empty not 0, not null. not undefined

```
# Generic
### 1.Built-in Generics & What are Generics
 Express a feature with not specific type object which can be applied in feature =. so we can use it in many places for many target object.
 ```ts
 const names: Array<string> = []; //string[];
 ```
 ### 2. Create generic function
 ```ts
 function merge<T, U>(objA: T, objB: U) {
    return Object.assign(objA, objB);
 }

  const  mergeObj = merge( {name: 'Thanh', hibbies: ['Sports']}, {age: 30}); //=> auto infer the type for generic behind
  console.log(mergeObj.age); //It can be access and log 30 
 ```
### 3. Work with Constraints
From example 2 - we can send a some in parameter -> It is hot our expected input so we have do a constraint.
```ts
 function merge<T extends object , U extends object>(objA: T, objB: U) { //We have this contraint here. It will check and you can't send the input which is not object. 
    return Object.assign(objA, objB);
 }
```
### 4. Aother Generic Function
Idea for generic we don't need to care about input type but sometime we have to some certain function to interact inside of main function, so we should make it as common function and put it in a generic interface to use like ``` T extends GenerticType ```

### 5. "keyof" Constaint
```ts
function extractAndConvert<T extends object, U extends keyof T>(obj: T, key: U) {
  return object[key];
}
```
### 4. Generic class
Same idea with generic function
```ts
class Storage<T> {
 // can use T inside of this class
}
class StoragePrimitives<T extends string | number | boolean> {
 // can use T inside of this class
}
```
### 5. Generic Utility Types
```ts
  const person: Parial<Person> = {}; //that will set all properties in Person become optional
  const names: Readonly<string[]> = ['Max', 'Anna']; //It become readonly array and can't push more value to.
```
### Generic Types vs Union Types
```ts
 class StoragePrimitives<T extends string | number | boolean> { //can use union type hgere
 // can use T inside of this class
}
```

# DECORATORS

### 1. Class Decorator
```ts
 function Logger(constructor: Function) {
  console.log('Logging...');
  console.log(constructor);
 }

 @Logger
 class Person {
  name = 'Thanh';
  constructor() {
    console.log('Creating person object ...');
  }
 }
```
### 2. Decorator Factories.

 ```ts
 function Logger(msg: string) {
  return function (constructor: Function) {
    console.log(msg);
    console.log(constructor);
  }
 }

 @Logger('Person')
 class Person {
  name = 'Thanh';
  constructor() {
    console.log('Creating person object ...');
  }
 }
```
### 3. More usefull Decorators
It is Decorator in Angular - you can see it to understand more.
```ts
  function Logger(msg: string) {
    return function (constructor: Function) {
      console.log(msg);
      console.log(constructor);
    }
 }

 function WithTemplate(template: string, hookId: string) {
  return function(contructor: function) {
    const hookEl = document.getElementById(hookId);
    const p =  new constructor();
    if(!hookEl) {
      hookEl.innerHTML = template;
      hookEl.querySelector('h1')!.textContent = p.name
    }
  }
 }
 @Logger() //can have multiple decorator and it run from top to bottom
 @WithTemplate('<h1>My personal template</h1>', 'app')
 class Person {
  max = 'Thanh';
  constructor() {
    console.log('Creating person object...');
  }
 }
```
### 4. Property Decorators. Accessor & Parameter
```ts
function Log(target: any, propertyName: String | Symbol) {
  console.log('Property decorator');
  console.log(target, propertyName);
}

function Log2(target: any, name: string,  desciptor: PropertyDescriptor) {
  console.log('Accessor decorator');
  console.log(target);
  console.log(name);
  console.log(descriptor);
}

function Log3(target: any, name: string | Symbol, descriptor: PropertyDescriptor) {

}

function Log4(targer: any, nameMethod: string | Symbol, positionOfParameter: number) {
  console.log('Paramerter decorator');
  console.log(target);
  console.log(nameMethod);
  console.log(positionOfParameter);
}

class Product {
  @Log
  title: string;
  private _price: number;

  @Log2
  set price(@Log4 val: number) {
    if(val > 0) {
      thí._price = val;
    } else {
      throw new Error('Invalid price');
    }
  }
}
```
### 5. When do Decorators Execute ??
Deeoratoes will be call when you work with class, method, property

### 6. Returning (changing) a Class in a Class Decorators

### 7. Autobinding
```ts
 function Autobind(_: any, _2: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  const adjDescriptor: PropertyDescriptor = {
    configurable: true,
    enumerable: false,
    get() {
      const boundFn = originalMethod.bind(this); //bind the this from class to listener
      return boundFn;
    }
  };
  return adjDescriptor;
 }

class Printer {
  message = 'This works!';

  @Autobind
  showMessage() {
    console.log(this.message);
  }
}

const p = new Printer();
p.showMessage(); //this will disaply mssage = 'This works!'

const button = document.querrySelector('button');
button.addEventListener('click', p.showMessage); //if we don't have Autobind in showMessage method
// then then p.showMessage will recive the this from button so value = undefine but after my @Autobind it works with message = 'It is works'

```
### 7. Validation with Decorators
```ts
function Required() {

}

function PositiveNumber() {

}

class Course {
  @Required
  title: string;

  @PositiveNumber
  price: number;

  constructor(t: string, p: number) {
    this.title = t;
    this.price = p;
  }
}

