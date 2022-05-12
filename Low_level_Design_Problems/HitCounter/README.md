Instant ts;

Long sec = ts.getEpochSecond()

The getEpochSecond() method of Instant class is used to return the number of seconds from the Java epoch of 1970-01-01T00:00:00Z

1. Use ConcuurentHashMap where keys would be seconds and value would be counter 

    List<Map<Long, AtomicInteger>> ds = new LinkedList<>();
    
2. Index of list would be based on date. or another option could be

    Map<Date, Map<Long, AtomicInteger>> ds = new ConcurrentHashMap<>();
