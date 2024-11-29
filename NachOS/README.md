# NachOS 4.0

**Now Compatible with 64-bit Linux Machines**

This is a modified version of NachOS (Original NachOS available at https://homes.cs.washington.edu/~tom/nachos/) which has undergone various patches to make it compatible with modern Linux machines.

The original readme file has been relocated to [README.Original.md](README.Original.md)

In this project, only the `Halt()` system call from the original NachOS and our sample `PrintInt()` system call have been implemented. Attempting to use other unimplemented system calls will result in a core dump.

As of now, this project has been tested and confirmed to work on the latest LTS version of Ubuntu Linux (22.04)

*Please note that the non-LTS versions of Ubuntu (or Debian-based) have not been tested but are expected to work. However, we do not provide support for non Ubuntu LTS versions.*

# Table of Contents
- [Prerequisite](#Prerequisite)
  - [For 64-bit Ubuntu Linux](#For-64-bit-Ubuntu-Linux)
  - [For 32-bit Ubuntu Linux](#For-32-bit-Ubuntu-Linux)
  - [Download Project](#Download-Project)
  - [Install Cross-Compiler for NachOS](#Install-Cross-Compiler-for-NachOS)
- [Building NachOS](#Building-NachOS)
- [Testing NachOS](#Testing-NachOS)
- [Make Usage](#Make-Usage)
- [NachOS Usage](#NachOS-Usage)
- [Debug Flag](#Debug-Flag)
- [Adding User Program](#Adding-User-Program)
- [References](#References)

# Prerequisite

### For 64-bit Ubuntu Linux

Enable i386 architecture first

```shell
$ sudo dpkg --add-architecture i386 
```

Preform system upgrade

```shell
$ sudo apt update; sudo apt dist-upgrade
```

Install the dependency (csh/git/compiler)

```shell
$ sudo apt install csh ed git build-essential gcc-multilib g++-multilib gdb gdb-multiarch
```

### For 32-bit Ubuntu Linux

Preform system upgrade

```shell
$ sudo apt update; sudo apt dist-upgrade
```

Install the dependency (csh/git/compiler)

```shell
$ sudo apt install csh ed git build-essential gdb
```

### Download Project

Clone the project repository

```shell
$ git clone https://github.com/wynn1212/NachOS
```

### Install Cross-Compiler for NachOS

Navigate to the `NachOS` directory, then copy the cross-compiler to the system directory

```shell
$ cd NachOS
NachOS$ sudo cp -r usr /
```

# Building NachOS

Navigate to the `code` directory in `NachOS`, then run `make` to build NachOS

```shell
NachOS$ cd code
NachOS/code$ make
```

**Note 1:** Whenever you make modifications to the source code, it is essential to rebuild the entire NachOS system.

**Note 2:** If your modifications are limited to the test directory, you can simply execute `make` within the test directory to build your program. However, if you have made changes to system calls or other core components, it is still necessary to rebuild the complete NachOS system.

# Testing NachOS

After a successful build, you should find the `nachos` executable in the `NachOS/code/userprog/` directory and your `test1` program in the `NachOS/code/test/` directory.

To run `test1` in NachOS, execute the following command:

```shell
NachOS/code$ ./userprog/nachos -e ./test/test1
```

*Please note that you should be inside the `NachOS/code` directory. Otherwise, you should specify the actual location accordingly.*

If you see this output, it indicates that you have successfully run `test1` in NachOS.

```shell
NachOS/code$ ./userprog/nachos -e ./test/test1
Total threads number is 1
Thread ./test/test1 is executing.
Print integer:9
Print integer:8
Print integer:7
Print integer:6
return value:0
No threads ready or runnable, and no pending interrupts.
Assuming the program completed.
Machine halting!

Ticks: total 200, idle 66, system 40, user 94
Disk I/O: reads 0, writes 0
Console I/O: reads 0, writes 0
Paging: faults 0
Network I/O: packets received 0, sent 0
NachOS/code$
```

# Make Usage

See [documents/Make_Usage.md](documents/Make_Usage.md)

# NachOS Usage

See [documents/NachOS_Usage.md](documents/NachOS_Usage.md)

# Debug Flag

See [documents/Debug_Flag.md](documents/Debug_Flag.md)

# Adding User Program

See [documents/Adding_User_Program.md](documents/Adding_User_Program.md)

# References

- https://homes.cs.washington.edu/~tom/nachos/ - Original NachOS 4.0 source code and documents.
- [GitHub - connlabtw/NachOS2020](https://github.com/connlabtw/NachOS2020) - This repository originated as a fork and includes the `PrintInt()` system call implementation. 
- https://blog.csdn.net/Aloneingchild/article/details/115339992 - A guide that provides a solution for building NachOS on 64-bit Linux systems.
- [GitHub - Yan-Hau/NachOS](https://github.com/Yan-Hau/NachOS/tree/master#readme) - Another solution for building NachOS on 64-bit Linux systems. This repository includes information about the required dependency packages for NachOS.
  - If you want to run NachOS on Docker or WSL2, you can follow the provided guide.
  - If you're interested in learning how to use gdb (GNU Debugger) with Visual Studio Code for NachOS development, there's also a guide available.
  - **Please be aware that this repository uses NachOS 4.1, which has a different source code structure compared to our NachOS 4.0. Additionally, it does not have the `PrintInt()` system call implemented, which means you'll need to implement the `PrintInt()` system call yourself if you choose to use this version.**
