# Javascript Objects

Javscript is designed based on an object based paradigm. Javascript views your browser window, and the web page within as objects.

Every time we have accessed a property: myArray.length or called a built in function: Math.random(), we have been interacting with predefined objects using dot notation.

## So whats is an Object data type?

An object is a collection of properties. Properties are sets of key value pairs. If a property’s value is a function, we call it a method.

Javascript Objects are an amazingly descriptive and flexible data type. We can label and store and access a collection of information about an object.

## Object Initialization:

Declaring a variable named `customer` and assigning an object as its value

```js
const customer = {
  name: 'Tony',
  age: 23,
  married: false,
  pets: ['dog', 'cat', 'iguana'],
  siblings: [
    {name: 'Mary', age: 32, married: true},
    {name: 'Billy', age: 16, married: false},
  ],
}
```

Our variable customer contains the keys: `name`, `age`, `married` , `pets`, and `siblings`. Notice the values are a mixture of other data types. Objects can store, strings, numbers, booleans, arrays, other objects, or even arrays of objects. Objects can also store functions, but remember we call those stored functions methods.

## Accessing Object Properties:

We can access individual properties with the property name.

Dot Notation:
`customer.name // 'Tony’`

Bracket Notation:
`customer[age] // 23`

## Accessing a property name inside a variable:

```js
const myProperty = 'married'

const customer = {
  name: 'Tony',
  age: 23,
  married: false,
  pets: ['dog', 'cat', 'iguana'],
  siblings: [
    {name: 'Mary', age: 32, married: true},
    {name: 'Billy', age: 16, married: false},
  ],
}

customer[myProperty] // false
```

## Adding New and Modifying Existing Properties:

Just like we can assign new values to an existing variable, we can assign a new value to an existing property using Dot or Bracket Notation:

`customer.name = 'Anthony’`

Now the result of `console.log(customer)` is:

```js
const customer = {
  name: 'Anthony',
  age: 23,
  married: false,
  pets: ['dog', 'cat', 'iguana'],
  siblings: [
    {name: 'Mary', age: 32, married: true},
    {name: 'Billy', age: 16, married: false},
  ],
}
```

### We can also add properties and sub-properterties to existing objects using Dot or Bracket Notation:

`customer.eyeColor = 'green’`

Now the result of `console.log(customer)` is:

```js
const customer = {
  name: 'Anthony',
  age: 23,
  married: false,
  eyeColor: 'green',
  pets: ['dog', 'cat', 'iguana'],
  siblings: [
    {name: 'Mary', age: 32, married: true},
    {name: 'Billy', age: 16, married: false},
  ],
}
```

#### When a properties value is an Array, we have access to all of Javascript’s Array Methods:

`customer.pets.push('Chicken’)`

Now the result of `console.log(customer)` is:

```js
const customer = {
  name: 'Anthony',
  age: 23,
  married: false,
  eyeColor: 'green',
  pets: ['dog', 'cat', 'iguana', 'chicken'],
  siblings: [
    {name: 'Mary', age: 32, married: true},
    {name: 'Billy', age: 16, married: false},
  ],
}
```

#### How might we add the property ‘pets’ to ‘Mary’ with the values of ‘snail’ and ‘spider’?

`customer.siblings[0].pets = ['snail', 'spider’]`

Now the result of `console.log(customer)` is:

```js
const customer = {
  name: 'Anthony',
  age: 23,
  married: false,
  eyeColor: 'green',
  pets: ['dog', 'cat', 'iguana', 'chicken'],
  siblings: [
    {name: 'Mary', age: 32, married: true, pets: ['snail', 'spider']},
    {name: 'Billy', age: 16, married: false},
  ],
}
```

## JSON: Javascript Object Notation

Cbjects in JS are such a great way to store large, complicated, or deeply nested data sets. When properly formatted with a plugin like PrettifyJSON or Prettier, they are also easy read with the naked eye. This is one of the reasons, many API’s return results in JSON or Javascript Object Notation. It’s syntactically similar, and can be used by ANY programming language.

### Our Javascript Object:

```js
const customer = {
  name: 'Anthony',
  age: 23,
  married: false,
  eyeColor: 'green',
  pets: ['dog', 'cat', 'iguana', 'chicken'],
  siblings: [
    {name: 'Mary', age: 32, married: true, pets: ['snail', 'spider']},
    {name: 'Billy', age: 16, married: false},
  ],
}
```

### That same data as JSON:

