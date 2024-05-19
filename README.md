# Week 4 - [Memory](https://cs50.harvard.edu/x/2024/weeks/4/)

* Lecture

<iframe width="679" height="382" src="https://www.youtube.com/embed/F9-yqoS7b8w" title="CS50x 2024 - Lecture 4 - Memory" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

----

</br>

* TED-ed talk: How computer memory works - Kanawat Senanan

<iframe width="560" height="315" src="https://www.youtube.com/embed/p3q5zWCw8J4?si=0LuMH9F-PbcBKYIf" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---

## Pixels

* Pixels
A pixel is the smallest addressable element in a dot matrix to describe amount of color of R, G, B. It's also used for describing resolution in display device.

----

### RGB values 
<img src ="https://hackmd.io/_uploads/ry_7vmR-C.png" width = 35% style="display: block; margin: auto"> 
* A pixel color can be represented by amount of Red, Green, Blue.

----

* In  this convention, 255 is the largest value, and the 0 is the smallest. (0 means color is black. 
* There're another discription for color in hexadecimal : [#6699FF](#1/1). This numeral system is called Hexadecimal numeral system.

----

### Hexadecimal numeral system 
* Hexadecimal
In base-10 numeral system counting from 0, 1, 2, 3, 4, 5, 6, 7, 8, 9,..., and every ten counts adds to 1 carry.
In hexadecimal system, counting starts from : 
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F, ..., and every 16th counts adds to 1 carry.

----

* Why use it?
    In computer science, it's very often to use stream of bits (or pattern) to record data. since these long patterns are very hard for human to handle.
    
    The length of bits pattern in computer are usually 4's multiple, one hexadecimal character can represent a 4 bits pattern. For simplification,  we take advantage of hexadecimal notation (or other numeral system) to solve this problem. 

----

* Hexadecimal and Bits pattern: 0~7 (base- 10)
    
| Bits pattern | Hexadecimal |
|:------------:|:-----------:|
|     0000     |      0      |
|     0001     |      1      |
|     0010     |      2      |
|     0011     |      3      |
|     0100     |      4      |
|     0101     |      5      |
|     0110     |      6      |
|     0111     |      7      |

----

* Hexadecimal and Bits pattern: 8~15 (base- 10)

| Bits pattern | Hexadecimal |
|:------------:|:-----------:|
|     1000     |      8      |
|     1001     |      9      |
|     1010     |      A      |
|     1011     |      B      |
|     1100     |      C      |
|     1101     |      D      |
|     1110     |      E      |
|     1111     |      F      |


----

## Memory allocation 

## Static and Dynamic Memory Allocation
1. Static Memory Allocation: 
1-1. The allocation of memory performs at the compile time.
1-2. Static memory allots memory from the stack.
2. Dynamic Memory Allocation: 
2-1. The allocation of memory performs at execution or run time.
2-2. Dynamic memory allots from the heap.

----

### Pointer & Arrays
        
"a" is an array containing five integers. While "pa" is a pointer pointing to array "a".

<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; padding: 10px 5px 5px 10px;">
<img src = "https://hackmd.io/_uploads/SyKIKR4xC.png" alt = "drawing" width = 45% style = "display:block; margin: auto">
</div>    


----

```C 
// pa is a pointer pointing to an integer
int *pa;

// pa points to the first element of a
// It's also equivalent to pa = a;
pa = &a[0];

// points to the next element in a: a[1]
pa + 1

// get the value at location a[1]
*(pa +1)
```

----

* Practice

```c 
int x = 1, y = 2, z[10];
int *ip; // ip is a pointer to int
ip = &x; // ip now points to x's address
y = *ip; // go to ip's address and get the value, y is now 1
*ip = 0; // x is now 0
ip = &z[0]; // ip now points to z[0]
```

----


### Pointer & Address
<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; padding: 10px 5px 5px 10px;">
<img src = "https://hackmd.io/_uploads/Sk4kXA4gR.png" alt = "drawing" width= 50% style="display: block; margin: auto"> 
</div>
<p>In the computer's sequential memory, p is a pointer pointing to char c. p stores c's address.</p> 
<p>itself takes some memory cell to store address value. Address value may use hexadecimal representaion, i.e. 0x12A, ..., etc.</p>


----

* One way to dynamically allocate memory is to use malloc(). 
    * datatype *variableName = malloc(sizeof(datatype)  of units)
* int *var = malloc ( sizeof( int) * 3)   
* Allots 4 * 3 = 12 bytes memory to a variable named var.
* Remember, once you run to the end of your code, before exiting the program, use free() to free memory allocated, otherwise, it'll cause memory leakage/loss. 
 

---

### System stack memory

![image](https://hackmd.io/_uploads/ry23Lamx0.png)

 
* A main function includes local variables, pointer, and return address.
<img src = "https://hackmd.io/_uploads/H1UglAmgR.png" alt = "drawing" width= 40% style="display: block; margin: 50px 100px 50px 150px;">


----

* When the program executes to the line and calling the function f1, the system stack's top frame becomes f1.
</br>
<img src = "https://hackmd.io/_uploads/Sy3xeC7g0.png" alt = "drawing" width= 40% style="display: block; margin: 50px 100px 50px 150px;">
</br>

----

f1 is composed of a local variable, pointer, and return address. The pointer points to the function block called f1. The return address in f1 records the address where the line in the main should f1 return values.
</br>
<img src = "https://hackmd.io/_uploads/r1Q-l07gR.png" alt = "drawing" width= 80% style="display: block; margin: 50px 100px 50px 150px;">

---

## File I/O
* Open a file in read/write mode:
Create a buffer to read/write file once a time, and set a condition that if read to the end of the file then stop.


```c [1-8]
// Allocate a file memory to create an output file
//and in read or write mode
FILE *output = fopen(filename/path, "r/w")

// Create a buffer to read input files one unit at a time
// A buffer: "header",  has a datatype of uint8_t 
// (8 bits unsigned integer)
uint8_t header[HEADER_SIZE];
```


----

```c 
// Read from input file:
// read from the buffer: "header", which  unit size is HEADER_SIZE. Read 1 unit of data.
fread(header, HEADER_SIZE, 1, input)

// Write to output file:
// Write 1 unit size of "HEADER_SIZE" to output
fwrite(header, HEADER_SIZE, 1, output)

// Close files after executing
fclose(input)
fclose(output)
```

---

## Memory leaks check: [Valgrind](https://valgrind.org/docs/manual/mc-manual.html#mc-manual.options)
Sometimes it won't show a memory error when you compile the program. So using the valgrind command to check memory leaks is very important.  

----

<p>Here's an example using valgrind from week 4 p-set: recover.</p>

![image](https://hackmd.io/_uploads/SkA3hAEg0.png)

----

<p>1. In HEAP SUMMARY</p> 

* <p>" 472 bytes in 1 block are still reachable in loss record 1 of 1."</p> 
  <p>It means 1 block of memory wasn't freed before the program exits. The cause happened at line 64 using fopen().</p>       

----

<p>2. In LEAK SUMMARY</p>

* <p>definitely lost</p>
    This means no pointer to the block can be found. The block is classified as "lost".

----

* <p>inderectly lost</p>
    This means the block is lost not because there are no pointer points to it, but rather because all the block points to it themselves are lost. (You may think of a binary tree, whose root node is lost, although its children still have some pointers pointing to them(the root), children's nodes are still indirectly lost.)

----

* <p>possibly lost</p>
    This means that a chain of one or more pointers to the block has been found, but at least one of the pointers is an interior pointer. To correctly free memory, it's safer to use a pointer points to the "start" of the block of memory.
    (interior pointer: a pointer points to somewhere in the middle of a block of memory.)

----

* <p>suppressed</p>
    The suppressed message means that Valgrind hid some messages not to show you, which are either positive/negative issues within the system library.

---

### Overflow
1. A ***heap overflow*** is when you touch areas of memory you are ***not*** supposed to (where may already allocated to another variable,..., etc.).
2. A ***stack overflow*** happens when you call too many functions and your computer doesn't have enough memory.
3. Both 1 and 2 are considered buffer overflow which means the buffer exceeds its storage capacity.

---

## Psets
### [Filter-less](https://cs50.harvard.edu/x/2024/psets/4/filter/less/)
Before starting to solve problems, understand the whole structure first. Files needed in this problem:
1. An image folder called "images", containing some .bmp files as input file
2. filter.c: The main file to transform input .bmp to filtered .bmp image.
3. helpers.c: This file is the TO-DO file in this problem, you'll need to complete the 4 filters function.

----

4. A Makefile: This tells the compiler how to compile the filter. c, using all the needed files.

5. <bmp.h>: It's a self-defined header file to define BMP-related data types based on Microsoft's own. Pic below defines the struct datatype: RGBTRIPLE, it stores R, G, and B values in the single pixel.

<img src = "https://hackmd.io/_uploads/HJd1tqQxC.png" alt = "drawing" width= 40% style="display: block; margin: auto">  

----

* When you zoom in on a picture very closely, you may find an image is represented with a grid of pixels. A BMP image, i.e. a map formed by bits. A BMP image supports 1-, 4-, 8-, 16-, 24-, and 32-bit colors. In this practice problem, we use a 24-bit color format.

<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; margin: 50px 120px;">
    
![rgbpixel](https://hackmd.io/_uploads/S1_PhDmeA.png)
    
</div>
* A color image is fomed by Red, Green, Blue and using 8 bits to represent each color.
    
---- 

![courtyard](https://hackmd.io/_uploads/B19IDwXxC.png)

Original picture


----

#### Gray scale
A black-and-white image means there must not be too much Red, or too much Green and too much blue color, these 3 have to be equivalent amounts in a pixel. In this sense, we can get the grayscale value by calculating the average value of R, G, and B and setting the value to the new R, G, and B values.
        
----
        
```c
// demo:
BYTE x = round((image[i][j].rgbBlue + image[i][j].rgbGreen + 
image[i][j].rgbRed)/3.0);

RGBTRIPLE newrgbBlue = x;
RGBTRIPLE newrgbGreen = x;
RGBTRIPLE newrgbRed = x;
```

----

<img src = "https://hackmd.io/_uploads/H1sNeOXl0.png" alt = "grayscaleimg" width= 100% style="display: block; margin: auto">

Result of grayscale image


----

#### Sepia
* Sepia filter has its formula to calculate each R, G and B value:  
    1. ***sepiaRed*** = .393 * originalRed + .769 * originalGreen + .189 * originalBlue
    2. ***sepiaGreen*** = .349 * originalRed + .686 * originalGreen + .168 * originalBlue
    3. ***sepiaBlue*** = .272 * originalRed + .534 * originalGreen + .131 * originalBlue
    4. (newRed, newGreen, newBlue) = (sepiaRed, sepiaGreen, sepiaBlue)

----

* While calculating these values, keep in mind that we use 8 bits to record one color (i.e. 256 color depth: from 0 to 255). If the result is beyond 255, you should set it to 255.

----

<img src = "https://hackmd.io/_uploads/SJkhXuXgC.png" alt = "grayscaleimg" width= 100% style="display: block; margin: auto">

Result of sepia filter image
    
----

####  Reflect
* In the reflecting filter, the image flips horizontally, you may think of reversing one row of image once at a time, and so on the other rows.    

* Image row [ i ]: 
<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; margin: 10px 120px;">
    
<img src = "https://hackmd.io/_uploads/S1X1j_7xC.png" alt = "drawing" width= 60% style="display: block; margin: auto">

</div>
    
----

Reversed horizontally image row [ i ]
<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; margin: 10px 120px;">
    
<img src = "https://hackmd.io/_uploads/SkoWid7xA.png" alt = "drawing" width= 60% style="display: block; margin: auto">   

</div>    
    
----

Swap pixels from the start index 0 to the middle index of the row. Remember swap examples in the class, there're many ways to swap value: passing by values or passing by copies.

----

![image](https://hackmd.io/_uploads/rJuM2_mlA.png)
* *a is the pointer of the row image on the left side, while *b is the pointer of the row image on the right side. Also declared a temporary pointer points to a's address. 
* Re-assign pointer points to the address of *b points at, and vice versa, re-assign *b points to address the tmp, which records pointer a.
----

<img src = "https://hackmd.io/_uploads/SJmjTO7xC.png" alt = "grayscaleimg" width= 100% style="display: block; margin: auto">

Result of reflected image
    
----    
    
#### Blur
Blur filter has many types, in this problem, boxed-blur filter is being used.
    Boxed blur takes adjacent 9 pixels (along with itself) average as its new R, G, B value.

<img src = "https://hackmd.io/_uploads/SJUYqtmlC.png" alt = "drawing" width= 70% style="display: block; margin: 50px 120px;">

----

* Pixels in different positions of the image: 
1. For pixel "**6**", in the middle of the image:
( 1 + 2 + 3 + 5 + 6 + 7 + 9 + 10 + 11 ) / 9
3. For **8**'s position, which is at the edge of the image: Its new blue value after blurred is: 
( 3 + 4 + 7 + 8 + 11 + 12 ) / 6
4. For **1**'s position, which is at the corner of the image: Its new blue value after blurred is: 
( 1 + 2 + 5 + 6 ) / 4 

----

* Use a 3x3 mask to obtain the pixels' location to calculate the blurred value. The center element mask[1][1] is the pixel being calculated.
* Mask[i][j] records the corresponding R, G, B of the pixel 
<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; margin: 10px 80px;">

<img src = "https://hackmd.io/_uploads/Bk1al9mg0.png" alt = "drawing" width= 50% style="display: block; margin: auto">

</div>


----


* Mask[i][j] records the corresponding position of the image 

<div style="background-color: rgba(255, 255, 255, 0.9); color: #1A237E; margin: 10px 80px;">

<img src = "https://hackmd.io/_uploads/rkkEZcXlC.png" alt = "drawing" width= 50% style="display: block; margin: auto">

</div>


----

![Part0](https://hackmd.io/_uploads/ryVbLcQgR.png)
Copy the original image so that we won't mess up all the data while doing the calculation

----

![Part1-1](https://hackmd.io/_uploads/ryjtSqml0.png)
![Part1-2](https://hackmd.io/_uploads/SkyLBqmlA.png)
create mask[ i ][ j ] to record all the pixel data needed for the calculation.


----

![Part2-1](https://hackmd.io/_uploads/ByLsScmgA.png)
![Part2-2](https://hackmd.io/_uploads/SJ_nrc7lC.png)
Define mask row and col size


----

![image](https://hackmd.io/_uploads/S1uGvcQl0.png)
Add up boxBlue, boxRed, boxGreen and set them as new R, G, B

----

<img src = "https://hackmd.io/_uploads/Hytcw9XlR.png" alt = "grayscaleimg" width= 100% style="display: block; margin: auto">

Result of blurred image

---

### [Filter-more](https://cs50.harvard.edu/x/2024/psets/4/filter/more/)
* Edge detection filter 
1. [Sobel operator](https://en.wikipedia.org/wiki/Sobel_operator)
Following Gx and Gy are Sobel operators. These 3x3 kernels calculate the approximations of the derivatives for the image's x-direction and y-direction
                   
<div style="text-align": center>   
    
|   |Gx |   |    |Gy  |    |                       
|:-:|:-:|:-:|:--:|:--:|:--:|       
|-1 |0  |1  | -1 | -2 | -1 |                      
|-2 |0  |2  |0   |0   |0   |                     
|-1 |0  |1  |1   |2   |1   |
    
</div>
  
  
----


* For an image pixel: image[ i ][ j ], find its adjacent 9 pixels (including itself), and conduct convolution with Gx and Gy. When calculating all 9 pixels's convolutions, get the new image[ i ][ j ] R, G, B value by calculating the square root of Gx_Red^2 + Gy_Red^2, Gx_Green^2 + Gy_Green^2 and Gx_Blue^2 + Gy_Blue^2.
* Be aware that the "^" operator does not calculate the square value in C, it means Bitwise XOR, you may directly time itself twice like Gx * Gx, or use pow(Gx, 2) instead.


----

Here's my attempt: 
```c [1-17]
void edges(int height, int width, RGBTRIPLE image[height][width])
{
// input parameters are: image height, image width, and the whole image 
// carries Red,  Green, and Blue color information, stored in RGBTRIPLE data type in a pixel.

// Block 1: Copy the original image 
// to conduct convolution per pixel 
// and not influence other original pixels

RGBTRIPLE copy[height][width];
for (int p = 0; p < height; p++)
{
    for (int q = 0; q < width; q++)
    {
        copy[p][q] = image[p][q];
    }
}
```

----

```c [1-14]
// Block 2: Create a matrix containing pixels needed to perform the calculation
// to calculate new R, G, and B values: edge_Red, edge_Green, edge_Blue.
// (There's no necessity to use a pointer creating matrix, it's just personal practice in here.)

RGBTRIPLE(*mpt)[3][3] = malloc(sizeof(RGBTRIPLE) * 9);
(*mpt)[0][0] = copy[i - 1][j - 1];
(*mpt)[0][1] = copy[i - 1][j];
(*mpt)[0][2] = copy[i - 1][j + 1];
(*mpt)[1][0] = copy[i][j - 1];
(*mpt)[1][1] = copy[i][j];
(*mpt)[1][2] = copy[i][j + 1];
(*mpt)[2][0] = copy[i + 1][j - 1];
(*mpt)[2][1] = copy[i + 1][j];
(*mpt)[2][2] = copy[i + 1][j + 1];
```

----


```c []
// Block 3: Set constraints if the image pixel is at the corners or edge.

RGBTRIPLE *edge = malloc(sizeof(RGBTRIPLE));
edge->rgbtRed = 0;
edge->rgbtGreen = 0;
edge->rgbtBlue = 0;
if (i == 0){
    
    (*mpt)[0][0] = *edge;            
    (*mpt)[0][1] = *edge;
    (*mpt)[0][2] = *edge;
}

if (i == height - 1){
    
    (*mpt)[2][0] = *edge;
    (*mpt)[2][1] = *edge;
    (*mpt)[2][2] = *edge;
}

if (j == 0){
    
    (*mpt)[0][0] = *edge;
    (*mpt)[1][0] = *edge;
    (*mpt)[2][0] = *edge;
}

if (j == width - 1){
    
    (*mpt)[0][2] = *edge;
    (*mpt)[1][2] = *edge;
    (*mpt)[2][2] = *edge;
}

```

----


```c
// Block 4: Calculate convolution
RGBTRIPLE *m00pt = &(*mpt)[0][0];
int *Gxpt = &Gx[0][0];
int *Gypt = &Gy[0][0];
int sumx_edgeB = 0;
int sumy_edgeB = 0;
int sumx_edgeG = 0;
int sumy_edgeG = 0;
int sumx_edgeR = 0;
int sumy_edgeR = 0;

for (int n = 0; n < 9; n++)
{
    sumx_edgeB += ((m00pt + n)->rgbtBlue) * (*(Gxpt + n));
    sumy_edgeB += ((m00pt + n)->rgbtBlue) * (*(Gypt + n));
    sumx_edgeG += ((m00pt + n)->rgbtGreen) * (*(Gxpt + n));
    sumy_edgeG += ((m00pt + n)->rgbtGreen) * (*(Gypt + n));
    sumx_edgeR += ((m00pt + n)->rgbtRed) * (*(Gxpt + n));
    sumy_edgeR += ((m00pt + n)->rgbtRed) * (*(Gypt + n));
}
```

----

```c
// Block 5: Obtain the new R, G, and B values

double R = round(sqrt(pow(sumx_edgeR, 2) + pow(sumy_edgeR, 2)));
double G = round(sqrt(pow(sumx_edgeG, 2) + pow(sumy_edgeG, 2)));
double B = round(sqrt(pow(sumx_edgeB, 2) + pow(sumy_edgeB, 2)));
// * Remember to free memory before the program exits

free(*mpt);

```  

----

<img src = "https://hackmd.io/_uploads/Sk0u2HsfR.png" alt = "grayscaleimg" width= 100% style="display: block; margin: auto">

Result of Edge filter image

---

## Additional knowledge
* Gray-scale formula:
In filter-less p-set's description of implement grayscale, it suggests taking average of red, green and blue values to compuete shade of grey for the new pixel. There's another way to express gray scale formula. In NTSC^[1] is represented as:
0.299 * Red + 0.587 * Green + 0.114 * blue
    
--- 

## Reference Material
* [Color space and Color gamut](https://www.agneovo.com/tw/insight/everything-you-need-to-know-about-graphic-design-monitors#dci-p-3)
* [Benq-What is color gamut?](https://www.benq.com/en-us/knowledge-center/knowledge/color-gamut-monitor.html)

---
^[1]: NTSC (National Television Standard Commitee)
