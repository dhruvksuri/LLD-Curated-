ConsistentHashRing - 
  
   1. Attributes
    
   final SortedMap<Integer, Server> hashRing;
   
   int numberOfReplicas;
   
   HashFunction hashFunction;
   
   
   2. How to Add servers to HashRing
    
    //get hashkey from server ip with the replica number
    
    String hashKey = server.getIpAddress() + ":" + i;

    //pass hashkey to hashFunction to extract hashedValue
    
    Integer hashedValue = hashFunction.createHash(hashKey);
    
   
   3. How to get server for a given Key

    // Compute the hash of key, if hash ring contains direct value then return server.
    
    Integer hash = hashFunction.createHash(key);
    
    // If not, find first server on hashRing with hash > key.
    
    // If no server found, then choose smallest server hashkey which is first server from Tree set
    
    
   4.  How to Remove servers from HashRing
    
    // get hashkey from server ip with the replica number
    // Reindex stores value to next server
    
    Server serverToBeDeleted = hashRing.get(hashedValue);

    //remove the server at the hashkey in the Sorted Dictionary
    
    this.hashRing.remove(hashedValue);
    
    // Reindex Key value pairs of server to be deleted
    
    for (Entry<String, String> entry : serverToBeDeleted.getEntries()) {
        put(entry.getKey(), entry.getValue());
     }
     
   
   //   createHash
   
   public Integer createHash(String input) { <br/>
        int hash = 7;<br/>
        for (int i = 0; i < input.length(); i++) {<br/>
            hash = hash * 31 + input.charAt(i);<br/>
        }<br/>
        return hash;
    }<br/>
