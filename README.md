# duplicate-file-finder
This is a python script to find duplicate files in a directory structure.

Files are searched in 3 ways to get optimal performance:

1. Compare by file size only
2. Compare by md5-hash value

After the whole directory structure is searched, duplicate files are displayed. With the default settings the top 10 duplicate values (those with the most duplicate files) are displayed, but that can be changed by an argument (-top).

## Usage:
	usage: duplicatefilefinder.py [-h] [-a | -top X] [--hidden] [--empty] [--fast]
        	                      directory
	
	Module for traversing a directory structure, finding duplicate FILES and displaying them, but does NOT delete them.
	
	positional arguments:
	  directory   the directory which should be checked for duplicate FILES
	
	optional arguments:
	  -h, --help  show this help message and exit
	  -a          display all duplicate FILES. equal to -top 0
	  -top X      set the amount of displayed duplicates. If 0 is given, all
	              results will be displayed. default=10
	  --hidden    check hidden FILES and directories too
	  --empty     check empty FILES too
	  --fast      Searches very fast for only for the top X duplicates. The fast
	              check may return less than the top X, even if they would exist.
	              Remarks: the --fast option is useless when -a is given.

##EXAMPLES:
    (1) duplicatefilefinder.py ~/Downloads
        Description: Searches the Downloads directory for duplicate FILES and displays the top 10.

    (2) duplicatefilefinder.py ~/Downloads -top 3
        Description: Searches duplicates, but only displays the top 3 most duplicates

    (3) duplicatefilefinder.py ~/Downloads -top 3 --fast 
        Description: Searches for the top 3 duplicates. May eventually get less than 3 results, even if they would exist.

    (4) duplicatefilefinder.py ~/Downloads -a
        Description: Searches duplicates and displays ALL results

    (5) duplicatefilefinder.py ~/Downloads --hidden --empty
        Description: Searches duplicates and also include hidden or empty FILES


##Sample Output:
	duplicatefilefinder.py . --empty --hidden
	(By File Size) 160 Files checked, 50 duplicates found (66 duplicate files) 
	(By File Hash) 66 Files checked, 3 duplicates found (6 duplicate files) 
	
	(1) Found 2 duplicate files (size: 16 Bytes) in ./test/:
	 1: copy of testfile
	 2: testfile
	
	(2) Found 2 duplicate files (size: 41 Bytes) in ./.git/:
	 1: ORIG_HEAD
	 2: refs/tags/v1.1
	
	(3) Found 2 duplicate files (size: 41 Bytes) in ./.git/refs/:
	 1: heads/master
	 2: remotes/origin/master
	
	Found 3 duplicates (6 duplicate files total)

