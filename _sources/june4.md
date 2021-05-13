June 4 ~ JavaScript
============================



## JavaScript Syntax

Javascript is a scripting language originally designed to facilitate interactions between the user and a web page. It has since grown into a full client- and server-side scripting language, with web frameworks built entirely in Javascript like [NodeJS](https://nodejs.org/en/) (including the framework for this application!).

The [Mozilla Javascript tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction) does a nice job of introducing Javascript and the kinds of things it can do, but there's a lot!

---

## There's a JavaScript terminal in your browser 

Right-click > inspect element > console 

<img src="https://developers.google.com/web/updates/images/2015-05-19-devtools-quickly-monitor-events-from-the-console-panel/monitor-events.gif">

---

## [Variables](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#Declarations)


- `let` can be reassigned.
    - `let fish = 'trout';`

- `const` is constant and cannot be redefined or updated. 
    - `const fish = 'trout';`

- you can also just type `fish = trout;`, but it's best practice to use `let` or `const`.  You may also see `var` in older code (pre-2015). It's  similar to `let`. 

---

To see the current value of your variable just type its name or type
`console.log(x)`. It's similar to `print(x)` in Python. You'll see the results printed in the browser's console tab. 

JavaScript is dynamically typed. For example, you can add numbers and characters.

```javascript
let fish = 'trout';
let count = 200;
console.log(fish + " " + count);
``` 

---

## [Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) 

```javascript

let fishes = [];
fishes.push('trout')

fishes[0]  // access values by index
```

---

## [Dictionaries](https://pietschsoft.com/post/2015/09/05/javascript-basics-how-to-create-a-dictionary-with-keyvalue-pairs)

```javascript
var dict = {};
dict["one"] = 1;

var one = dict["one"];
```

---


## [Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

```javascript
function HowManyFish() { 
    let fishes = ['trout','bass','carp','halibut']
    return fishes.length
};

```
or better

```javascript
let fishes = ['trout','bass','carp','halibut'];
function HowManyFish(fishes) { 
    return fishes.length;
};

add_fishes(fishes); // pass the array to the function
```
---

## [The DOM (document object model)](https://developer.mozilla.org/en-US/docs/Web/API/Document)

- `document.documentURI;` // get current URI value
- `document.getElementById('my_img').src = new value;`
- `document.getElementByClassName('fish');`
- `document.getElementsByName('fish');`
- Note that getElement returns the first result, getElements returns an array of results 

__jQuery selectors__ 

- `$(.class)` similar to `document.getElementByClassName('class');`
- `$(#id)` similar to `document.getElementByID('class');`


---

## Working with selected elements 

A selected element is an object with attributes 

- `elem.value` 
- `elem.innerHTML`
- `elem.innerText`
- `elem.attribute`

---

## This

`<button onclick="open(this)">Open</button>`

```javascript
function open(e){
    let elementValue = e.innerText;
    console.log(elementValue)
}
```
[give it a try](https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_button_test)


---

## Making changes to the DOM 

Once you have selected an element in the DOM, you can read values and set values.  This can be used to change the page without having to refresh the page or make a call to the server. 

For example:  

let's make changes to https://alwaysjudgeabookbyitscover.com/

in the console
```javascript
let element = document.getElementsByTagName("h1"); 
element[0].innerText = "The sun is a mass of incandescent gas a gigantic nuclear furnace.  Where hydrogen is build into helium at a temperature of millions of degrees." 
```

---

## [Loops](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)


```javascript
let fishes = ['trout','bass','carp','halibut'];
let i;
for (i = 0; i < fishes.length; i++) {
  console.log('I like: ' +fishes[i]);
}
```

[give it a try](https://www.w3schools.com/js/tryit.asp?filename=tryjs_loop_for)

---

## [While](https://www.w3schools.com/js/js_loop_while.asp)

```javascript
let i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 5);
```

---

## JavaScript libraries 

- JavaScript code can be imported from a file `<script src="displaydate.js" type="text/javascript"></script>`  
- Or a CDN or external source `<script src="https://cdn.jsdelivr.net/npm/p5@1.1.9/lib/p5.js"></script>`


## Robot Chicken 
The following is a creative coding exercise to help you become familiar with the [p5.js](https://p5js.org/) library.

- [P5 reference](https://p5js.org/reference/)
- Using the [p5.js editor](https://editor.p5js.org/)
- [Slides](https://aatishb.com/stc209/slides.html)
- [give it a try](https://editor.p5js.org/bulbil/sketches/YkzH6niu5)
- [Go game](https://editor.p5js.org/ajanco@haverford.edu/sketches/wgMel_OQ)
- [Robot Chicken exercise](https://github.com/Princeton-CDH/playingwithdata/raw/master/p5%20playing%20with%20data%20workshop%20handout.pdf)
- [Simple animation](https://editor.p5js.org/slcruz/sketches/b2uP4YSNu)
- [Plotting data](https://editor.p5js.org/slcruz/sketches/005jy4zME)
- [Stripes visualization](https://editor.p5js.org/slcruz/sketches/mCzhpwQ_7)

This section is based on the [P5.js workshop](https://github.com/Princeton-CDH/playingwithdata) at Princeton's Center for Digital Humanities. Many thanks to the Princeton CDH for sharing these materials and for organizing a remarkable workshop!