# Debug and implementation of binary directory tress (BDT), directory tree (DT) and file tree (FT) abstract objects

A tree is a linked data structure that represents a hierarchical organization of data. There is exactly one node with no incoming links, which we call the root of the tree. There is a unique path from the root to every other node in the tree. Every other node in the tree has exactly one incoming link (from its parent). A node with no outgoing links (and thus no children) is called a leaf of the tree.

For example, the Linux file system is structured as a tree. There is one root directory, technically with no name but colloquially called / , that serves as the ancestor of all other directories in the directory hierarchy. Both directories and files may be leaves of the tree, and nodes that are not leaves may have either or both of directories and files as children. Each node in the hierarchy has a canonical name (absolute path or full path) derived from an enumeration of the nodes visited traveling from the root directory to that node, delimited by slashes. As an example, /usr/bin/ls describes all four nodes visited in reaching the ls binary executable: the unnamed directory that is the tree's root, the usr directory that is a child of the root, the bin directory that is a child of usr, and the ls file leaf that is a child of bin.

In this repository, I worked on three different tree data structures, each of which represents an increasingly complicated file system hierarchy, eventually achieving the full description from the first paragraph above:

Binary Directory Tree (BDT): A BDT is a hierarchy of directories in which each node may have at most 2 children.

Directory Tree (DT): A DT is a generalization of a BDT in which each directory may have an arbitrary number of children.

File Tree (FT): An FT is an extension of a DT in which leaves may now represent either an empty directory or a file.As a simplification to avoid complications with empty strings within paths, in all three implementations, neither the root nor any other directory will be unnamed, and no superfluous delimiters will be permitted within path names. Thus no absolute path may have multiple slash delimiters in a row (e.g., a/b/c would be a valid full path and /a//b/c would not be, unlike in Linux).

The deployments are: 
1. Binary Directory implementation debug
   Input information: 
   - Object files for several faulty Binary Directory Tree implementations, as well as for a correct implementation. 
   - The source codes for a minimalist BDT client that exhibits behavioral or memory management errors when run after building with any of the faulty implementations. 
   
   Task: locate the bugs in the faulty implementations by debugging the client program using gdb.

2. Directory Tree implementation debug
   Input information: 
   - Object files for several faulty Directory Tree implementations, as well as the source for a correct implementation and a minimalist DT client. The object files were not configured to facilitate stepping through the code in those files while debugging in gdb.
   - The API functions that mutate the data structure were augmented at the leading and trailing edges to include calls to an internal validation module. 
   
   Task: flesh out the invariant tests in that internal validation module to verify the validity of the data structure's representation such that it correctly identifies the invalid state of the data structure and terminates the program for each faulty implementation.
   
3. File Tree interface implement
   Input information: 
   - An expanded API that is appropriate for hierarchies that contain both directories and files.
   
   Task: Implement the File Tree interface, using the Directory Tree implementation from Part 2 as a jumping off point. Along the way, need to reassess the program design and modularity decisions made for the DT implementation if they are no longer the best choices for the FT requirements.

This project is a COS217 assignment. https://www.cs.princeton.edu/courses/archive/spr23/cos217/asgts/04dftrees/

A complete code is a private repository and it is available upon request only for employment purpose.
