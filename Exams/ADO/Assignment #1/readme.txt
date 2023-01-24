createPageFile
- This function creates one new page in the name 'fileName' which is passed as parameter to this function by opening this file in 'w+b' mode
- Once the page is created, we intialize a page handler (SM_PageHandle) and allocate memory using calloc() method
- This function then fills this page with '/0' bytes using memset() method
- The data from buffer page is copied to the file using fwrite() method
- File is closed using fclose() and memory in the buffer is deallocated using free() method

openPageFile

- This function opens the file of 'fileName' in 'r+' mode
- Corresponding values for file handler (SM_FileHandle) are assigned
	- fileName is assigned from the parameter
	- curPagePos is set as 0
	- mgmtInfo is assigned with the opened file
	- totalNumPages is assigned with the total number of pages calculated using stat() method
- If the file is not opened, then RC_FILE_NOT_FOUND will be returned

closePageFile
- If the passed file handler parameter is NULL, then RC_FILE_HANDLE_NOT_INIT is returned
- Else the file stored in 'mgmtInfo' of the file handler is closed using fclose() method
- If the close method fails, RC_FILE_NOT_FOUND is returned

readBlock
- In this function if the file handler parameter is NULL, RC_FILE_HANDLE_NOT_INIT is returned
- If the file at 'mgmtInfo' of the file handler is NULL, RC_FILE_NOT_FOUND is returned
- If the page number is less than 0 or greater than total number of pages, RC_READ_NON_EXISTING_PAGE is returned
- Else, the cursor is moved to the start of the block in the given pageNum page using fseek() method
- If the fseek method does not return 0, RC_ERROR will be returned
- Then the file is read using fread() method and is stored in the memPage pointer poisition which is passed as a parameter
- If the fread() method does not return the total number of bytes, then RC_READ_FAILED is returned
- The pageNum value is assigned to the 'curPagePos' of the file handler