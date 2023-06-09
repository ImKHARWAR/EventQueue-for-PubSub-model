# EventQueue-for-PubSub-model

Requirement and Dependencies ->

1.Apache Kafka Along with Zookeeper

2.MongoDB Atlas

3.Java 17 or above

4.Springboot Framework

5.Maven Dependencies like SpringWeb MVC, Apache Kafka, MongoDB

6.Ngrok

7.Metamask Account with sufficient Sepolia Ether and Seploia LINK for testing on Sepolia TestNet 

8.ChainLink.sol


Setup steps ->

1.Run Zookeeper using command ".\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties" for windows from the kafka folder.
("/bin/zookeeper-server-start.sh /config/zookeeper.properties" for linux)

2.Run Kafka Server using command ".\bin\windows\kafka-server-start.bat .\config\server.properties" for windows from the kafka folder.
("/bin/kafka-server-start.sh /config/server.properties" for linux)

3.Add Current System IP in mongoDB atlas on mongoDB Atlas website under connect tab and update its url in "application.properties" file in EventQueue project.

4.Run ngrok and bind the "localhost:8080" to a global ip using command "ngrok.exe 8080" on ngrok terminal.

Steps to Run ->

1.Start the EventQueue Project in IntelliJ IDEA(preferred) or any other IDE.

2.Start Solidity IDE (preferred Remix) and complie and deploy the smart contracts "'GetMethodAPI.sol", "PostMethodAPI.sol" and "Demo.sol".

3.Open "Demo.sol" deployed contract.

4.Set the deployed address of PostMethodAPI contract using "setAddrPost" method.

5.Set the deployed address of GetMethodAPI contract using "setAddrGet" method.

6.Fund the Deployed "GetMethodAPI.sol" and 'PostMethodAPI.sol" contracts with 'LINK' using metamask account (0.1 LINK per get or post request, refer to official documentation of ChainLink).

7.Set the parameter of "postRequest(url,user_id,topic_id,msg)" method for publishing data where 'url' is appened as the '{url}/rest/api/publish?' which we got from ngrok. (Referf to Offical Documentation of ChainLink for any issue)

8.Transact "postRequest" Method and wait for few seconds and call "postMessage" to fetch output of the request.

9.Set the parameter of "getRequest(url,user_id,topic_id,path)" method for publishing data where 'url' is appened as the '{url}/rest/api/view?' which we got from ngrok and {path} is the address of variable for which you want to get value. (Referf to Offical Documentation of ChainLink for any issue)

10.Transact "getRequest" Method and wait for few seconds and call "getMessage" to fetch output of the request.

11.See the output of postRequest in postResponse variable and getRequest in getResponse variable.

12.Reset Contract using reset method and use again with new Parameters.
