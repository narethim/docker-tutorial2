# Example

## 1 Step 1

Introducing a very simple image.

### 1.1 Dockerfile

Dockerfile

```docker
FROM node:9.3.0-alpine
```

### 1.2 Build docker image

Build command:

```sh
docker build .
```

Tag it as: 'flipp-node:latest'

```sh
docker build . -t flipp-node:latest
```

### 1.3 Run docker container

```sh
docker run -it flipp-node:latest /bin/sh
```

## 2 Step 2

Add `node' app to the container.

### 2.1 Dockerfile

Dockerfile

```docker
FROM node:9.3.0-alpine

WORKDIR /app

ADD . /app
```

server.js

```js
var http = require('http');

http.createServer(function (req, res) {
  res.write('Hello World!');
  res.end();
}).listen(8000);
```

### 2.2 Build docker image

Build command:

```sh
docker build . -t flipp-node:latest
```

### 2.3 Run docker container

```sh
docker run -p 8000:8000 -it flipp-node:latest node server.js
```

```sh
firefox http://localhost:8000
```


