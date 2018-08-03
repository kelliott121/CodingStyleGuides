1. **General Rules**

    1. **Line Width**

        1. **Rules:**

            1. The length of all lines in a program shall be limited to a maximum of 150 characters.

        2. **Reasoning:**  Code shall be easily visible on a screen without the need of line-wrapping and scroll bars.  150 characters is the maximum number that fit on 1600px width monitors. It also allows for varying Visual Studio layouts.

        3. **Enforcement:**  Violations of this rule shall be detected by CppLint during the automated builds.  An option is also available in Visual Assist under VAssistX->Options->Display "called Display indicator after column" that allows for a dotted line in the editor to show the character limit.

    2. **Braces**

        4. **Rules:**

            2. Braces shall be indented to the same level as their corresponding code block.

            3. Braces shall exist on a separate line from any code.

            4. Braces shall always be used.

        5. **Examples:  **

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>if (true)
    {
    ...
    }</td>
    <td>if (true)
{
    ...
}</td>
  </tr>
  <tr>
    <td>if (true){
    ...
}</td>
    <td></td>
  </tr>
  <tr>
    <td>if (true){...}</td>
    <td></td>
  </tr>
  <tr>
    <td>if (true)
    ...</td>
    <td></td>
  </tr>
</table>


        6. **Reasoning:**  Readability

        7. **Enforcement:**  Artistic Style

    3. **Forbidden C Constructs**

        8. **Rules:**

            5. auto, register, goto, break, and continue keywords shall never be used.

                1. An exception for break may be used in the case of switch statements.

            6. Every function shall only have a single return statement.

        9. **Reasoning:**  auto and register are both compiler shortcuts which are obsoleted by careful coding practices.  goto, break, and continue provide jump statements that can cause confusion with regards to program flow.

        10. **Enforcement:**  PC-Lint "-deprecate" option & Code Review

    4. **Important C Constructs**

        11. **Rules:**

            7. Volatile variables shall only be added as an absolute necessity.  A volatile variable shall have a corresponding comment explaining why it is necessary.

        12. **Reasoning:**  Volatile variables can cause performance degradation.

        13. **Enforcement:**  Code Review

2. **Files**

    5. **Naming Conventions**

        14. **Rules:**

            8. All file names shall use camelCase.

                2. **Exception**: If an acronym occurs at the end of the file name, it should be written using all caps.  Acronyms anywhere else in the name should be treated as one word and should therefore use camelCase.

            9. Each file in a code module shall have the same name (for .h and .c files).

            10. The purpose and function of a file shall be obvious from it’s name.

            11. File names shall not exceed 31 characters.

            12. File names shall not start with a number and shall not contain special characters or operators (+, -, /, etc.).

        15. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>this_file.c</td>
    <td>thisFile.c</td>
  </tr>
  <tr>
    <td>ThisFile.c</td>
    <td></td>
  </tr>
  <tr>
    <td>THIS_FILE.c</td>
    <td></td>
  </tr>
  <tr>
    <td>digitalIOPrivate.h</td>
    <td>digitalIoPrivate.h</td>
  </tr>
  <tr>
    <td>CRCFunctions.c</td>
    <td>crcFunctions.c</td>
  </tr>
  <tr>
    <td>configureGpio.c</td>
    <td>configureGPIO.c</td>
  </tr>
