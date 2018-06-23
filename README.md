# 201807-NYC-QCON

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# How did it all start?
 
October 2008. It all started with Satoshi Nakamoto and his paper [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf) which addressed a key problem in electronic commerce:

<img src="https://farm5.staticflickr.com/4505/24079519258_ab8a80f7ed_o.png" width="769" height="229" alt="Double Spending">
<p>

<i>A blockchain is a decentralized virtual ledger for recording transactions <b>without central authority </b> through a distributed cryptographic protocol. It is made up of three technologies 

1. cryptographic algorithms, 
1. a distributed protocol, 
1. and replicated data 
<p>
which combined provide a trustworthy service to a group of nodes that do not fully trust each other. 
<p>
</i>
<p>
Source: https://www.zurich.ibm.com/dccl/papers/cachin_dccl.pdf

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# The Blockchain Distributed Ledger  
  
<img src="https://www.ibm.com/blogs/internet-of-things/wp-content/uploads/2017/05/2-1.jpg">
<p> 
A distributed ledger is a type of database that is shared, replicated, and synchronized among the members of a network. The distributed ledger records the transactions, such as the exchange of assets or data, among the participants in the network.

Participants in the network govern and agree <b>by consensus</b> on the updates to the records in the ledger. <b>No central, third-party mediator, such as a financial institution or clearinghouse, is involved.</b>

Every record in the distributed ledger has a timestamp and unique crytographic signature, thus making the ledger an auditable history of all transactions in the network. One implementation of distributed ledger technology is the open source Hyperledger Fabric blockchain.

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Programming the Blockchain with Chaincode

http://hyperledger-fabric.readthedocs.io/en/release-1.1/chaincode.html

Chaincode is a program, written in Go, node.js, and eventually in other programming languages such as Java, that implements a prescribed interface. Chaincode runs in a secured Docker container isolated from the endorsing peer process. Chaincode initializes and manages ledger state through transactions submitted by applications.

A chaincode typically handles business logic agreed to by members of the network, so it may be considered as a “smart contract”. State created by a chaincode is scoped exclusively to that chaincode and can’t be accessed directly by another chaincode. However, within the same network, given the appropriate permission a chaincode may invoke another chaincode to access its state.



# Blockchain Usecases
[Blockchain usecases from IBM](https://www.ibm.com/blockchain/use-cases/)

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

<img src="https://www.hyperledger.org/wp-content/uploads/2016/09/logo_hl_new.png">
<p>

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Hyperledger : http://hyperledger.org/

[Hyperledger Documentation](https://hyperledger-fabric.readthedocs.io/en/release/)

Hyperledger, an open source collaborative effort to advance cross-industry blockchain technologies, 
is hosted by The Linux Foundation®. 

Deployed in Docker images.

<img src="https://farm5.staticflickr.com/4494/37926120211_b7dddb090d_o.png" width="682" height="423" alt="Hyperledger Services">
<p> Permissioned<p> 
Google RPC P2P Protocol<p> 
https://medium.com/@robertgreenfieldiv/hyperledger-blockchain-for-a-web-2-0-architecture-6d3c83818eb1
<p>

# Hyperledger main components 

<img src="https://farm5.staticflickr.com/4660/25963918068_b7a6234a86_b.jpg" width="1024" height="539" alt="EndorsementConsensus">

It is also important to note the Hyperledger Fabric has HSM (Hardware Security Module) support which is vital for safeguarding and managing digital keys for strong authentication. Hyperledger Fabric provides modified and unmodified PKCS11 for key generation, which supports cases like identity management that need more protection.


## Hyperledger Composer

### [Composer Playground](https://composer-playground.mybluemix.net/login)

### Hyperledger Fabric

### [IBM Blockchain Platform Service](https://console.bluemix.net/catalog/services/blockchain)
### [IBM Blockchain Platform](https://console.bluemix.net/developer/blockchain/dashboard)

## [Launch a basic IBM Blockchain network on the IBM Container Service's free plan](https://ibm-blockchain.github.io)


## Channels
A Hyperledger Fabric channel is a private “subnet” of communication between two or more specific network members, for the purpose of conducting private and confidential transactions. 

## The Ledger and the State Database

There are two place which "store" data in Hyperledger Fabric:
### The ledger is the actual "blockchain". 
It is a file-based ledger which stores serialized blocks. Each block has one or more transactions. <br>
Each transaction contains a read-write set which modifies one or more key/value pairs. <br>
The ledger is the definitive source of data and is immutable.

### The state database holds the last known committed value for any given key. 
It is populated when each peer validates and commits a transaction. <br>
The state database can always be rebuilt from re-processing the ledger. <br>
There are currently two options for the state database: an embedded LevelDB or an external CouchDB.
<p>
As an aside, if you are familiar with Hyperledger Fabric channels, there is a separate ledger for each channel as well.
<p>
When we query from where do we retrieve data?  1) from the blockchain chain or 2) from state db? <p>.
If it is from state db how can it retrieve a specific key because you mentioned "state database holds the last known committed value for any given key" <p> 
Queries or GetState in chaincode return data from the state db. They will only return the last value for a key. <p>
If you want to get the entire history for a key, you need to enable the historical database in the configuration of your peer 

