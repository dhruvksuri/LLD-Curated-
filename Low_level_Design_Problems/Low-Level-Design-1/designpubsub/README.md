MessageBroker - List of Topics
  1. Can create Topic, can add partition in Topic.
  2. Publish & Subscribe to Topic.
  3. Create consumer group
  https://github.com/dhruvksuri/LLD-Curated-/blob/main/Low_level_Design_Problems/Low-Level-Design-1/designpubsub/publicInterface/MessageBroker.java

Topic - Name, Id, Set of Partition
 1. Can add Partition

Partition - Name, Id, Key, List/queue of Messages, List of Consumers
1. Can add Messages
2. Each consumer can have their own queue(local). As soon as message is added to partition, it would send to consumer queue which it can listen.

Publishers would write to remote queue of Topic inside Partition.

 MessageBroker broker = new MessageBroker();

        // 1. Creating a Topic
        Topic topic = broker.createTopic("Topic1");

        // 2. Creating partitions in Topic
        Partition p1= broker.createPartition(topic,"P1");
        Partition p2= broker.createPartition(topic,"P2");
        Partition p3= broker.createPartition(topic,"P3");

        // 3. Create a consumerGroup
        ConsumerGroup consumerGroup= broker.createConsumerGroup("C_G1",3);

        // 4. Create multiple Consumers in a ConsumerGroup
        Consumer c1 = broker.createConsumer("C1",consumerGroup);
        Consumer c2 = broker.createConsumer("C1",consumerGroup);
        Consumer c3 = broker.createConsumer("C1",consumerGroup);

        // 5. Subscribe a consumer_group to a particular topic and partitions
        broker.subscribe(topic,p1,c1);
        broker.subscribe(topic,p2,c2);
        broker.subscribe(topic,p3,c3);

        // 6. publish message
        broker.publish(topic,p1,new Message("Hey"));

        new Thread(c1).start();
        new Thread(c2).start();
        new Thread(c3).start();