</table>


        16. **Reasoning:**  Readability

        17. **Enforcement:**  Code Review

    6. **Content**

        18. **Rules:**

            13. Code modules shall be broken into three parts with a public header file (moduleName.h), code file (moduleName.c), and private header file (moduleNamePrivate.h).

            14. Contents of a file shall consist of logically related functions and data structures.

            15. Global and private variables should each be grouped as a global structure and private structure with no other variables external to the structure unless there is no other option.

            16. Global prototypes, constants, structures, typedefs, enums and variables shall be declared in the header file.

            17. Local prototypes, constants, structures, typedefs, enums and variables shall be declared in the code file.

            18. Functions shall be defined in the code file.

            19. Inline functions shall be defined in the timing critical code file.

        19. **Reasoning:**  Code Clarity

        20. **Enforcement:**  Code Review

    7. **Header Inclusion**

        21. **Rules:**

            20. Angle brackets shall only be used for system/library headers files.

            21. Quotes shall be used for user include files.

            22. Only absolute paths shall be used.  Rather than using relative paths and the ".." operator, new directories should be added to the include paths.

            23. Include guards shall use #if defined and #if !defined rather than #ifdef and #ifndef

            24. The include guard definition shall be of the format FILENAME_H_INCLUDED.

            25. All header files must have an include guard starting on line 1 and encompassing the entire contents of the file.

            26. A header file must include any header files that are necessary for its compilation, but should not include any other header files.

            27. A module shall include its private header file first, after which the remaining includes shall be sorted alphabetically by line.  This can easily be accomplished by selecting the lines and using the **Sort Selected Lines** option from the **VAssistX/Tools** menu.

        22. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>#include "time.h"</td>
    <td>#include <time.h></td>
  </tr>
  <tr>
    <td>#include <servoLoop.h></td>
    <td>#include "servoLoop.h"</td>
  </tr>
  <tr>
    <td>#include "../hal/C6674.h"</td>
    <td>//Add "hal" parent to include path
#include "hal/C6674.h"</td>
  </tr>
  <tr>
    <td>#ifndef _FILENAME_H_
#define _FILENAME_H_
…
#endif</td>
    <td>#if !defined(FILENAME_H_INCLUDED)
#define FILENAME_H_INCLUDED
…
#endif   // FILENAME_H_INCLUDED</td>
  </tr>
</table>


        23. **Reasoning:**  Code Clarity & Readability

        24. **Enforcement:**  Code Review

3. **Comments**

    8. **Acceptable Types**

        25. **Rules:**

            28. Only // style comments shall be used.

        26. **Reasoning:**  Readability

        27. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>/* This is a bad comment */</td>
    <td>// This is a good comment.</td>
  </tr>
