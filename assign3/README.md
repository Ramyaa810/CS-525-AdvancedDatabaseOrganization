# Manual to run the record manager program #

### To run the record manager program in linux server execute the below commands in order ###

Navigate to assign3 folder and execute below commands

$ make                                                                                                                                                                        

$ ./recordmanager

### What is this repository for? ###

* This repository contains C program code files required to insert records, delete records, update records, and scan through the records in a table
* Version 1
* Repository contains, C program files, C test cases, C header files, output files, make file and ReadMe instrcution manual.

### Project Members ###

* Ramya Krishnan(rkrishnan1@hawk.iit.edu)
* Jason Scott(jscott30@hawk.iit.edu)
* Darek Nowak(dnowak2@hawk.iit.edu)

### Functions Implemented ###

#### Optional Extensions ####
1. Tombstones is implemented using deleteFlag. Prefix will be added to the record post deletion
2. deserializeSchema and deserializeRecord functions are implemented to deserialize the schema objet and the token string respectively.

#####Schema *deserializeSchema(char *schemaData)#####
#####Record *deserializeRecord(char *deserialize_record_str, Schema *schema)#####

##### extern RC initRecordManager (void *mgmtData) #####
1. Memory is allocated and the record manager is initialized.
2. Returns RC_OK once initialized

##### extern RC shutdownRecordManager () #####
1. Shutdown the record manager 
2. Returns RC_OK once completed

##### extern RC createTable (char *name, Schema *schema) #####
1. Method creates table
2. Created page file and stores the schema info
3. Takes name and schema of the table as input
4. Returns the RC value based on the operation performed

##### extern RC openTable (RM_TableData *rel, char *name) #####
1. Method opens the created table
2. takes table data as input and the name
3. Returns the RC code based on the operation performed
4. If the table is opened sucessfully, retuns RC_OK

##### extern RC closeTable (RM_TableData *rel) #####
1. Method closes the table once all the operations are performed
2. Takes table data as input
3. Returns the RC code based on the operation performed
4. If the table is closed sucessfully, retuns RC_OK

##### extern RC deleteTable (char *name) #####
1. Method deletes the table once all the operations are performed
2. Takes table name as input
3. Returns the RC code based on the operation performed
4. If the table is deleted sucessfully, retuns RC_OK

##### extern int getNumTuples (RM_TableData *rel) #####
1. Method gets the table tuple value
2. Takes table data as input
3. Returns the tuple value as integer

##### extern RC insertRecord (RM_TableData *rel, Record *record) #####
1. Method inserts records into thetable once created
2. Takes table data and record info as input
3. Returns the RC code based on the operation performed
4. If the record is inserted sucessfully, retuns RC_OK

##### extern RC deleteRecord (RM_TableData *rel, RID id) #####
1. Method deletes records into the table once created
2. Takes table data and record id as input
3. Returns the RC code based on the operation performed
4. If the record is deleted sucessfully, retuns RC_OK

##### extern RC updateRecord (RM_TableData *rel, Record *record) #####
1. Method updates records into the table once created
2. Takes table data and record info as input
3. Returns the RC code based on the operation performed
4. If the record is updated sucessfully, retuns RC_OK

##### extern RC getRecord (RM_TableData *rel, RID id, Record *record) #####
1. Method gets records from the table once inserted
2. Takes table data and record info and rid as input
3. Returns the RC code based on the operation performed
4. If the record is retrieved sucessfully, retuns RC_OK

##### extern int getRecordSize (Schema *schema) #####
1. Method gets records size from the schema once created
2. Takes schema data as input
3. Returns record size as integer

##### extern Schema *createSchema (int numAttr, char **attrNames, DataType *dataTypes, int *typeLength, int keySize, int *keys) #####
1. Method gets inputs required to create schema
2. Takes schema data as input
3. Returns created schema object 

##### extern RC freeSchema (Schema *schema) #####
1. Method frees the schema once all the operations performed
2. Takes schema data as input
3. Returns the RC code based on the operation performed
4. If the record is retrieved sucessfully, retuns RC_OK

### Contribution guidelines ###

* table and manager,handling records in a table,dealing with schemas - Ramya Krishnan
* dealing with records and attribute values - Jason Scott
* Scans - Darek Nowak


