# 📖 get_next_line

The `get_next_line` project is one of three exercice of the second circle.

Gnl is a project where you create a function that reads a file descriptor line by line.

The goal is to handle dynamic memory allocation and buffer management efficiently
while respecting file boundaries and returning one line at a time, including the
newline character if present.

This project reinforces knowledge of reading from files, using static variables, and managing memory safely in C.

![](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

## 🛠️ Function prototype

Name of the function : get_next_line.

Prototype : `char*    get_next_line( int fd );`

### ⚙️ Usage

Step 1:

Run in your shell environment :
```bash
git clone https://github.com/jotudela/get_next_line.git && cd get_next_line
```

---

Step 2:

Create a file with content inside :
```bash
echo  "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Porttitor massa id neque aliquam vestibulum morbi blandit cursus. Vitae et leo duis ut diam quam nulla. Et malesuada fames ac turpis egestas maecenas. Arcu bibendum at varius vel. Urna nec tincidunt praesent semper. Ut ornare lectus sit amet est placerat in egestas erat. Eu lobortis elementum nibh tellus. Et molestie ac feugiat sed lectus vestibulum mattis ullamcorper velit. Id venenatis a condimentum vitae sapien. Enim neque volutpat ac tincidunt vitae semper quis lectus. Hac habitasse platea dictumst quisque sagittis purus. Pretium fusce id velit ut tortor pretium viverra suspendisse potenti. Ac turpis egestas integer eget aliquet nibh praesent." > lorem_ipsum
```

Step 3:

Create a simple `main.c` function :
```c
#include "get_next_line.h"
#include <stdio.h>
#include <string.h>
#include <fcntl.h>

int main(void)
{
  // opens up a file descriptor from which get_next_line will access and read the file
  int fd = open("lorem_ipsum", O_RDONLY);

  // The buffer in which we'll store the current line
  char *master_buffer;

  while (1)
  {
    // Actual reading from get_next_line
    master_buffer = get_next_line(fd);

   // When get_next_line returns NULL, it means we reached the EOF
    if (master_buffer == NULL)
	    break;

    // prints the current line from `fd`
    printf("%s", master_buffer);

    free(master_buffer); // Even though you have 512TB of RAM
  }

    // Security check
  if (master_buffer)
	  free(master_buffer);

  // don't forget to close the opened fd from `read` function
  close (fd);
}
```

---

Step 4:

Once the file is builded, compile it with this :
```bash
gcc -Wall -Wextra -Werror main.c get_next_line.c get_next_line_utils.c -o program
```

---

Step 5:

Run with this :
```bash
./program
```

And your terminal will print the content of lorem_ipsum file readed.

My final grade :

![](imgs/125_percent.png)

![](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

## 🤝 Contribution
Contributions are open, make a pull request or open an issue 🚀
