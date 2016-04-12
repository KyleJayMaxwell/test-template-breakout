# Mocha Chai Set Up - for integration testing
(Assuming you are using Yo Galvanize Express, and mocha is already installed globally)

## Steps

1. Create a "test" directory in project root
1. Install dependencies :

```sh
$ npm install chai chai-http mocha --save-dev
```

1. Add a "test" script to *package.json*:

```json
"test": "mocha"
||
 "test": "mocha --recursive"
```

1. Add new file called *mocha.opts* to the "test" directory and add the following flag. So mocha looks into all directories in the "test" directory for all tests:

```
--recursive
```

1. Create a new folder called "integration" within the "test" directory.

1. Create a new file for each route resource that you are testing - i.e., *AUTHORS-routes.js* - within the "integration" directory (*cars-routes.js*, in this case)

1. Add the following base testing config for each test file, also in the base-test-template.js.

```
  process.env.NODE_ENV = 'test';

  var chai = require('chai');
  var chaiHttp = require('chai-http');
  var server = require('../../src/server/app');
  var should = chai.should();

  chai.use(chaiHttp);


  describe('car routes', function() {


    // beforeEach(function(done) {
    //   done();
    // });

    // afterEach(function(done) {
    //   done();
    // });

    describe('', function() {

      it('', function(done) {
          done();
      });
    });

  });
```

1. Only show the logger if the `NODE_ENV` is not 'test'. So, add an if statement to the config middleware: 

  ```javascript
  if (process.env.NODE_ENV !== 'test'){
    app.use(logger('dev'));
  };
  ```

