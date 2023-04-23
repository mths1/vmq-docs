---
description: Topics Tree and Performance hints
---

# Topic Tree
In MQTT, a well-designed and concise topic tree is essential. A poorly organized topic tree, that is overly complex, or lacking in structure 
makes it difficult to manage and scale.

Therefore, it is important to invest time and effort in upfront design of the topic tree to ensure that it is clear, concise, 
and structured in a logical and consistent manner. This can involve defining the topic levels, naming conventions, and hierarchy of topics 
to reflect the needs and requirements of your specific use-case.

## Things to consider
* Topics are case-sensitive. `VerneMQ/t1` and `VERNEMQ/t1` are not the same topics.
* The beginning slash can and should be omitted. `/VerneMQ/t1` and `VerneMQ/t1` are not the same topics.

## Dos and Don'ts
In the following, we will present the dos and don'ts of MQTT topics, to provide a useful guide for designing an effective and well-organized topic tree.
### Dos:
* DO keep topic names short and descriptive: A clear and concise topic name can make it easier to understand the purpose of a message and reduce the likelihood of errors.
* DO use a hierarchical structure for topics: A hierarchical structure can make it easier to manage topics and ensure that they are organized in a logical and understandable way.
* DO use forward slashes (/) to separate topic levels: The use of forward slashes can help to create a clear and hierarchical structure for topics.
* DO use wildcards to subscribe to multiple topics: MQTT supports two types of wildcards: "+" for a single level and "#" for multiple levels.
* DO use unique topic names: Using unique topic names can help to avoid conflicts and ensure that messages are sent and received by the intended recipients.

###  Don'ts:
* DON'T use spaces or any other special characters in topic names, do not depend on case-sensivity: Special characters and spaces can cause issues with message delivery and create confusion.
* DON'T use too many levels in topic names: While a hierarchical structure can be helpful, it is important to avoid creating overly complex topic names with too many levels.
* DON'T use topics that are too generic: Using generic topic names can make it difficult to understand the purpose of a message and create confusion for subscribers. 
* DON'T start the topic tree with a forward slash: Starting the topic tree with a forward slash can cause issues with topic subscriptions and create confusion for MQTT clients.

## Alias
In MQTT, a topic alias can be used in place of the actual topic name. The mapping is done by the broker. It allows a client to reduce the size of a published message.
Topic aliases are an MQTTv5 feature and negotiated between client and broker during the CONNECT message exchange. An introduction into aliasing is provided here: 
https://vernemq.com/blog/2019/10/21/saving-bandwith-with-topic-aliases.html

## Remarks on permformance
* Avoid single consumers that subscribe to a lot of topics indivually. Use wildcards instead whenenver feasable. VerneMQ otherwise might take some time and resources to manage and distribute subscriptions.
* Avoid subscribing to the whole topic tree (#). This is prone to overload the subscriber as the traffic grows.
* For very constrained devices you can use a little known feature called aliasing. Thus you can reduce the actual payload send by the client.
* Make use of shared subscriptions to offload work to multiple workers

## Further reading
* https://vernemq.com/intro/mqtt-primer/topic_routing.html
* https://vernemq.com/blog/2019/10/21/saving-bandwith-with-topic-aliases.html
