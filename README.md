# Table of Contents

- [Table of Contents](#table-of-contents)
- [Portable Index-Allocated File System](#portable-index-allocated-file-system)
- [Filesystem Specifications](#filesystem-specifications)
- [Commands](#commands)
- [Installation and Running](#installation-and-running)
- [Feedback](#feedback)
- [Copyright](#copyright)

# Portable Index-Allocated File System

This is a user-space portable index-allocated file system. It provides 2<sup>26</sup>  bytes of drive space in a disk image and allows users to create the filesystem image, list the files currently in the file system, add files, remove files, and save the filesystem. Files persist in the file system image when the program exits.

# Filesystem Specifications

- Uses an index allocation scheme.
- Filesystem block size is 1024 bytes.
- Consists of 65536 blocks.
- Supports files up to 2<sup>20</sup> bytes in size.
- Supports up to 256 files.
- Supports filenames of up to 64 characters.
- Only alphanumeric filenames are supported with “.”. There is no restriction on the number of characters before or after the “.”. Files without a “.” are also supported.
- The directory structure is a single-level hierarchy with no subdirectories.
- Directory is stored in blocks 0-18.
- Block 19 is allocated for the free inode map.
- Blocks 20-276 are allocated for inodes.
- Block 277 is allocated for the free block map.
- Blocks 278-65535 are used for file data.
- Files are not required to be contiguous. Blocks do not have to be sequential.


# Commands

|Command|Usage|Description|
|-------|-----|-----------|
|insert|```insert <filename>```|Copy the file into the filesystem image|
|retrieve|```retrieve <filename>```|Retrieve the file from the filesystem image and place it in the current working directory|
|retrieve|```retrieve <filename> <newfilename>```|Retrieve the file from the filesystem image and place it in the current working directory using the new filename|
|read|```read <filename> <starting byte> <number of bytes>```|Print \<number of bytes\> bytes from the file, in hexadecimal, starting at \<starting byte\>
|delete|```delete <filename>```|Delete the file from the filesystem image|
|undel|```undelete <filename>```|Undelete the file from the filesystem image|
|list|```list [-h] [-a]```|List the files in the filesystem image. If the ```-h``` parameter is given it will also list hidden files. If the ```-a``` parameter is provided the attributes will also be listed with the file and displayed as an 8-bit binary value.|
|df|```df```|Display the amount of disk space left in the filesystem image|
|open|```open <filename>```|Open a filesystem image|
|close|```close```|Close the opened filesystem image|
|createfs|```createfs <filename>```|Creates a new filesystem image|
|savefs|```savefs```|Write the currently opened filesystem to its file|
|attrib|```attrib [+attribute] [-attribute] <filename>```|Set or remove the attribute for the file|
|encrypt|```encrypt <filename> <cipher>```|XOR encrypt the file using the given cipher.  The cipher is limited to a 1-byte value|
|decrypt|```encrypt <filename> <cipher>```|XOR decrypt the file using the given cipher.  The cipher is limited to a 1-byte value|
|quit|```quit```|Quit the application|


# Installation and Running

Ensure you have GCC installed on your machine. You can check this by running `gcc --version` in your terminal. If you don't have GCC installed, you can install it by following the instructions on the [GCC official website](https://gcc.gnu.org/install/index.html).

To compile the program, navigate to the directory containing the source file, then run the following command: `gcc -Wall -Werror --std=c99 <filename.c>`

After compilation, you can run the program with the following command: `./a.out`. When the program is ready to accept input, it will print out a prompt of `mfs>`.

After running the program, you can use the available commands as described in the [Commands](#commands) section.

# Feedback
If you encounter any bugs or have suggestions for improvements, feel free to open an issue.

# Copyright

Copyright © 2023. All rights reserved.

This software is provided for educational purposes only. It is prohibited to use this Portable Index-Allocated File System, for any college assignment or personal use. Unauthorized distribution, modification or commercial usage is strictly forbidden. Please respect the rights of the author.