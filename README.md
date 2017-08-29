# fetch-reply-with

[![npm version](https://badge.fury.io/js/fetch-reply-with.svg)](https://www.npmjs.com/package/fetch-reply-with) [![Shippable branch](https://img.shields.io/shippable/59a3e414c80c0407002b779f/master.svg)](https://app.shippable.com/projects/59a3e414c80c0407002b779f) [![Linked In](https://img.shields.io/badge/Linked-In-blue.svg)](https://www.linkedin.com/in/john-i-doherty) [![Twitter Follow](https://img.shields.io/twitter/follow/CambridgeMVP.svg?style=social&label=Twitter&style=plastic)](https://twitter.com/CambridgeMVP)

Node module to mock [fetch](https://www.npmjs.com/package/isomorphic-fetch) http requests using `.replyWith`, simplifying unit testing

## Install

```bash
npm install --save-dev fetch-reply-with
```

## Usage

```js
require('fetch-reply-with'); // <- fetch is now globally available within the node environment

// add a fetch reply for GET http://www.orcascan.com
fetch('http://www.orcascan.com', {

    // regular fetch option
    method: 'GET',

    // add reply for this fetch
    replyWith: {
        status: 200,
        body: 'Bulk Barcode Scanning app',
        headers: {
            'Content-Type': 'text/html'
        }
    }
})
.then(function(res) {
    // handle the response within the first then
    // as suggested by https://github.com/kevmarchant
});

// or at some point in the future
fetch('http://www.orcascan.com').then(function(res){
    return res.text();
})
.then(function(text){
    // text now equals Bulk Barcode Scanning app
});
```

_Requests without replies are executed as normal._

## Tests

The project includes unit tests, to run the tests execute the following from the command line:

```bash
git clone https://github.com/john-doherty/fetch-reply-with
cd fetch-reply-with
npm install
npm test
```

## License

Licensed under [MIT License](LICENSE) &copy; [John Doherty](http://www.johndoherty.info)