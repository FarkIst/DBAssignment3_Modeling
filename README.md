# DBAssignment3_Modeling

## 1. Twitter Data

### 1.1 How many Twitter users are in the database?
![picture](https://github.com/FarkIst/DBAssignment3_Modeling/blob/master/img/Q1.PNG)

### 1.2 Which Twitter users link the most to other Twitter users? (Provide the top ten.)
![picture](https://github.com/FarkIst/DBAssignment3_Modeling/blob/master/img/Q2.PNG)

### 1.3 Who are the most mentioned Twitter users? (Provide the top five.)
![picture](https://github.com/FarkIst/DBAssignment3_Modeling/blob/master/img/Q5.PNG)

### 1.4 Who are the most active Twitter users (top ten)?
![picture](https://github.com/FarkIst/DBAssignment3_Modeling/blob/master/img/Q3.PNG)

### 1.5 Who are the five most grumpy (most negative tweets) and the most happy (most positive tweets)?
![picture](https://github.com/FarkIst/DBAssignment3_Modeling/blob/master/img/Q4.PNG)


## 2. Modeling

### Arrays of Ancestors
* Atomicity
   * The write operation is atomic considering a single document. When we execute a write or insert operation, only one document is created or updated
* Indexes
  * It is possible to add indexes, however in this case the indexes were automatically generated and are represented by the \_id field.
* Large Number of Collections
  * I am storing all information in one collection, not separating them into multiple collections, since it is unnecesarry for our purpose. In order to obtain a large collection, we have to refer to the ancestor of each document.

### Materialized Paths
* Sharding
   * Sharding is a very exciting aspect of MongoDB, since it provides horizontal scaling, involving dividing the system dataset and load over multiple servers resulting in a set of machines handling a subset of the overall workload, potentially providing better efficiency. To my undesrstanding my query system does not include sharding, since I did not create shard clusters or shard keys. In my case the shard key could possibly be the \_id, provided that I follow recommended design patterns, and set up identity. 
* Large Number of Collections
   * Very similar to the explanation in Arrays of Ancestors/Large Number of Collections, since the path is stored in the document.
* Collection Contains Large Number of Small Documents
   * MongoDB stores data as a binary represantation of JSON documents, referred to as BSON documents. In our case every line from the CSV file corresponding to a header is a document (Document example: \_id, polarity, id, date, query, user, text; where each of these headers contain information). In our case there is a large number of documents containing smaller documents.
### Nested Sets
 - The tree like structure is imutable.

* Atomicity
  * The write operation is atomic considering a single document. When we execute a write or insert operation, only one document is created or updated
* Sharding
  * In this regard because of the imutability, sharding can increase complexity. The nested sets pattern is inneficient in regards to modifying the tree structure, it's best used for static trees that do not change.
* Indexes
  * As far as I understand indexes are represented by the fields 'left' 'right'. The purpose using indexes is therefore obsolete, since we can use it for parent node and the previously mentioned fields.
