# kafka-eagle-docker
###### smartloli kafka-eagle Dockerfile


---
- ### docker-compose.yaml
  ```yaml
  version: '2'
  services:
    kafka-eagle:
      container_name: kafka-eagle
      image: buzhiyun/kafka-eagle
      ports:
        - "8048:8048"
      volumes:
        - ./system-config.properties:/opt/kafka-eagle/conf/system-config.properties
        - ./db:/hadoop/kafka-eagle/db
  ```
---
- ### system-config.properties
  ```properties
  ######################################
  # multi zookeeper & kafka cluster list
  ######################################
  kafka.eagle.zk.cluster.alias=cluster1,cluster2
  cluster1.zk.list=tdn1:2181,tdn2:2181,tdn3:2181
  cluster2.zk.list=xdn10:2181,xdn11:2181,xdn12:2181
  
  ######################################
  # broker size online list
  ######################################
  cluster1.kafka.eagle.broker.size=20
  
  ######################################
  # zk client thread limit
  ######################################
  kafka.zk.limit.size=25
  
  ######################################
  # kafka eagle webui port
  ######################################
  kafka.eagle.webui.port=8048
  
  ######################################
  # kafka offset storage
  ######################################
  cluster1.kafka.eagle.offset.storage=kafka
  cluster2.kafka.eagle.offset.storage=zk
  
  ######################################
  # kafka metrics, 30 days by default
  ######################################
  kafka.eagle.metrics.charts=false
  kafka.eagle.metrics.retain=30
  
  ######################################
  # kafka sql topic records max
  ######################################
  kafka.eagle.sql.topic.records.max=5000
  kafka.eagle.sql.fix.error=false
  
  ######################################
  # delete kafka topic token
  ######################################
  kafka.eagle.topic.token=keadmin
  
  ######################################
  # kafka sasl authenticate
  ######################################
  cluster1.kafka.eagle.sasl.enable=false
  cluster1.kafka.eagle.sasl.protocol=SASL_PLAINTEXT
  cluster1.kafka.eagle.sasl.mechanism=SCRAM-SHA-256
  cluster1.kafka.eagle.sasl.jaas.config=org.apache.kafka.common.security.scram.ScramLoginModule required username="kafka" password="kafka-eagle";
  cluster1.kafka.eagle.sasl.client.id=
  cluster1.kafka.eagle.sasl.cgroup.enable=false
  cluster1.kafka.eagle.sasl.cgroup.topics=
  
  cluster2.kafka.eagle.sasl.enable=false
  cluster2.kafka.eagle.sasl.protocol=SASL_PLAINTEXT
  cluster2.kafka.eagle.sasl.mechanism=PLAIN
  cluster2.kafka.eagle.sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required username="kafka" password="kafka-eagle";
  cluster2.kafka.eagle.sasl.client.id=
  cluster2.kafka.eagle.sasl.cgroup.enable=false
  cluster2.kafka.eagle.sasl.cgroup.topics=
  
  ######################################
  # kafka sqlite jdbc driver address
  ######################################
  kafka.eagle.driver=org.sqlite.JDBC
  kafka.eagle.url=jdbc:sqlite:/hadoop/kafka-eagle/db/ke.db
  kafka.eagle.username=root
  kafka.eagle.password=www.kafka-eagle.org
  
  ######################################
  # kafka mysql jdbc driver address
  ######################################
  #kafka.eagle.driver=com.mysql.jdbc.Driver
  #kafka.eagle.url=jdbc:mysql://127.0.0.1:3306/ke?useUnicode=true&characterEncoding=UTF-8&zeroDateTimeBehavior=convertToNull
  #kafka.eagle.username=root
  #kafka.eagle.password=123456
  ```
