# Example

## 4 Step 4

Add `node' app to the container.
Add ENTRYPOINT and CMD to execute the command in the container automatically.

ENTRYPOINT ["node'] - node is the execuatble application binary
CMD ["server.js"] - is the argument list

### 4.1 Dockerfile

Dockerfile

```docker
FROM node:9.3.0-alpine

WORKDIR /app

ADD . /app

ENTRYPOINT ["node"]

CMD  ["server.js"]
```

server.js

```js
var http = require('http');

http.createServer(function (req, res) {
  res.write('Hello World!');
  res.end();
}).listen(8000);
```

### 4.2 Build docker image

Build command:

```sh
docker build . -t flipp-node:latest
```

### 4.3 Run docker container

Run in detach mode ( -d )

```sh
docker run -d -p 8000:8000 -it flipp-node:latest
```

Verify it

```sh
docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES
fd093d34067f        flipp-node:latest   "node server.js"    59 seconds ago      Up 58 seconds       0.0.0.0:8000->8000/tcp   wizardly_hawking
```

```sh
firefox http://localhost:8000
```

### 4.4 Stop docker container

```sh
# docker stop <name>
docker stop wizardly_hawking
```

