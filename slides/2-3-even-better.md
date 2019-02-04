## Even Better!

```javascript
// ./init.js
const $ = require('jquery')
require('jquery-ui')

module.exports = function init() {
  $('body')
    .append('<h1>Hello, World!</h1>')
    .effect('slide', 250)
}

// ./main.js
const $ = require('jquery')
const init = require('./init')

$(init)
```

