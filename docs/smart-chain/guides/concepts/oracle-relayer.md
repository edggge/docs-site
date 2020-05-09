# Oracle Relayer



The relayer is a service which monitors events on BSC, builds and broadcasts transactions to BBC. Each validator operator should maintain its own relayer service. The relayer service requires to have access to validator operator private key. All relayer service independently witness the peggy contract events, then build transactions to claim events to BBC oracle module. 

The relay process:

* Continually listen for cross chain event
* Parse the cross chain tranfer parameters from event data 
* Use this information to build an unsigned BBC oracle transaction
* Sign and broadcast transaction.