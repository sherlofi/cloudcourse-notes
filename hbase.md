# start and stop

- start hadoop first

  ```
  start-dfs.sh
  start-yarn.sh
  server20:50070
  ```

- start hbase second
  ```
  start-hbase.sh
  server20:60020
  ```

- stop hbase first
  ```
  stop-hbase.sh
  ```

- stop hadoop second
  ```
  stop-yarn.sh
  stop-dfs.sh
  ```
# hbase shell

- start shell

  ```
  hbase shell
  ```

# insert/delete/update/select

- ````
  list					//show tables
  describe ['table_name']	 //show table structure
  scan ['table_name']		//select * from table_name
  count ['table_name']		//count table
  ````

- ```
  disable ['table_name'] //to drop a table, you must disable it first
  drop ['table_name']
  ```

- ```
  scan 'Record1',{STARTROW => '33041100000776##0',ENDROW => '33041100000776##2'}
  scan 'Record1',{STARTROW => '33041100000776##14963325',ENDROW => '33041100000776##14963327'}
  ```

- ​

