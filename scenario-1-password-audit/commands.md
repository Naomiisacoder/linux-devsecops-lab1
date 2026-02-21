
## Part A: Create audit_test User Without Password
1-  # Create user without password

     sudo useradd audit_test

     
2- # Verify user exists
    cat /etc/passwd 

    
3- # Output:audio_test:x:1001:1001::/home/audio_test:/bin/sh
#Screenshot showing the creation of audio-tester user
<img width="706" height="185" alt="created audio_test user" src="https://github.com/user-attachments/assets/6178e319-fa9b-4c80-906f-50e6e98dfefd" />

##part B:Identifiy Users Without passwords(Discovery required)
Inspect password file

Sudo cat  /etc/shadow
#Output: audit_test:!:18295:0:99999:7::

#Explanation:indicates no active password set .The syntax for this display is username:password:lastchange:min:max:inactive:expire. 
Hence in the case of the audit_test user the password section has no information apart from the exclamation mark which indicates no password.

# Screenshot showing user login information
<img width="1106" height="84" alt="password defined for audiotest" src="https://github.com/user-attachments/assets/f050ae0b-394e-4282-aa32-d1c83e626f6f" />
<img width="1103" height="537" alt="content of etcshadow" src="https://github.com/user-attachments/assets/f4282c48-201b-45d0-b3dc-5b7665538e12" />
<img width="1110" height="203" alt="content etcshadow" src="https://github.com/user-attachments/assets/80ed1aa3-b9ba-4c3e-abb1-7c318281be48" />

#Part C : Set password for audit test 
#Set password for user 
   Sudo passwd audit_test
#To view output of the applied password
 Sudo /et/shadow
#Output example
#Note “$6$...” indicates an active hashed password

# Screenshot showing password state after update
<img width="1106" height="84" alt="password defined for audiotest" src="https://github.com/user-attachments/assets/3de80a7e-f401-4c33-8a21-3203ee8a2ca8" />
another display of the shadow file after password update.
<img width="941" height="72" alt="content of etcshadow2passwordforaudiotest" src="https://github.com/user-attachments/assets/bcedae09-7283-4b90-87aa-9063b9656bd5" />

# Observation and notes from scenario 1:
Details about existing users are found in  /etc/passwd 
Details about the user password ,when it was last modified is located in  /etc/shadow 
The ! in /etc/shadow is replaced by a hashed password,after password was added to the user account.
The user can now log in.
/etc/shadow remains root-only, so normal users cannot view password hashes, ensuring security.
