
# unwashed-words

A filter for toxic-words in English, Spanish, French, and Arabic.


## Installation

    npm i unwashed-words --save

## Usage

```jsx
import React from 'react';
import Filter from 'unwashed-words';

function App() {
  const filter = new Filter();

  return (
    <div>
      {filter.clean("Don't be an ash0le")} {/* Output: Don't be an a***** */}
    </div>
  );
}

export default App;
```

### Placeholder Overrides

```jsx
import React from 'react';
import Filter from 'unwashed-words';

function App() {
  const customFilter = new Filter({ placeHolder: 'x' });

  return (
    <div>
      {customFilter.clean("Don't be an ash0le")} {/* Output: Don't be an axxxxx */}
    </div>
  );
}

export default App;
```

### Add words to the blacklist

```jsx
import React from 'react';
import Filter from 'unwashed-words';

function App() {
  const filter = new Filter();

  // Adding words to the blacklist
  filter.addWords('some', 'toxic', 'word');

  return (
    <div>
      {filter.clean("some toxic word!")} {/* Output: s*** t** w***! */}
    </div>
  );
}

export default App;
```

### Instantiate with an empty list


```jsx
import React from 'react';
import Filter from 'unwashed-words';

function App() {
  const filter = new Filter({ emptyList: true });

  return (
    <div>
      {filter.clean('hell this wont clean anything')} {/* Output: hell this wont clean anything */}
    </div>
  );
}

export default App;
```

### Remove words from the blacklist

```jsx
import React from 'react';
import Filter from 'unwashed-words';

function App() {
  const filter = new Filter();

  // Removing specific words from the blacklist
  filter.removeWords('hells', 'sadist');

  return (
    <div>
      {filter.clean("some hells word!")} {/* Output: some hells word! */}
    </div>
  );
}

export default App;
```

## Author

- [@anurag](https://github.com/anuragrathour132002)

#

## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://anuragrathour.in/)

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anurag-rathour07/)

#

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

