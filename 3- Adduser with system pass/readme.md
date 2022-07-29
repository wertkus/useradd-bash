# Generating password with date!

There is a little Unix trick for generating random password with some cyrpt commands

lets check aforementioned column;
 
    #Generate a password.
    PASSWORD=$(date +%s%N | sha256sum | head -c48)

## date

    DESCRIPTION
       Display the current time in the given FORMAT, or set the system date.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

       %s     seconds since 1970-01-01 00:00:00 UTC
			 %N     nanoseconds (000000000..999999999)
we've got some random numbers with this commands, it's easier than using number libraries.

## sha256sum
The program sha256sum is **designed to verify data integrity using the SHA-256** (SHA-2 family with a digest length of 256 bits) 

       DESCRIPTION
       
       Print or check SHA256 (256-bit) checksums.

       With no FILE, or when FILE is -, read standard input.

we've had already got some numbers with date command. Although it wasn't enough for strong password cause we couldn't get alphabetical characters. the sha256sum command is used for encryption. When  that used, we got  such a strong string which that able to be password ; 
 >    ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad

## head 
    DESCRIPTION
       Print  the  first  10 lines of each FILE to standard output.  With more
       than one FILE, precede each with a header giving the file name.

       With no FILE, or when FILE is -, read standard input.

       Mandatory arguments to long options are  mandatory  for  short  options
       too.

       -c, --bytes=[-]NUM
              print  the  first  NUM bytes of each file; with the leading '-',
              print all but the last NUM bytes of each file

it has used for just clip the last strong string.  -c48  is meaning  show first 48 bytes as a string.
> as you see...

