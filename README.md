# kafka_simpe_example
kafka simple example 3 clusters

# run project with
docker compose up -d

# create topic
docker exec -it kafka-1 kafka-topics --create --topic example-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

# run producer container
docker exec -it kafka-1 kafka-console-producer --broker-list localhost:9092 --topic example-topic

# run consumer
docker exec -it kafka-1 kafka-console-consumer --bootstrap-server localhost:9092 --topic example-topic --from-beginning

# miscellaneous

kafka-topics --list --bootstrap-server localhost:9092
kafka-topics --delete --topic example-topic --bootstrap-server localhost:9092 
docker compose down --volumes --remove-orphans
kafka-topics.sh --create --topic example-topic --partitions 3 --replication-factor 2 --bootstrap-server kafka-1:9092

