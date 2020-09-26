# linux_commands

Type the following dpkg command to see installed compilers and version:
  $ dpkg --list | grep compiler
  
Use the apt-get command to install compiler under Debian / Ubuntu Linux:
  $ sudo apt-get install clang-10
  
System wide C++ change on Ubuntu:

  sudo apt-get install clang
  sudo update-alternatives --config c++


Locating iostream in Clang++: fatal error: 'iostream' file not found:
  Firstly find your version (path): 
    ls /usr/include/c++/
    
  Output:
    8
  Then:
    export CPLUS_INCLUDE_PATH=/usr/include/c++/8:/usr/include/x86_64-linux-gnu/c++/8
