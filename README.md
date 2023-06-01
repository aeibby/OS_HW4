# OS_HW4
Operating System HW4

## Team Members:
21900673 Jung Eunchong  
21900805 Yewon Hong  
21900842 Abigail Yong  

## 1. Project Description & List of functions definitions
Our goal for this project was to design  and  construct **findeq**, a multithreaded program that finds groups of equal files. 
Using findeq, the users can count how much memory space is  wasted by redundant files and identify chances of saving up  storage spaces by removing redundant files.  Findeq must use multithreading to parallelize the search to find as many identical  files as possible with given computation time and resource. 

```
handleSIGINT
```
Signal handler function for the SIGINT signal when a user presses CTRL+C.  
This function is also executed when the program recieves the SIGINT signal and performs necessary cleanup operations before exiting.

```
appendFL(fileList **head, long num, char *str)
```
Appends a new file to the file list.  
This function adds a new file (specified by its size and path) to the file list.

```
freeFL(fileList **head, fileList **first)
```
Frees the memory occupied by the file list.  
This function frees the memory allocated for the file list and its associated files.

```
appendData(Data **head, char *str)
```
Appends a new data item to the data list.  
This function adds a new data item (specified by its path) to the data list.

```
data2File(Data *head, char *name)
```
Writes the data list to a file.  
This function writes the contents of the data list to a file specified by the given name.

```
scanDir(const char *path, int minimum_size)
```
Scans a directory for files matching the minimum size criteria.  
This function recursively scans the specified directory for files and adds files with a size greater than or equal to the minimum size to the file list.

```
compareFile(fileList *fl, Data *data)
```
Compares files in the file list for similarity and updates the data list accordingly.  
This function compares files in the file list to identify duplicates and updates the data list with the paths of similar files.

```
travel(void *arg)
```
Function executed by worker threads to process subtasks.  
This function is responsible for calling the compareFile function on the given subtask to compare files and update the data list.

```
worker(void *arg)
```
Worker thread function.  
This function is executed by worker threads to continuously retrieve and process subtasks using the get_subtask and travel functions.


## 2. Usage & Process to run
```
./findeq ./File
```
findeq takes inputs as command-line arguments. The usage of findeq is as follows: 
Basically,  findeq  receives  a path  to  a  target  directory  DIR. 

```
./findeq -m=1200 ./File
```
Ignores all files whose size is less than NUM bytes 
from the search. The default value is 1024. 

```
./findeq -o=new ./File
```
Produces  to  the  output  to  FILE.  By default,  the 
output must be printed to the standard output. 
```
./findeq -o=new2 -m=1200 ./File
```

## 3. Issues & Limitations
We seem to encounter a big performance lag in the single-threading and multi-threading. It seems to take alot more of time in the multi-thread as compared to a single-thread.

## 4. Contact Information
21900673 Jung Eunchong (21900673@handong.ac.kr)  
21900805 Yewon Hong (21900805@handong.ac.kr)  
21900842 Abigail Yong (abby@handong.ac.kr)  