### Chaincode.
Like <b>Stored Procedures</b> in a traditional database, handles business logic. http://hyperledger-fabric.readthedocs.io/en/release/chaincode4ade.htm

<img src="https://farm5.staticflickr.com/4523/38243385192_43d682cf94_o.png" width="910" height="483" alt="Hyperledger helloworld 2">
<p>  
Chaincode is a piece of code that is written in one of the supported languages such as Go or Java. It is installed and instantiated through an SDK or CLI onto a network of Hyperledger Fabric peer nodes, enabling interaction with that network's shared ledger. 
  
 ### [Consensus](https://www.zurich.ibm.com/blockchain/) 
 <p>Today, consensus protocols exist in many variations, but all of them need a majority or even a qualified majority (such as 2/3 of the nodes) to be correct, whereas the remaining ones could fail, misbehave, or even act adversarially against finding consensus.

Starting with the celebrated protocols for Byzantine Agreement established in 1982, consensus protocols have found widespread applications for keeping distributed systems healty and making cloud platforms operate continuously. </p> 



<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband"> 
  
# Designing and creating Blockchain applications with Hyperledger

## Step 1: Learn Design Thinking

[IBM Design Thinking Field Guide](https://www.ibm.com/blogs/bluemix/2016/12/ibm-design-thinking-field-guide/)

## Step 2: Go through IBM Blockchain Use Cases

[IBM Blockchain Use Cases](https://www.ibm.com/blockchain/use-cases/)

## Step 3a: Take the IBM Blockchain on-line course

[Zero to Blockchain An IBM Redbooks course](https://www.redbooks.ibm.com/Redbooks.nsf/RedbookAbstracts/crse0401.html)

## Step 3b: Go through selected Blockchain Developer Patterns
[Blockchain Developer Patterns](https://developer.ibm.com/code/technologies/blockchain/)

## Step 4: Learn the Hyperledger Composer tool
[Hyperledger Composer Tutorial](https://hyperledger.github.io/composer/next/)

[Writing Your First Application](http://hyperledger-fabric.readthedocs.io/en/release/write_first_app.html?highlight=fabcar)

In Hyperledger Composer: save data model as a .bna file.

## Step 5: Deploy the business network to Hyperledger Fabric. 
* This requires the Hyperledger Composer chaincode to be installed on the peer,
* then the business network archive (.bna) must be sent to the peer, 
* and a new participant, identity, and associated card must be created to be the network administrator. 
* Finally, the network administrator business network card must be imported for use, 
* and the network can then be pinged to check it is responding.

[Step by step description](https://developer.ibm.com/code/patterns/decentralized-energy-hyperledger-composer/)

## Steo 6: [Deploy on the IBM Blockchain Platform](https://www.ibm.com/blockchain/platform/)

<img src="http://34b70.http.dal05.cdn.softlayer.net/broker-static/v1-ga1/img1.png"><br>
<img src="http://34b70.http.dal05.cdn.softlayer.net/broker-static/v1-ga1/img2.png"><br>
<img src="http://34b70.http.dal05.cdn.softlayer.net/broker-static/v1-ga1/img3.png"><br>
<img src="http://34b70.http.dal05.cdn.softlayer.net/broker-static/v1-ga1/img4.png"><br>

[Deploy a sample application to the IBM Blockchain Platform Get up and running with the Enterprise Membership fast](https://www.ibm.com/developerworks/cloud/library/cl-deploy-sample-application-ibm-blockchain-platform/index.html)

[Develop in a cloud sandbox IBM Blockchain Platform](https://ibm-blockchain.github.io/)

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Exercises

<a href="https://www.ibm.com/developerworks/cloud/library/cl-ibm-blockchain-101-quick-start-guide-for-developers-bluemix-trs/index.html">IBM Blockchain 101: Quick-start guide for developers. Create your first blockchain network and start coding applications</a>

## Exercise 1: Hyperledger Composer Playground Tutorial 
<img src="https://farm5.staticflickr.com/4652/39667642831_41001d8453_z.jpg" width="640" height="429" alt="Composer">
<p>
  
[Hyperledger Composer Playground Tutorial](https://composer-playground.mybluemix.net)

<p>
<a href="https://hyperledger.github.io/composer/introduction/introduction.html">Hyperledger Composer Documentation</a>
<p>
<a href="https://hyperledger.github.io/composer/reference/commands.html">Hyperledger Composer Command Line</a>
<p>
  
###  <a href="https://github.com/ibm-silvergate/netcomposer/blob/master/README.md">Hyperledger Fabric Network bootstrapping made simple for experimentation, development and testing</a>  

## Exercise 2 Decentralized energy with Hyperledger Composer
<a href="https://developer.ibm.com/code/patterns/decentralized-energy-hyperledger-composer/?ca=dw-_-DeveloperJourney-_-dwtv-Blockchain-_-topic"> Decentralized energy with Hyperledger Composer </a>
<p>
Wondering where blockchain might apply in your own life? Interested in energy, sustainability, or climate change? Try your hand at creating a basic blockchain app to interact with a decentralized energy network! The idea behind the app is a neighborhood where residents produce and sell excess solar-panel energy to residents who need it. This is an excellent example of how blockchain can begin to transform our world.   
<p>
  
## Excercise 3 Create the full marbles app
Go through the <a href="https://github.com/LennartFr/BlockchainNetwork-CompositeJourney">BlockchainNetwork-CompositeJourney</a>

## Exercise 4 [IBM Blockchain Platform](https://www.ibm.com/cloud/blockchain-platform)<p>
An enterprise-ready blockchain platform designed to accelerate the development, governance and operation of a multi-institution business network<p>  
<p>  

[ibm.biz/ibmbctechpaper](http://ibm.biz/ibmbctechpaper)

### Exercise 4.1 Setting up a Blockchain app in the IBM Container Service ready for IBM Blockchain
[Develop in a cloud sandbox IBM Blockchain Platform](https://ibm-blockchain.github.io/)

### Exercise 4.2 Setting up a Blockchain app in the IBM Cloud
<a href="https://console.bluemix.net/catalog/services/blockchain/">IBM Blockchain in the IBM Cloud</a><br>

<img src="http://34b70.http.dal05.cdn.softlayer.net/broker-static/v1-ga1/img1.png"><br>
<img src="http://34b70.http.dal05.cdn.softlayer.net/broker-static/v1-ga1/img2.png"><br>

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Resources

## [Blockchain for DUMMIES](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=XIM12354USEN)

## Zero to Bockchain
<a href="https://www.redbooks.ibm.com/Redbooks.nsf/RedbookAbstracts/crse0401.html">Zero to Blockchain</a>

## [IBM Code: Blockchain Distributed database maintaining a continuously growing list of secured records or blocks](https://developer.ibm.com/code/technologies/blockchain/)

## [Welcome to Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release/)

## [Blockchain on IBM Cloud](https://console.bluemix.net/catalog/services/blockchain/)

## [Develop in a cloud sandbox IBM Blockchain Platform](https://ibm-blockchain.github.io/)

## Node-RED and Hyperledger Composer

## [Integrate your Blockchain with anything using Hyperledger Composer and NodeRed](https://medium.com/@CazChurchUk/integrate-your-blockchain-with-anything-using-hyperledger-composer-and-nodered-4226676f7e54)






 @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
# Develop Blockchain applications on Hyperledger Fabric   

Hyperledger, an open source collaborative effort to advance cross-industry blockchain technologies, 
is hosted by The Linux Foundation®. 

Deployed in Docker images.

<img src="https://farm1.staticflickr.com/960/41055079635_d00c82c7dd_z.jpg" width="640" height="203" alt="fabric">

https://youtu.be/pr4Hb0jb0lo

https://www.hyperledger.org/projects/fabric

[Hyperledger Fabric Documentation](https://hyperledger-fabric.readthedocs.io/en/release/)

<img src="https://farm5.staticflickr.com/4494/37926120211_b7dddb090d_o.png" width="682" height="423" alt="Hyperledger Services">
<p> Permissioned<p> 

https://medium.com/@robertgreenfieldiv/hyperledger-blockchain-for-a-web-2-0-architecture-6d3c83818eb1
<p>

# Develop Blockchain applications with Hyperledger Composer

https://youtu.be/gAxK6zYrfxI

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

<img src="https://farm1.staticflickr.com/968/27085403057_c8a2ccd0cc_z.jpg" width="640" height="202" alt="composer">

https://www.hyperledger.org/projects/composer

Hyperledger Composer Modeling Language: https://hyperledger.github.io/composer/v0.16/reference/cto_language

[Composer Playground](https://composer-playground.mybluemix.net/login)


<img src="https://hyperledger.github.io/composer/v0.16/assets/img/Composer-Diagram.svg">

<img src="https://cdn-images-1.medium.com/max/800/1*q4INoHadf0wBcB_Cax93uQ.png">


<img src="https://www.ibm.com/developerworks/cloud/library/cl-integrate-data-with-hyperledger-composer-blockchain/fig1.png">

<img srec="https://cdn-images-1.medium.com/max/1600/0*mQOJAR6zZtU6esW6.png">

[Deploying Business Networks](https://hyperledger.github.io/composer/latest/business-network/bnd-deploy.html)


<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Host Blockchain applications in the IBM Cloud 

IBM Blockchain Platform is a flexible software-as-a-service offering that is delivered via the IBM Cloud. It enables network members to quickly get started developing and easily move to a collaborative environment. The platform simplifies your blockchain journey of developing, governing, and operating a network. Choose a membership plan based on your ecosystem needs. Note that you must choose the **US South** cloud region to create blockchain networks with Starter Membership Plan (Beta).

[IBM Blockchain Platform](https://console.bluemix.net/developer/blockchain/dashboard)

[IBM Blockchain Platform Service](https://console.bluemix.net/catalog/services/blockchain)

[Launch a basic IBM Blockchain network on the IBM Container Service's free plan](https://ibm-blockchain.github.io)

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband"> 


# Social networks and support

https://chat.hyperledger.org/home

