# WinAPI-ThreadClass
A WinAPI Thread class which uses the CreateThread function for class members.

## Example
### main.cpp
```c++
#include <iostream>
#include <string>

#include "Thread.h"

class HelloWorld
{
public:
    DWORD print ()
    {
        std::cout << "Hello World!" << std::endl;
        return 0;
    }
};
int main(void)
{
    // Random object with DWORD method (void)
    HelloWorld world;
    // thread should call print method of world.
    Thread<HelloWorld> thread(&world, &HelloWorld::print);
    if (thread.start())
        std::cout << "Thread start()" << std::endl;
    thread.join(); // wait for thread
    return 0;
}
```
Compilation tested with VS2008.

### Output
```
Thread start();
Hello Wordl!
```
