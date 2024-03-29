# CMPE152 

Compiler Project

Developed a working compiler.

This is a Java-to-C++ port of the source code from the book
Writing Compilers and Interpreters, 3rd edition,
by Ronald Mak.

Compiling the .cpp and .h source files of the Pascal compiler
requires the Boost header files. Download them from
https://www.boost.org/. You only need the header files;
you don't need to compile any Boost libraries. Install the
header files in a directory and modify the makefile's
BOOST_INCLUDE_DIR variable to indicate the directory path.

If you are on Windows, you must first install the GNU g++ compiler
and the 'rm' and 'make' utilities from Cygwin: https://www.cygwin.com/. 

The makefile and header_dependencies.txt file together enable you
to use the 'make' utility to compile and run on the command line.
See https://www.gnu.org/software/make/.

The Pascal compiler also includes a Pascal interpreter. The interpreter
is completely working by Chapter 12, and the compiler is completely
working by Chapter 18. There is no C++ port of the IDE from Chapter 14.

-----------------------------------------------------------------------

NOTE: Before running any of the following 'make' commands, run

    make dependencies
    
once in each chapter to generate the file header_dependencies.txt which
tells the 'make' utility how the .cpp files depend on the .h files.
You should not need to run this command again in a chapter unless you
add or remove .h or .cpp files, or upgrade the boost header files.

-----------------------------------------------------------------------

Example uses of 'make' on the command line:

make clean

    Remove all generated .o files and the executable file to start fresh.

make

    Compile all the .cpp and .h files and generate the executable file
    (i.e., the compiler). There may be many warning messages.

make execute src=hello.pas flags=ix

    Run the Pascal interpreter to execute Pascal source file hello.pas.
    The src parameter is required and the flags parameter is optional,
    and they can appear in any order. (See the flags below.)

make compile src=hello.pas

    Run the Pascal compiler on the Pascal source file hello.pas
    to generate Jasmin assembly object code hello.j.
    You can include the optional flags parameter.
    
make assemble src=hello.j

    Run the jasmin assembler on assembly file hello.j
    to generate hello.class for the Java Virtual Machine.
    
make run src=hello

    Execute program hello.class on the Java Virtual Machine.

-----------------------------------------------------------------------

The optional flags:

    i  Print the intermediate code (i.e., the parse trees).
    x  Print the cross-reference tables (symbol table contents).
    
These are for debugging a Pascal program while running it
in the interpreter:

    l  (letter L) Print the current source line number.
    a  Print the value currently being assigned to each variable.
    f  Print the value currently being fetched from each variable.
    c  Print each call to a procedure or a function.
    r  Print each return from a procedure or a function.
    
You can combine the flags in any order.
