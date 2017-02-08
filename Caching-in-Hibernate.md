##Caching
* Reduce the repetitive effort. 

###Cache in Database
* Db access is costly operation.
* Intention is to minimize database access without compromising on functionality.
* Caching provide fast access to some piece of data.
* Hibernate Caching is trying to minimize access of database without compromising on functionality.

###Two types of Hibernate Caching are there
* Primary
* Secondary

###Primary Level Cache
* Enabled by default
* Works in session scope. This means, if we are trying to access same entity in same session - hibernate returns the same reference rather than querying database.
* If you are trying to load same entity in same session, due to first level caching the second query will not access database.
* Across different session, we won't see Primary caching in action.

###Second Level Cache 
* Primary Caching is not available across different session.
* But, same entity is usually accessed across session. To minimize db access, secondary caching functionality kicks in.

Primary Level cache is accessed prior to Secondary Level Cache

###How Secondary Level Cache Works ?
1. Whenever we are trying to load an entity, first check happens to first level cache.
2. Only if data is not present there in first level, lookup happens in second level cache.
3. If second level cache has cached entity, it is returned as a result of load method.
4. Before returning the entity, bring data from second level cache to first level cache.
5. If entity is not found in first level or second level cache, no option but to access database.
6. Entity is bought to both the caches before returning the load method after database access. 

###Imp Notes
7. Changes to database directly has no way to update second level cache.
8. Based on Cache Config XML, timeouts will decide life of cache


###ehCache - Popular Secondary Level Cache
1. Terracota ehCache is popular open source
2. It can be used as standalone second level cache.
3. This can be configured for clustering

###Configuration of ehCache
1. Configure Hibernate for Second Level Cache
2. Specify second level cache

###Configuring entity classes
1. @Cache enables an entity for caching
2. @Cache(usage=CacheConcurrencyStrategy.*)
   Caching strategies are as follows :-  

   none - No Caching will happen

   read-only - If application is read only & not modify, read only cache will be used

   read-write - caching support read write operations

   nonstrict-read-write - Occational need to update data, fast & optimized for minimal write operation

   transactional - Concurrent caches where both reading & writing entities are aware of the changes, eg JBoss TreeCache

###Dependencies
     <dependency>
       <groupId>org.hibernate</groupId>
       <artifactId>hibernate-core</artifactId>
       <version>4.3.5.Final</version>
     </dependency>
     
     <dependency>
       <groupId>mysql</groupId>
       <artifactId>mysql-connector-java</artifactId>
       <version>5.0.5</version>
     </dependency>

    <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-ehcache</artifactId>
      <version>4.3.5.Final</version>
    </dependency>

    <dependency>
      <groupId>net.sf.ehcache</groupId>
      <artifactId>ehcache-core</artifactId>
      <version>2.6.9</version>
    </dependency>   

##Steps to integrate EhCache to Hibernate Project
* Enable ehCache into hibernate.cfg.xml

>     <property name="hibernate.cache.region.factory_class">org.hibernate.cache.ehcache.EhCacheRegionFactory</property>
>     <property name="hibernate.cache.use_second_level_cache">true</property>
>     <property name="hibernate.cache.use_query_cache">true</property>
>     <property name="net.sf.ehcache.configurationResourceName">ehcache.xml</property>

* Provide ehCache.xml for secondary level cache configuration
* Add secondary caching annotations in Entity classes 

###Cache configuration File
    
    <?xml version="1.0" encoding="UTF-8"?>
        <ehcache xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:noNamespaceSchemaLocation="ehcache.xsd" updateCheck="true"
	monitoring="autodetect" dynamicConfig="true">

	<diskStore path="java.io.tmpdir/ehcache" />

	<defaultCache maxEntriesLocalHeap="10000" eternal="false"
		timeToIdleSeconds="120" timeToLiveSeconds="120" diskSpoolBufferSizeMB="30"
		maxEntriesLocalDisk="10000000" diskExpiryThreadIntervalSeconds="120"
		memoryStoreEvictionPolicy="LRU" statistics="true">
		<persistence strategy="localTempSwap" />
	</defaultCache>

* Configure the default Caching settings 
* timeToIdleSeconds - Time in seconds if till which a memory in cache is not 
                            accessed, considered idle.
* diskSpoolBufferSizeMB - Memory in MB reserved by default for cache
* memoryStoreEvictionPolicy - strategy for evicting(removing) data from cache 
* LRU - Least Recently Used, The data on cache that was least recently used is 
                            perfect candidate for cleanup.
* The amount of data that is present in cache is limited.

	<cache name="student" maxEntriesLocalHeap="10000" eternal="false"
		timeToIdleSeconds="5" timeToLiveSeconds="10">
		<persistence strategy="localTempSwap" />
	</cache>

	<cache name="org.hibernate.cache.internal.StandardQueryCache"
		maxEntriesLocalHeap="5" eternal="false" timeToLiveSeconds="120">
		<persistence strategy="localTempSwap" />
	</cache>

	<cache name="org.hibernate.cache.spi.UpdateTimestampsCache"
		maxEntriesLocalHeap="5000" eternal="true">
		<persistence strategy="localTempSwap" />
	</cache>
    </ehcache>


