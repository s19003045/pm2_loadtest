# pm2 with loadtest

## Environment
  - node.js ：v12.16.1

## Installation
  - install packages：
    ```npm install```
  - install pm2
    - install : ```npm install pm2 -g```
    - Official website：https://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/
  - install loadtest
    - install : ```npm install loadtest -g```
    - command:```loadtest [-n requests] [-c concurrency] [-k] URL```
    - npm：https://www.npmjs.com/package/loadtest

## Usage
  - With pm2：
    - start server：
      ```node app.js```
    - load test:
      ```loadtest -n 1000 -c 100 http://localhost:3000/```
    - after load test，close server
  - Without pm2：
    - start server with pm2：set up cluster (4 workers)
      ```pm2 start -i 4 app.js```
      or
      (named cluster:server)
      ```pm2 start -i 4 --name server app.js``` 
    - load test:
      ```loadtest -n 1000 -c 100 http://localhost:3000/```
    - after load test，close server
      ```pm2 delete app```
      or
      (named cluster:server)
      ```pm2 delete server```

