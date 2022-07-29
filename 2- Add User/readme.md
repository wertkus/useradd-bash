# useradd summary !

 ## PSEUDO CODE
 1-Make sure the script is being executed with superuser privileges.
 2-Get the username (login).
 3-Get the real name (contents for the description field).
 4-Get the password.
 5-Create the user with the password.
 6-Check to see if the useradd command succeeded.
 7-Set the password.
 8-Check to see if the passwd command succeeded.
 9-Force password change on first login.
 10-Display the username, password, and the host where the user was
created.
# Code pieces
###  What is a Linux UID?


A UID (user identifier) is **a number assigned by Linux to each user on the system**. This number is used to identify the user to the system and to determine which system resources the user can access. UID 0 (zero) is reserved for the root.
'''
{
if [[ "${UID}" -ne 0 ]]
then
   echo 'Please run with sudo or as root.'
   exit 1
fi
}

'''
### useradd !

DESCRIPTION  (from man)
       useradd is a low level utility for adding users. On Debian,
       administrators should usually use adduser(8) instead.

       When invoked without the -D option, the useradd command creates a new
       user account using the values specified on the command line plus the
       default values from the system. Depending on command line options, the
       useradd command will update system files and may also create the new
       user's home directory and copy initial files.

       By default, a group will also be created for the new user (see -g, -N,
       -U, and USERGROUPS_ENAB).
       
       -c, --comment COMMENT
           Any text string. It is generally a short description of the login,
           and is currently used as the field for the user's full name.

### passwd!

DESCRIPTION
        The passwd command changes passwords for user accounts. A normal user
        may only change the password for their own account, while the superuser
        may change the password for any account.  passwd also changes the
        account or associated password validity period.

    Password Changes
       The user is first prompted for their old password, if one is present.
       This password is then encrypted and compared against the stored
       password. The user has only one chance to enter the correct password.
       The superuser is permitted to bypass this step so that forgotten
       passwords may be changed.

       After the password has been entered, password aging information is
       checked to see if the user is permitted to change the password at this
       time. If not, passwd refuses to change the password and exits.

       The user is then prompted twice for a replacement password. The second
       entry is compared against the first and both are required to match in
       order for the password to be changed.

       Then, the password is tested for complexity. As a general guideline,
       passwords should consist of 6 to 8 characters including one or more
       characters from each of the following sets:

       •   lower case alphabetics

       •   digits 0 thru 9

       •   punctuation marks

       Care must be taken not to include the system default erase or kill
       characters.  passwd will reject any password which is not suitably
       complex.

     -e, --expire
           Immediately expire an account's password. This in effect can force
           a user to change their password at the user's next login.



