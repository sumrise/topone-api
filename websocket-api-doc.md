# topone-api

Official Documentation for the APIs

TOP.ONE 交易接口说明

# WebSocket API   

## 请求交互    

WebSocket服务连接地址：`wss://subscribe.top.one/ws/`     
流程：   
1）建立Websocket连接   
2）发送订阅数据请求    
3）接收推送数据及订阅响应   

订阅响应：   
`{"result": "success", "id": 0, "error": null}`

## API参考  

### 1)订阅深度数据
请求数据格式为：  
`{"method":"depth.subscribe","params":["TOP/ETH", "1x", 10],"id":0}`  
其中  
TOP/ETH: 交易市场名称   
1x: 深度合并(不合并)   
10: 买卖深度数据各10个报价    

推送深度数据示例： 

      {    
          "params": [
              "TOP/ETH",
              [
                  {
                      "bids": [
                          ["0.00001076", "175156"],
                          ["0.00001072", "125499"],
                          ["0.0000107", "7392"],
                          ["0.00001062", "8823"],
                          ["0.0000106", "10000"],
                          ["0.00001051", "32523"],
                          ["0.0000105", "311805"],
                          ["0.00001022", "222222"],
                          ["0.00001011", "42830"],
                          ["0.0000101", "623042"]],
                      "asks": [
                          ["0.0000115", "307646"],
                          ["0.0000119", "30000"],
                          ["0.00001195", "250342"],
                          ["0.000012", "507700"],
                          ["0.00001207", "64161"],
                          ["0.0000121", "30000"],
                          ["0.00001229", "70000"],
                          ["0.00001235", "80483"],
                          ["0.00001237", "1767403"],
                          ["0.00001239", "20000"]],
                      "time": 1526266518.043814
                  }
              ]
          ],
          "method": "depth.update",
          "id": null
      }
 
 ### 2)订阅成交tick
请求数据格式为：  
`{"method":"deals.subscribe","params":["TOP/ETH"],"id":0}`  
其中  
TOP/ETH: 交易市场名称   

推送成交数据示例： 

    {
        "params": [
            "TOP/ETH",
            [
                  [1526261908.24362, "0.0000115", "97045", 2],
                  [1526259958.30595, "0.0000115", "5000", 2],
                  [1526254787.086168, "0.00001149", "849000", 2],
                  [1526254688.183289, "0.00001073", "700000", 1],
                  [1526245846.150899, "0.00001072", "61397", 1],
                  [1526245846.150774, "0.00001073", "76489", 1],
                  [1526245846.15065, "0.00001074", "34256", 1],
                  [1526245846.150516, "0.00001075", "67854", 1],
                  [1526245846.150349, "0.00001077", "34526", 1],
                  [1526245846.150203, "0.00001082", "7000", 1]
            ]
        ],
        "method": "deals.update",
        "id": null
    }
 