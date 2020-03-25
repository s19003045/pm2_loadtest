# 使用 pm2 以提升效能

### 相關套件
  - pm2
    ```npm install pm2 -g```
  - loadtest
    ```npm install loadtest -g```

### 啟動及測試
  - 狀況一：
    - 啟動 server：
      ```node app.js```
    - 壓力測試
      ```loadtest -n 1000 -c 100 http://localhost:3000/```
    - 測試完畢後，關閉 server
  - 狀況二：
    - 啟動 pm2：建立 cluster ，共 4 個 worker
      ```pm2 start -i 4 app.js```
      或
      (命名 cluster 為 server)
      ```pm2 start -i 4 --name server app.js``` 
    - 壓力測試
      ```loadtest -n 1000 -c 100 http://localhost:3000/```
    - 測試完畢後，關閉 server
      ```pm2 delete app```

### 補充：pm2 指令
  - 官網：https://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/

### loadtest 指令
  ```loadtest [-n requests] [-c concurrency] [-k] URL```
  - 官網：https://www.npmjs.com/package/loadtest