</table>


        28. **Enforcement:**  PC-Lint message 1904 can check for /*

    9. **Content**

        29. **Rules:**

            29. Comments shall be clear and concise.

            30. Comments shall use full sentences with proper grammar, spelling, and punctuation.

            31. Comments shall only document non-obvious sections of code.

            32. Commented out code shall never be checked into source control.

            33. Issues referenced in comments shall be in the following format: "// CTRL-XXXXX: Text here“.

        30. **Reasoning:**  Code Clarity

        31. **Enforcement:**  Code Review

    10. **Formatting**

        32. **Rules:**

            34. Comments shall be indented to the same level as the code that is being explained.

            35. Inline comments shall not be used except #endif on header files (see section d).

            36. A space shall be included between the comment syntax and the beginning of the comment text.

        33. **Reasoning:**  Readability

        34. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>{
// Calling foo
    foo();
}</td>
    <td>{
    // Foo is being called because <reason>.
    foo();
}</td>
  </tr>
  <tr>
    <td>foo();  // Calling foo
</td>
    <td>// Foo is being called because <reason>.
foo();</td>
  </tr>
  <tr>
    <td>//This is a bad comment.</td>
    <td>// This is a good comment.</td>
  </tr>
</table>


        35. **Enforcement:**  Artistic Style & CppLint

    11. **#endif Inline Comments**

        36. **Rules:**

            37. An inline comment must be used by the #endif at the end of all header files.

            38. The comment must only be FILENAME_H_INCLUDED.

        37. **Reasoning:** In CTRL-31742, MDT and HDT agreed to use this style convention for consistency when automatically generating files.

        38. **Example:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>#if !defined(FILENAME_H_INCLUDED)
#define FILENAME_H_INCLUDED
…
#endif</td>
    <td>#if !defined(FILENAME_H_INCLUDED)
#define FILENAME_H_INCLUDED
…
#endif   // FILENAME_H_INCLUDED</td>
  </tr>
</table>


        39. **Enforcement:** Code Review

4. **White Space**

    12. **Horizontal Spacing**

        40. **Rules:**

            39. All program flow statements shall be followed by a space (if, else, while, for, switch, and return).

            40. All two argument operators (assignment, binary, arithmetic, and comparison) shall be preceded and followed by a space.

            41. Semicolons in for statement shall be followed by a space.

            42. Unary, structure member, function argument list, and line termination semicolons shall not be preceded or followed by a space.

            43. There shall be no spaces directly following an opening parenthesis or bracket or preceding a closing parenthesis or bracket.

            44. Commas shall be followed by a space.

            45. The parenthesis-terminated argument lists in function declarations, definitions, and calls shall never be preceded by a space.

            46. The bracket-terminated lists in array declarations, assignments, and accesses shall never be preceded by a space.

            47. The pointer (*) and reference (&) operators shall be adjacent to declared variable with no whitespace in between.

            48. The address operator (&) shall be adjacent to the expression being operated on with no whitespace in between.

            49. There shall be no unnecessary, trailing whitespace following lines of code.

        41. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>foo();
while(var)
{
    ...
}
bar();</td>
    <td>foo();

while(var)
{
    ...
}

bar();</td>
  </tr>
  <tr>
    <td>c=a+b;</td>
    <td>c = a + b;</td>
  </tr>
  <tr>
    <td>for (a=0;a<10;a++)
{
    ...
}</td>
    <td>for (a = 0; a < 10; a++)
{
    ...
}</td>
  </tr>
  <tr>
    <td>foo() ; </td>
    <td>foo();</td>
  </tr>
  <tr>
    <td>foo( bar1, bar2 );</td>
    <td>foo(bar1, bar2);</td>
  </tr>
  <tr>
    <td>foo(bar1,bar2,bar3);</td>
    <td>foo(bar1, bar2, bar3);</td>
  </tr>
  <tr>
    <td>int* pointer;</td>
    <td>int *pointer;</td>
  </tr>
  <tr>
    <td>int * pointer;</td>
    <td></td>
  </tr>
  <tr>
    <td>c = & address;</td>
    <td>c = &address;</td>
  </tr>
</table>


        42. **Reasoning:**  Readability

        43. **Enforcement:**  Artistic Style

    13. **Vertical Spacing**

        44. **Rules:**

            50. All code blocks ({...}) on the same indentation level shall be surrounded by at least one blank line.

            51. Function prototype sections shall be followed by at least one blank line.  The prototypes themselves can be directly adjacent.

            52. Variable declaration sections shall be followed by at least one blank line.

            53. Each source file shall have a new-line at the end.

            54. Natural blocks of code shall be surrounded by at least one blank line.

            55. All sections of a file (#includes, variables, functions, etc.) shall be separated by at least one blank line.

        45. **Examples:**

<table>
  <tr>
    <td>#include <time.h>



int32_t a;
int32_t b;



void foo(void)
{
    int c;
    int d;

    bar();

    return;
}


void bar(void)
{
    ...
}</td>
  </tr>
</table>


        46. **Reasoning:**  Readability

        47. **Enforcement:**  Code Review

    14. **Alignment**

        48. **Rules:**

            56. Multiple consecutive assignment statements shall have the assignment operator aligned.

            57. For #define directives, the first character in a constant name and first character in the definition shall be aligned.

        49. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>int32_t a = 0;
uint32_t b = 1;
float32_t a = 2;</td>
    <td>int32_t a   = 0;
uint32_t b  = 1;
float32_t a = 2;</td>
  </tr>
  <tr>
    <td>#define A 1
#define BB 2
#define CCC 3</td>
    <td>#define A   1
#define BB  2
#define CCC 3</td>
  </tr>
</table>


        50. **Reasoning:**  Readability

        51. **Enforcement:**  Code Review

    15. **Indentation**

        52. **Rules:**

            58. Tabs shall only be used for indentation.  All alignment after that shall use spaces.

            59. The case in a switch statement shall be indented to the same offset as the switch keyword.  The break shall be indented one level further.

            60. Each new scope ({...}) shall be incremented an additional tab.

            61. Preprocessor directives shall not be indented.

        53. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>switch (a)
{
    case 1:
    …
    break;
}</td>
    <td>switch (a)
{
case 1:
    …
    break;
}</td>
  </tr>
  <tr>
    <td>if (a)
{
while (b)
{
...
}
}</td>
    <td>if (a)
{
    while (b)
    {
        ...
    }
}</td>
  </tr>
  <tr>
    <td>if (a)
{
#if defined(A)
    while (b)
    {
    #if defined(B)
        …
    #endif
    }
#endif
}</td>
    <td>if (a)
{
#if defined(A)
    while (b)
    {
#if defined(B)
        …
#endif
    }
#endif
}</td>
  </tr>
</table>


        54. **Reasoning:**  Readability

        55. **Enforcement:**  Artistic Style

5. **Data Types**

    16. **Boolean**

        56. **Rules:**

            62. Variables that represent a boolean value (i.e., true or false) shall use the bool type.

            63. Only variables of type bool or the result of a boolean operator (i.e., <, >, <=, >=, ==, !=, !, &&, or ||) can be used in a context that expects a boolean value (e.g., an if or while statement).

            64. Variables of type bool should not be compared to other quantities (e.g., true or false) via the equality operators (i.e., == or !=).

        57. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>uint32_t additionalInfo;
if (additionalInfo)
...</td>
    <td>uint32_t additionalInfo;
if (additionalInfo != 0)
...</td>
  </tr>
  <tr>
    <td>uint32_t enable;
if (enable)
...</td>
    <td>bool enable;
if (enable)
...</td>
  </tr>
  <tr>
    <td>bool Homing;
if (Homing == true)
...</td>
    <td>bool Homing;
if (Homing)
...</td>
  </tr>
</table>


        58. **Reasoning:** Code Clarity

        59. **Enforcement:** Strong type checking via the PC-Lint -strong argument.

    17. **Integers**

        60. **Rules:**

            65. Only fixed-width integer types shall be used (int8_t, uint16_t, etc.).

            66. All signed and unsigned integer widths shall be no smaller than 32-bits (to ensure speed-optimized code) unless variable size is of explicit concern (flashConfig structure, bitfields, SMC/FPGA interface, etc.).

            67. Unsigned integer types are preferred over signed integer types. Signed integer types should only be used when the value being represented can be negative, and will not overflow the size of the type (the behavior of signed overflow is not defined).

            68. The use of char shall only apply to strings.

        61. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>unsigned int a;</td>
    <td>uint32_t a;</td>
  </tr>
</table>


        62. **Reasoning:**  Code Clarity.  Speed and size optimized integer widths are defined in stdint.h.  For our code/compiler, we want to use 32-bits as the smallest width to provide the fastest performance unless variable size is of explicit concern.

        63. **Enforcement:**  PC-Lint message 970

    18. **Floating Point**

        64. **Rules:**

            69. Only fixed-width floating point types shall be used (float32_t, float64_t, etc.)

        65. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>float a;</td>
    <td>float32_t a;</td>
  </tr>
  <tr>
    <td>double a;</td>
    <td>float64_t a;</td>
  </tr>
</table>


        66. **Reasoning:**  Code Clarity

        67. **Enforcement:**  PC-Lint message 970

    19. **Bitfields**

        68. **Rules:**

            70. Bitfields shall only be of the "unsigned" type.

            71. Bitfields that contain only a single bit are assumed to be a boolean value and must be used as such.

            72. All bits of a bitfield shall be defined with the unused bits being declared to fill out the minimum size of the variable.

        69. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>typedef struct
{
    unsigned a:1;
    signed b:1;
} Example_t;</td>
    <td>typedef struct
{
    unsigned a:1;
    unsigned b:1;
    unsigned :6;
} Example_t;</td>
  </tr>
</table>


        70. **Reasoning:**  Code Clarity

        71. **Enforcement:**  Code Review

    20. **Arrays**

        72. **Rules:**

            73. The count of array elements shall be obtained by using the same defined constant that was used as the dimension argument in the array declaration.

            74. The count of array elements shall be obtained by dividing the size of the array by the size of its zeroth element if a defined constant was not used as the dimension argument in the array declaration.

        73. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>

uint8_t myArray[10];

numElements = 10;</td>
    <td>#define NUM_ARRAY_ELEMENTS 10

uint8_t myArray[NUM_ARRAY_ELEMENTS];

numElements = NUM_ARRAY_ELEMENTS;</td>
  </tr>
  <tr>
    <td>uint8_t myArray[10];

numElements = sizeof(myArray);</td>
    <td>uint8_t myArray[10];

numElements = (sizeof(myArray) / sizeof(myArray[0]));</td>
  </tr>
</table>


        74. **Reasoning:**  These methods of obtaining the count of array elements will return the correct value even if the data type or length of the array are changed.

        75. **Enforcement:**  Code Review

6. **Functions**

    21. **Naming Conventions**

        76. **Rules:**

            75. Function names shall be in PascalCase for global functions and camelCase for static and inline functions.

            76. Function names shall be descriptive and without excessive abbreviation.

            77. Function arguments shall be in camelCase.

            78. Argument names shall be descriptive and without excessive abbreviation.

            79. Function names shall not exceed 31 characters.

            80. Public functions in modules should be prefixed with their module and an underscore (e.g. <ModuleName>_).

                3. All naming conventions still apply to the module name and the text after the prefix.

            81. Functions in external abstraction layers (e.g. the PAL and HAL) should be prefixed with their library name and an underscore (e.g. PAL_ and HAL_).

                4. All naming conventions still apply to the text after the library prefix.

        77. **Examples:**

<table>
  <tr>
    <td>void GlobalFunction(int32_t argOne, int32_t argTwo);
void localFunction(int32_t argOne, int32_t argTwo);</td>
  </tr>
</table>


        78. **Reasoning:**  Readability & Code Clarity

        79. **Enforcement:**  Code Review

    22. **Content**

        80. **Rules:**

            82. Empty functions shall be followed by brackets containing "// This space was intentionally left blank."

        81. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>void foo(void)
{
    
}</td>
    <td>void foo(void)
{
    // This space was intentionally left blank.
}</td>
  </tr>
</table>


        82. **Reasoning:**  Code Clarity

        83. **Enforcement:**  Code Review

    23. **Scope**

        84. **Rules:**

            83. A function’s scope shall be reduced as much as possible.

            84. If a function is only used within a module, it shall be declared static.

            85. Short functions that are only used a few times shall be declared inline.

        85. **Reasoning:**  Bug Prevention & Performance

        86. **Enforcement:**  Code Review

    24. **Size**

        87. **Rules:**

            86. No function shall exceed 100 lines of code, not including comments, braces, and whitespace.

        88. **Reasoning:  **Readability

        89. **Enforcement:  **CppLint

    25. **Prototypes**

        90. **Rules:**

            87. Prototypes shall always have named arguments.

            88. A function that takes no arguments shall have a "void" parameter list in both its prototype and definition.

        91. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>void foo(uint32_t, int32_t);
void bar();

void bar()
{
    // Do something...
}</td>
    <td>void foo(uint32_t a, int32_t b);
void bar(void);

void bar(void)
{
    // Do something...
}</td>
  </tr>
</table>


        92. **Reasoning:**  Code Clarity

        93. **Enforcement:**  PC-Lint message 955

    26. **Arguments**

        94. **Rules:**

            89. In the case of generic arguments (such as drive commands), a named variable describing the usage of the argument shall have the generic value assigned to it.

            90. When passing in an array to a function, the argument shall use empty brackets instead of a pointer.

            91. A conditional expression should never be passed into a function as an argument.

            92. The return value of a function should never be directly accessed unless the function name heavily implies a specific return value.

        95. **Examples:**

<table>
  <tr>
    <td>void SetParameter(DRIVE_COMMAND commandData, DRIVE_RESPONSE *commandResponse)
{
    uint32_t paramNumber   = commandData.argument[0]
    uint32_t paramValueLSW = commandData.argument[1]
    uint32_t paramValueMSW = commandData.argument[2]

    ...
}</td>
    <td></td>
  </tr>
  <tr>
    <td>void foo(uint32_t array[]);</td>
    <td></td>
  </tr>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>foo(X == 0);</td>
    <td>bool arg = false;

if (X == 0)
{
    arg1 = true;
}

foo(arg);</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
</table>


        96. **Reasoning:**  Code Clarity

        97. **Enforcement:**  Code Review and PC-Lint message 9132

    27. **Sorting**

        98. **Rules**:

            93. Functions shall be sorted alphabetically.

        99. **Reasoning:**  Readability

        100. **Enforcement:**  Code Review

7. **Variables**

    28. **Naming Conventions**

        101. **Rules:**

            94. Global variable names shall use PascalCase

            95. Local variable names shall use camelCase

            96. Variable names shall be descriptive and without excessive abbreviation.

            97. Variable names shall not exceed 31 characters.

        102. **Examples:**

<table>
  <tr>
    <td>int32_t GlobalVariable;
int32_t localVariable;</td>
  </tr>
</table>


        103. **Reasoning:**  Readability and Code Clarity

        104. **Enforcement:**  PC-Lint message 621

    29. **Scope**

        105. **Rules:**

            98. A variable’s scope shall be reduced as much as possible.

            99. If a variable is only used within a function, it shall be declared global to the module or locally depending on whether the value needs to be persistent.

        106. **Reasoning:**  Bug Prevention

        107. **Enforcement:**  PC-Lint message 9003

    30. **Declaration**

        108. **Rules:**

            100. Only one variable declaration shall occur on a single line.

        109. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>int32_t a, b;</td>
    <td>int32_t a
int32_t b;</td>
  </tr>
</table>


        110. **Reasoning:**  Readability

        111. **Enforcement:**  PC-Lint message 9146

    31. **Initialization**

        112. **Rules:**

            101. Initialization shall occur inline with the declaration when possible.

        113. **Reasoning:**  Code Clarity

        114. **Enforcement:**  Code Review

    32. **Sorting**

        115. **Rules:**

            102. The declaration of variables shall first occur by type (largest to smallest) and then alphabetically by name.

        116. **Reasoning:**  Readability & Performance

        117. **Enforcement:**  Code Review

8. **Expressions and Statements**

    33. **If Statements**

        118. **Rules:**

            103. Assignments shall not be made in if statements.

            104. The condition of an if statement shall only consist of boolean values or expressions.

        119. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>if ((bActive = (dwNumMappings > 0)) == TRUE)
{
    ...
}</td>
    <td>bActive = (dwNumMappings > 0);
if (bActive)
{
    ...
}</td>
  </tr>
  <tr>
    <td>int32_t i;
...
if (i)
{
    ...
} </td>
    <td>int32_t i;
...
if (i > 0)
{
    ...
}</td>
  </tr>
  <tr>
    <td></td>
    <td>bool i;
...
if (i)
{
    ...
}</td>
  </tr>
</table>


        120. **Reasoning:**  Code Clarity

        121. **Enforcement:**  PC-Lint message 9084 & 9036

    34. **Switch Statements**

        122. **Rules:**

            105. Switch statements shall have brackets around the list of cases, but no brackets for each case.

            106. All switch statements shall have default cases.

            107. The cases in a switch statement shall use enums.

                5. This won’t be entirely possible until [CTRL-28093](https://tracker.aerotech.com/browse/CTRL-28093) is completed and autogenerated constants use enums.

        123. **Examples:**

<table>
  <tr>
    <td>switch (variable)
{
    case 1:
        ...
        break;
 
    case 2:
        ...
        break;
 
    default:
        ...
        break;
}</td>
  </tr>
</table>


        124. **Reasoning:** Readability

        125. **Enforcement:** Astyle & PC-Lint message 744

    35. **Loops**

        126. **Rules:**

            108. All parameters of a for statement shall be filled out.

            109. A for statement shall only reference the variable used for loop flow control.

            110. Infinite loops shall be expressed with "while (1)"

            111. Empty loops shall be followed by brackets containing "// This space was intentionally left blank."

        127. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>for (iIndex=5,j=99;j>6; iIndex++, j--)
{
    ...
}</td>
    <td>iIndex=5;
for (j=99; j>6; j--)
{
    iIndex++
    ...
}</td>
  </tr>
  <tr>
    <td>for (;;)
{
    ...
}</td>
    <td>while (1)
{
    ...
}</td>
  </tr>
  <tr>
    <td>while (1)
{
    continue;
}</td>
    <td>while (1)
{
    // This space was intentionally left blank.
}</td>
  </tr>
</table>


        128. **Reasoning:**  Code Clarity

        129. **Enforcement:**  Code Review

    36. **Order of Operations**

        130. **Rules:**

            112. All two argument operations shall always be surrounded by parentheses to make the order of operations clear.

            113. The object of a cast shall always be a discrete expression, i.e. any operation performed on a variable being casted shall be within parentheses.

        131. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>a = b + c / d;</td>
    <td>a = (b + c) / d;</td>
  </tr>
  <tr>
    <td>a = b & c | d;</td>
    <td>a = (b & c) | d;</td>
  </tr>
  <tr>
    <td>a = b && c || d;</td>
    <td>a = (b && c) || d;</td>
  </tr>
  <tr>
    <td>(float32_t)-1.0;</td>
    <td>(float32_t)(-1.0)</td>
  </tr>
  <tr>
    <td>(uint32_t)*variable;</td>
    <td>(uint32_t)(*variable)</td>
  </tr>
</table>


        132. **Reasoning:**  Code Clarity

        133. **Enforcement:**  Code Review & PC-Lint message 9050

    37. **Inline Assembly Code**

        134. **Rules:**

            114. All embedded inline assembly code shall use the syntax "__asm()".

        135. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>asm(" NOP 4");</td>
    <td>__asm(" NOP 4");</td>
  </tr>
</table>


        136. **Reasoning:**  Using one notation adds code clarity, and TI recommends this syntax for strict ANSI code.

        137. **Enforcement:  **PC-Lint message 586

9. **Structures and Unions**

    38. **Naming Conventions**

        138. **Rules:**

            115. Member names shall be of in camelCase

        139. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>typedef struct
{
    uint32_t first_member:1;
    uint32_t SecondMember:1;
} Example_t;</td>
    <td>typedef struct
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} Example_t;</td>
  </tr>
</table>


        140. **Reasoning:**  Readability

        141. **Enforcement:**  Code Review

    39. **Formatting**

        142. **Rules:**

            116. The declaration of a typedef’d struct shall be in the form "typedef struct StructName_tag {...} StructName_t;"

        143. **Examples:**

<table>
  <tr>
    <td>typedef struct Example_tag
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} Example_t;</td>
  </tr>
</table>


        144. **Reasoning:** Code Clarity

        145. **Enforcement:** Code Review

    40. **Initialization**

        146. **Rules:**

            117. Initialization of of structures should use designated initializers.

        147. **Examples:**

<table>
  <tr>
    <td>Example = 
{
    .firstMember = 1,
    .secondMember = 2,
    .thirdMember = 3
}</td>
  </tr>
</table>


        148. **Reasoning:** Code Clarity

        149. **Enforcement:** Code Review

10. **Custom Types**

    41. **Naming Conventions**

        150. **Rules:**

            118. Type names shall be in PascalCase.

            119. Custom types shall have the suffix of "_t" at the end of the type name.

            120. Struct, enum, union tag names shall be in PascalCase.

            121. Custom struct, enum, union tags shall have the suffix of "_tag" at the end of the tag name.  These tags shall always be used (see [CTRL-31435](https://tracker.aerotech.com/browse/CTRL-31435)).

        151. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>typedef struct
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} EXAMPLE_TYPE;</td>
    <td>typedef struct Example_tag
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} Example_t;</td>
  </tr>
  <tr>
    <td>typedef struct structName_t
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} Example_t;</td>
    <td>typedef struct StructName_tag
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} Example_t;</td>
  </tr>
</table>


        152. **Reasoning:**  Readability & Code Clarity

        153. **Enforcement:**  Code Review

    42. **Allowable Types**

        154. **Rules:**

            122. A pointer of a type shall not be typedef’d to a new type.

        155. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>typedef struct
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} *PExampleType;</td>
    <td>typedef struct
{
    uint32_t firstMember:1;
    uint32_t secondMember:1;
} Example_t;</td>
  </tr>
</table>


        156. **Reasoning:**  Code Clarity

        157. **Enforcement:**  Code Review

11. **Constants**

    43. **Naming Conventions**

        158. **Rules:**

            123. All constant names should be in UNDERSCORE_CASE

            124. All static const names shall be prefixed with "STATIC_CONST_".

    44. **Const**

        159. **Rules:**

            125. Use when a constant will be used in arithmetic (i.e., the numerical value, not the name, is what is actually important).  Constant variables cannot be used for the following:

                6. Dimension argument when declaring an array

                7. Switch case labels

                8. When a constant value is needed to define a subsequent constant

            126. All constant variables shall be declared as static.

        160. **Examples:**

<table>
  <tr>
    <td>static const float64_t STATIC_CONST_PI = 3.14;</td>
  </tr>
</table>


        161. **Reasoning:**  

            127. Constant variables respect scope and are type-safe.

            128. By declaring constant variables as static, the compiler performs optimizations that result in identical instruction and memory allocation as if #define were used (i.e., constant variables are optimized out by the compiler).

            129. The prefixing of "STATIC_CONST_" is required for static analysis to suppress warnings related to defined constants that are never used within a source file.

        162. **Enforcement:**  Code Review

    45. **#define**

        163. **Rules:**  Only used when explicitly necessary in the following cases:

            130. Dimension argument when declaring an array length

            131. If a constant value is needed to define a subsequent constant

        164. **Examples:**

<table>
  <tr>
    <td>// #define necessary since this is used as dimension in array declaration
#define GALVOCAL_MAX_AXES   3</td>
  </tr>
</table>


        165. **Reasoning:**  We want to avoid this convention whenever possible, as #define does not provide type-safety or respect scope.

        166. **Enforcement:**  Code Review

    46. **Enumeration**

        167. **Rules:**

            132. Use for a list of options when a human-readable label in the code is important (i.e., we aren't as concerned with the numerical value of the constant).

            133. Enumerations are always integer types, so if a different (longer) type is required, a constant variable should be used.

            134. All enumerations should be defined as an explicit unnamed type, with corresponding variables declared as that type.

            135. Enumeration typedef’s shall only assign values to the members when the default assignments (0,1,2…) are not suitable.

            136. All assignments to enumeration variables shall consist of the enumeration member name, not a literal value.

        168. **Examples:**

<table>
  <tr>
    <td>// Abort states
typedef enum
{
	ABORT_NONE,
	ABORT_START,
	ABORT_DECEL,
	ABORT_DELAY,
	ABORT_ROUND,
	ABORT_DONE,
} AbortStates_t;

EXTERN AbortStates_t AbortState[MAX_NUM_AXES];</td>
  </tr>
</table>


        169. **Reasoning:**  

            137. Enumeration information is stored in the binary, so enumeration names can be shown by the debugger.

            138. Enumerations are type-safe and respect scope.

            139. Since enumeration values are "known" at compile-time, they can be used in switch case labels (where constant variables cannot).

            140. Enumeration typedef’s provide the clearest implementation of enumerations in our code.

            141. By always assigning an enumeration member name to an enumeration variable (and not a literal value), we ensure that the assignment is valid.

            142. Static analysis provides additional benefits when using enumerations, such as ensuring that all possible cases are covered when switching over an enumeration variable.

        170. **Enforcement:**  Code Review

12. **Preprocessor Directives**

    47. **Conditional Compilation**

        171. **Rules:**

            143. Conditional compilation directives for code sections shall use #if defined() and #if !defined() rather than #ifdef and #ifndef.

        172. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>#ifdef X
…
#endif</td>
    <td>#if defined(X)
…
#endif</td>
  </tr>
</table>


        173. **Reasoning:**  Readability

        174. **Enforcement:**  Code Review

    48. **Code/Data Section Allocation**

        175. **Rules:**

            144. All functions definitions shall be directly preceded by a code section pragma establishing the location of the function in memory.

            145. All variables outside of internalGlobals* and externalGlobals* shall be directly preceded by a data section pragma establishing the location of the function in memory.

        176. **Examples:**

<table>
  <tr>
    <td>Incorrect</td>
    <td>Correct</td>
  </tr>
  <tr>
    <td>void foo(void)
{
    ...
}
</td>
    <td>#pragma CODE_SECTION(foo, ".internalCode")
void foo(void)
{
    ...
}</td>
  </tr>
</table>


        177. **Reasoning:**  Code Clarity & Performance

        178. **Enforcement:**  Code Review

    49. **Additional Pragmas**

        179. **Rules:**

        180. **Examples:**

<table>
  <tr>
    <td></td>
  </tr>
</table>


        181. **Reasoning:**

        182. **Enforcement:**

