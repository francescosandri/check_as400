AS400 Nagios Plugin - Installation instructions
----------------------------------------------------

Preinstall notes
-------------------

* Security Note: Realize that this plugin communicates to the AS400 via telnet, which is easy to sniff and capture user names and passwords.  Use a generic user with restrictive rights for the plugin. The mandatory user rights are *ALLOBJ and *JOBCTL
* The project is pre-compiled with Java 1.8

Installation
-----------------
1) For languages other than Italian you will need to replace the correct check_as400_lang.java file (from Lang Source folder) and recompile the plugin before continuing (with javac check_as400.java command).
2) Copy all *.class and check_as400 files inside /usr/lib/nagios/plugins/ folder. If the folder of plugins is different correct the content of check_as400 file.
3) Apply chmod 0775 check_as400*
4) DONE!


Nagios configuration example
-----------------
Check command CPU example: /usr/bin/java -cp $USER1$ check_as400 -H $HOSTADDRESS$ -u $ARG1$ -p $ARG2$ -v CPU -w $ARG3$ -c $ARG4$ 
with 	ARG1 : username
		ARG2 : password
		ARG3 : warning
		ARG4 : critical
		
Check command MAXAVA example: /usr/bin/java -cp $USER1$ check_as400 -H $HOSTADDRESS$ -u $ARG1$ -p $ARG2$ -v MAXAVA $ARG3$
with 	ARG1 : username
		ARG2 : password
		ARG3 : library


Set AS/400 monitoring user profile (es. NAGIOS) Display sign-on information *NO
-----------------
CHGUSRPRF USRPRF(NAGIOS) DSPSGNINF(*NO) 


If you have suggestions or would like to submit bugs or a Paypal donation, write me at ing.francesco@gmail.com