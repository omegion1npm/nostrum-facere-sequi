<p align="center">
  <a href="https://github.com/omegion1npm/nostrum-facere-sequi">
    <img src="./assets/logo.png" width="256" alt="Rest URL Parser" />
  </a>
</p>

# Rest URL Parser

[![license](https://img.shields.io/github/license/omegion1npm/nostrum-facere-sequi)](https://github.com/omegion1npm/nostrum-facere-sequi)
[![npm](https://img.shields.io/npm/v/@omegion1npm/nostrum-facere-sequi)](https://www.npmjs.com/package/@omegion1npm/nostrum-facere-sequi)

Only a function called `parseRequestURL()`. 

Simplify the handling of URLs that contain parameters..

It's particularly useful for applications that deal with REST APIs where resource identifiers are embedded in the URL.

## Table of Contents

- [Rest URL Parser](#rest-url-parser)
  - [Table of Contents](#table-of-contents)
  - [Get Started](#get-started)
    - [Install](#install)
  - [Usage](#usage)
  - [API](#api)
  - [Contributing](#contributing)
  - [License](#license)

## Get Started

### Install

This project uses [node](http://nodejs.org) and [npm](https://npmjs.com). Please install them first.

```sh
npm install  @omegion1npm/nostrum-facere-sequi
```

## Usage

```javascript
import parseRequestURL from '@omegion1npm/nostrum-facere-sequi';

const sourceConfig = {
  url: '/user/:userId/post/:postId',
  params: {
    userId: '123',
    postId: '456',
  },
};

const result = parseRequestURL(sourceConfig);

console.log(result);
```

Use with Axios:

```javascript
import parseRequestURL from '@omegion1npm/nostrum-facere-sequi';

const instance = axios.create(appConfig.httpClient);

const requestInterceptor = instance.interceptors.request.use(
  function (config) {
    const restConfig = parseRequestURL(config);
    return restConfig;
  },
  function (error) {
    return Promise.reject(error);
  }
);

instance.post('/user/:userId/post/:postId', {
  userId: '123',
  postId: '456',
});
```

## API

**parseRequestURL(sourceConfig)**

This function takes a `sourceConfig` object and parses the `url` property for parameters. It returns the updated `sourceConfig`.

```javascript
parseRequestURL(sourceConfig);
```

## Contributing

Your contributions and suggestions are heartily welcome.
Submit an issue or submit a pull request.

Thanks to all the people who already contributed!

<a href="https://github.com/omegion1npm/nostrum-facere-sequi/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omegion1npm/nostrum-facere-sequi" />
</a>

## License

[MIT](https://opensource.org/licenses/MIT)
