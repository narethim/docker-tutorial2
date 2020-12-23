# Example

## 3 Step 3

Add `node' app to the container.
Add CMD to execute the command in the container automatically.

### 3.1 Dockerfile

Dockerfile

```docker
FROM node:9.3.0-alpine

WORKDIR /app

ADD . /app

CMD  ["node", "server.js"]
```

server.js

```js
var = http = require('http');

http.createServer(function (req, res) {
  res.write('Hello World!');
  res.end();
}).listen(8000);
```

### 3.2 Build docker image

Build command:

```sh
docker build . -t flipp-node:latest
```

### 3.3 Run docker container

Run in detach mode ( -d )

```sh
docker run -d -p 8000:8000 -it flipp-node:latest
```

```sh
firefox http://localhost:8000
```

### 3.4 Stop docker container

```sh
docker ps

# docker stop <name>

docker stop adoring_chaum
```

