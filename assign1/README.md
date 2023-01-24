# Manual to run the storage manager program #

### To run the storage manager program in linux server execute the below commands in order ###

$ make <br />
$ ./storagemanager

### What is this repository for? ###

* This repository contains C program code files required to create, open, close, write and read the files.
* Version 1
* Repository contains, C program files, C test cases, C header files, output files, make file and ReadMe instrcution manual.

### Project Members ###

* Ramya Krishnan(rkrishnan1@hawk.iit.edu)
* Jason Scott(jscott30@hawk.iit.edu)
* Darek Nowak(dnowak2@hawk.iit.edu)

### Functions Implemented ###

#### Manipulating page file functions ####

##### void initStorageManager(void) <br />
1. Initializes the stroage manager <br />

##### RC createPageFile (char *fileName) <br />
1. Opens file  <br />
2. Append an empty block <br />
3. Write the empty block <br />

##### RC openPageFile(char *fileName, SM_FileHandle *fHandle) <br />
1. Opens existing file, else returns not found error <br />
2. Initializes attributes of file <br />

##### RC closePageFile (SM_FileHandle *fHandle) <br />
1. Opens a file <br />
2. If exists, it closes or destroys <br />
3. If issues with 1 or 2, it displays errors <br />

##### RC destroyPageFile (char *fileName) <br />
1. Destoys page file <br />

#### Read functions ####

##### RC readBlock(int pageNum, SM_FileHandle* fHandle, SM_PageHandle memPage)  <br />
1. Check validity of fHandle, if it is not initialized then return error(RC_FILE_HANDLE_NOT_INIT) <br />
2. Check the input page number, if its zero or not valid number, return error(RC_FILE_HANDLE_NOT_INIT) <br />
3. Check validity of memPage, if it is NULL then return error(RC_FILE_NOT_FOUND) <br />
4. If all the above conditions are passed, fseek is used to move the curser to the beginning of the blck in respective page <br />
5. If fseek read is not zero'th position then return rror(RC_Error) <br />
6. If the above condition satisfied, then fread will read the file and store in memPage as a pointer position <br />
7. Retrun error if fread is failed(RC_READ_Failed) <br />
8. If not, set the current position in fhandle and return success, RC_OK <br />

##### int getBlockPos(SM_FileHandle* fHandle)  <br /> 
1. Check if fHandle is initialized, if not return error RC_FILE_HANDLE_NOT_INIT <br />
2. Check if MgMtInfo is valid, if not return error RC_FILE_NOT_FOUND <br />
3. If above conditions satisfied, then return current page position <br />

##### RC readFirstBlock(SM_FileHandle* fHandle, SM_PageHandle memPage)  <br />
1. Check if fHandle is initialized, if not return error RC_FILE_HANDLE_NOT_INIT <br />
2. Check if MgMtInfo is valid, if not return error RC_FILE_NOT_FOUND <br />
3. If above conditions satisfied, pass 0 to the readBlock method and return the result <br />
4. Return RC_OK if everything is successful <br />

##### RC readPreviousBlock(SM_FileHandle* fHandle, SM_PageHandle memPage) <br />
1. Get the current position from fHandle using getBlockPos function <br />
2. Subtract one from the current position value and pass it to the readblock funtion to read the previous block <br />
3. Return RC_OK if everything is successful <br />

##### RC readCurrentBlock(SM_FileHandle* fHandle, SM_PageHandle memPage) <br />
1. Get the current position from fHandle using getBlockPos function <br />
2. Pass it to the readblock funtion to read the current block <br />
3. Return RC_OK if everything is successful <br />

##### readNextBlock(SM_FileHandle* fHandle, SM_PageHandle memPage) <br />
1. Get the current position from fHandle using getBlockPos function <br />
2. Add one from the current position value and pass it to the readblock funtion to read the next block <br />
3. Return RC_OK if everything is successful <br />

##### RC readLastBlock(SM_FileHandle* fHandle, SM_PageHandle memPage) <br />
1. Get the total number of pages from fHandle <br />
2. Subtract one from the number of pages value and pass it to the readblock funtion to read the last block <br />
3. Return RC_OK if everything is successful <br />

#### Write functions ####

##### RC writeBlock (int pageNum , SM_FileHandle * fHandle , SM_PageHandle memPage )  <br />
1. Opens file. <br />
2. Fseeks given the offset from memPage to find the absolute location of where we will write. <br />
3. Writes using fwrite. <br />

##### RC writeCurrentBlock (SM_FileHandle * fHandle , SM_PageHandle memPage )  <br />
1. Opens file. <br />
2. Write using fwrite. <br />

##### RC appendEmptyBlock (SM_FileHandle * fHandle)  <br />
1. Create new page via a new char* to newBlock <br />
2. Iterate through the page until you fill it with 4096 0 chars. <br />
3. Update the metadata by incrementing totalNumPages. <br />
4. Use the writeBlock function to write a new file with the given newBlock. <br />

##### RC ensureCapacity (int numberOfPages , SM_FileHandle * fHandle )  <br />
1. Check to see if there is a difference in pages with memory and disk. <br />
2. If there are more pages in memory, then write to the disk 1 empty file. <br />

### Contribution guidelines ###

* Read block - Ramya Krishnan
* Open, Close(Manipulation) - Jason Scott
* Write block - Darek Nowak


