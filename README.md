# unwashed-words

A filter for toxic-words in English, Spanish, French, and Arabic 

## Installation

    npm i unwashed-words --save

## Usage

```js
var Filter = require('unwashed-words'),
    filter = new Filter();

console.log(filter.clean("Don't be an ash0le")); //Don't be an a*****
```

### Placeholder Overrides

```js
var Filter = require('unwashed-words');
var customFilter = new Filter({ placeHolder: 'x'});

customFilter.clean("Don't be an ash0le"); //Don't be an axxxxx
```

### Add words to the blacklist

```js
var filter = new Filter(); 

filter.addWords('some', 'bad', 'word');

filter.clean("some bad word!") //s*** b** w***!

//or use an array using the spread operator

var newBadWords = ['some', 'bad', 'word'];

filter.addWords(...newBadWords);

filter.clean("some bad word!") //s*** b** w***!

//or

var filter = new Filter({ list: ['some', 'bad', 'word'] }); 

filter.clean("some bad word!") //s*** b** w***!
```

### Instantiate with an empty list

```js
var filter = new Filter({ emptyList: true }); 
filter.clean('hell this wont clean anything'); //hell this wont clean anything
```

### Remove words from the blacklist

```js
let filter = new Filter(); 

filter.removeWords('hells', 'sadist');

filter.clean("some hells word!"); //some hells word!

//or use an array using the spread operator

let removeWords = ['hells', 'sadist'];

filter.removeWords(...removeWords);

filter.clean("some sadist hells word!"); //some sadist hells word!
```


#### constructor

Filter constructor.

**Parameters**

-   `options` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Filter instance options (optional, default `{}`)
    -   `options.emptyList` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Instantiate filter with no blacklist
    -   `options.list` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** Instantiate filter with custom list
    -   `options.placeHolder` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Character used to replace profane words.
    -   `options.regex` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Regular expression used to sanitize words before comparing them to blacklist.
    -   `options.replaceRegex` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Regular expression used to replace profane words with placeHolder.

#### isProfane

Determine if a string contains profane language.

**Parameters**

-   `string` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** String to evaluate for profanity.

#### replaceWord

Replace a word with placeHolder characters;

**Parameters**

-   `string` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** String to replace.

#### clean

Evaluate a string for profanity and return an edited version.

**Parameters**

-   `string` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Sentence to filter.

#### addWords

Add word(s) to blacklist filter / remove words from whitelist filter

**Parameters**

-   `word` **...[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Word(s) to add to blacklist

#### removeWords

Add words to whitelist filter

**Parameters**

-   `word` **...[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Word(s) to add to whitelist.


## License

The MIT License (MIT)

Copyright (c) 2024 Michael Price

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