```json
{
  "name": "Anthony",
  "age": 23,
  "married": false,
  "eyeColor": "green",
  "pets": ["dog", "cat", "iguana", "chicken"],
  "siblings": [
    {"name": "Mary", "age": 32, "married": true, "pets": ["snail", "spider"]},
    {"name": "Billy", "age": 16, "married": false}
  ]
}
```

## JSON from API Endpoints:

Let’s take a look at some free API JSON results. We can easily view these in our browser. Make sure you are using CHROME and be sure to install a free extension to make viewing and browsing JSON more user friendly. I am using [JSON Viewer](https://chromewebstore.google.com/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh).

[Random Inspiration Quote](https://api.quotable.io/quotes/random)

[Fake User Data](https://randomuser.me/api/)

[Rick and Morty Character Data - change character number](https://rickandmortyapi.com/api/character/1)

## Using the JS Fetch API:

We can save JSON data in a static `.json` file, or load some hardcoded JS objects from a `.js` file from within our project folder at any time. This is a great option when you are building out the front end UI based on mock data, or great in a pinch when you do not have internet access.

But what if we wan’t to query an API endpoint when our page loads? We need to request and store the data returned from an API. Let’s take a look at the native [Fetch API and how to use it](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

## Async and Await Keywords:

Javascript wants to execute our code, line by line, as quickly as it can read it.

This is why we need to wrap certain variable assignments within the event listener `DOMContentLoaded`. Without it, JS will wind up with a bunch of `null` or `undefined` variables due to the fact that the HTML may not have fully loaded by the time JS attempts to ‘grab’ it.

API results are usually pretty quick, but they are not INSTANT. Even if it takes a few milliseconds to complete, JS will have moved on and left our named result variables as an unresolved `Promise`.

We need to tell Javascript to chill out, and wait for the API to return a result (even if that result is an error) before continuing along with the following lines of code.

We do this with the `await` keyword. Take a look at the code snippet and notes below:

```js
// we need to flag this function as asynchronous, if we are flagging anything with await within
async function logApiResults() {
  // the await flag = Dear JS, please wait for a response to be resolved/returned
  // before executing the next lines of code
  const response = await fetch('ENTER_FULL_API_ENDPOINT_HERE')
  // if we didn’t await response, response would be null/undefined here and there would be no JSON to parse
  const result = await response.json()
  // here we are simply logging the result, but we could call out any of the properties
  console.log(result)
}
```

The `await` keyword always precedes the code that ‘might take a few milliseconds’ to complete.

Whenever we use `await` within a function, we need to also flag that function with the `async` keyword.

Think of both of these keywords as saying:

“Dear JS, I know you’re going as fast as you can, but can you please wait for this next line to resolve before moving on?”

## JSON.parse() and JSON.stringify()

While we are writing our JavaScript code, it is much easier to work with JavaScript Objects.

When communicating with an API, we need to send/receive JSON because JSON works with other programming languages. The API we are using, may not even be written in JS!

Luckily, there are a few methods we can use to seamlessly convert between the 2.

### .json()

`.json()`: The name is a little confusing. Event though its called `json()` it takes the JSON data from the response, and converts it into a JS Object.

`myData.json()` - converts `myData` from JSON to a JS Object.

### JSON.stringify(data)

`JSON.stringify(objectToConvert)` - converts a JS Object into JSON aka sneaks in all of those string quotes on the property names. Hence, `.stringify()`.

_Note: the object you wish to convert to JSON is passed to JSON.stringify() method as a parameter._

### JSON.parse(data)

`JSON.parse(jsonDataToConvert)` - converts the JSON passed in as a parameter into a JS object.

### In Class Exercises

Let’s take a look at some quick examples in VSCode. Once we have our API results stored as global variables we can format and display some information to the user with Template Strings.

1- Using the random inspirational quote API endpoint. Display an inspirational quote, and the authors name to the user. (google font usage encouraged)

2- Display a random users information. Be sure to display the users:

- First Name, Last Name
- Username
- Mailing Address
- Any other information you’d like to display from the returned JSON

3- Make a helper function to generate a [random INTEGER between 1-100](https://github.com/Kadee80/WebDevSpring24/blob/main/Week08/Week8_1/Math/In_Class_Exercise/B/index.html#L83). Use that random integer in the API endpoint to grab a random Rick and Morty character. Use the result to generate a message with the following info in a sentence.

- Name
- Status
- Origin
- Location
