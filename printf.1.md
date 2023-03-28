.TH man 3 "19 May 2022" "hk1.0" "_printf man page"

.SH AUTHOR "Otitoola Olufolabi" "Sikiru Ademola"

.SH NAME

.B _printf

\- function to print formatted output of arguments

.SH SYNOPSIS

#include "main.h"

int _printf(const char *format, ...);



.B _printf

.RI {FORMAT}

.RI [ARGUMENTS]...

.SH DESCRIPTION

	The  functions  in the _printf family produce output according to a format as described below.  The functions _printf() write output to stdout,

	the standard output stream.

	The function write the output under the control of a format string that specifies how subsequent arguments (or arguments) are converted for output.



   Format of the format string

       The format string is a character string, beginning and ending in its initial shift state, if any.  The format string is composed of zero or more  di‐

       rectives:  ordinary  characters  (not  %),  which  are copied unchanged to the output stream; and conversion specifications, each of which results in

       fetching zero or more subsequent arguments.  Each conversion specification is introduced by the character %, and ends with  a  conversion  specifier.

       In the case of a double "%" i.e. "%%", the first "%" acts as an escape character for the second "%" and prints out only one "%" in the formated output.

       In between there may be (in this order) zero or more flags and subsequent arguments.



	_printf("%d", num);



  Flag characters

       The character % is followed by zero or more of the following flags:

   Conversion specifiers

       A character that specifies the type of conversion to be applied.  The conversion specifiers and their meanings are:



       d, i   The int argument is converted to signed decimal notation.  The precision, if any, gives the minimum number of digits that must appear; if  the

              converted  value  requires fewer digits, it is padded on the left with zeros.  The default precision is 1.  When 0 is printed with an explicit

              precision 0, the output is empty.



       o, u, x, X

              The unsigned int argument is converted to unsigned octal (o), unsigned decimal (u), or unsigned hexadecimal (x and X) notation.   The  letters

              abcdef  are  used for x conversions; the letters ABCDEF are used for X conversions.  The precision, if any, gives the minimum number of digits

              that must appear; if the converted value requires fewer digits, it is padded on the left with zeros.  The default precision is 1.  When  0  is

              printed with an explicit precision 0, the output is empty.



       c      If no l modifier is present, the int argument is converted to an unsigned char, and the resulting character is written.  If an l  modifier  is

              present,  the  wint_t  (wide  character) argument is converted to a multibyte sequence by a call to the wcrtomb(3) function, with a conversion

              state starting in the initial state, and the resulting multibyte string is written.



       s      If no l modifier is present: the const char * argument is expected to be a pointer to an array of character type (pointer to a string).  Char‐

              acters from the array are written up to (but not including) a terminating null byte ('\0'); if a precision is specified, no more than the num‐

              ber specified are written.  If a precision is given, no null byte need be present; if the precision is not specified, or is greater  than  the

              size of the array, the array must contain a terminating null byte.



.SH EXAMPLE

To print the address of Holberton School in the form "972 Mission St., San

Francisco, CA 94103", followed by a new line, where \fIstreet\fR, \fIcity\fR,

and \fIstate\fR are pointers to strings:



.RS

#include "main.h"



int main(void)



{



	char *street = "Mission St.";



	char *city = "San Francisco",



	char *state = "CA";



	printf("%d %s, %s, %s, %d\\n", 972, street, city, state, 94103);



}



.RE



To print the result of basic mathematical operations prepended by signs and

all numbers printed with a minimum precision of two digits:



.RS

#include "main.h"



int main(void)



{



	_printf("%.2d + %.2d = %+.2d\\n", 1, 2, 1 + 2);



	_printf("%d - %d = %+d\\n", 10, 20, 10 - 20);



}





.SH RETURN VALUE

       Upon successful return, these functions return the number of characters printed which excludes the null byte used to end output for strings.

.B ARGUMENT

(s) according to

.B

.SH FORMAT

.SH Reporting Bugs

	Report _printf bugs to https://github.com/Ade2002/printf/issues

        Code  such  as  _printf(foo);  often indicates a bug, since foo may contain a % character.  If foo comes from untrusted user input, it may contain %n,

        causing the _printf() call to write to memory and creating a security hole.

.SH Copyright

	Copyright 2022

	Free Software Foundation, Inc. License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.

	This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law.
