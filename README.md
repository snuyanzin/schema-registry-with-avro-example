Example of Avro serialization/deserialization messages to Kafka.
Producer takes Kafka connection info and a semicolon separated file to generate messages

HowTo
1. `./mvnw clean verify`, or `mvnw clean verify` for Windows

Pass appropriate values for the next list of arguments as in examples below
```
-bootstrap, -bs                  A list of host/port pairs to use for establishing the initial connection to the Kafka cluster
-schemaregistryurl, -srurl       Schema registry url
-schemaregistryuser, -sru        Schema registry user
-schemaregistrypassword, -srp    Schema registry user
-sslkeypassword, -sslp           The password of the private key in the key store file
-keystore, -ks                   The location of the key store file
-keystorepassword, -ksp          The store password for the key store file
-truststore, -ts                 The location of the trust store file
-truststorepassword, -tsp        The password for the trust store file
-f                               Semicolon separated file with data
-t                               Kafka topic
```

An example of message producing (for Windows use producer.bat)
```
bin/producer -bs kafka-1690a57d-senu-dev-sandbox.aivencloud.com:12693 \
             -ksp myKeySt0reP@ssw0rd \
             -srurl https://kafka-1690a57d-senu-dev-sandbox.aivencloud.com:12696 \
             -ts /path/to/client.truststore.jks \
             -tsp myTrustSt0reP@ssw0rd \
             -ks /path/to/client.keystore.p12 \
             -srp MySchem@RegistryP@ssw0rd \
             -sru avnadmin \
             -sslp mySSLKeyP@ssw0rd \
             -f fileWithData \
             -t clickrecordTopic
```

An example of message consumption (for Windows use consumer.bat)
```
bin/consumer -bs kafka-1690a57d-senu-dev-sandbox.aivencloud.com:12693 \
             -ksp myKeySt0reP@ssw0rd \
             -srurl https://kafka-1690a57d-senu-dev-sandbox.aivencloud.com:12696 \
             -ts /path/to/client.truststore.jks \
             -tsp myTrustSt0reP@ssw0rd \
             -ks /path/to/client.keystore.p12 \
             -srp MySchem@RegistryP@ssw0rd \
             -sru avnadmin \
             -sslp mySSLKeyP@ssw0rd \
             -t clickrecordTopic
```

An example of `fileWithData` content
```
Any line without semicolon is considered as a comment
SESSION  CHANNEL   BROWSER   CAMPAIGN     REFERRER   IP
session1;channel1;mozilla;campaign2;referrer1;32.18.1.1
session2;channel2;chrome;campaign1;referrer3;72.168.1.1
```