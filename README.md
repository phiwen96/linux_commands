# linux_commands

Type the following dpkg command to see installed compilers and version:
  $ dpkg --list | grep compiler
  
Use the apt-get command to install compiler under Debian / Ubuntu Linux:
  $ sudo apt-get install clang-10
  
System wide C++ change on Ubuntu:

  sudo apt-get install clang
  sudo update-alternatives --config c++
