# Unit 15 Homework

### Web Application 1: *Your Wish is My Command Injection*

1. Complete the following to set up the activity. 

    - Start Terminal and run `cd Documents/web-vulns && docker-compose up`

    - Navigate to the following webpage: <http://192.168.13.25> and select the **Command Injection** option.
    
      - The web page should look like the following:

        ![DVWA Code Injection](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/DVWA%20Code%20Injection.PNG)


2. This page is a new web application built by Replicants in order to enable their customers to `ping` an IP address. The web page will return the results of the ping command back to the user.

    - Complete the following steps to walkthrough the intended purpose of the web application. 

      - Test the webpage by entering the IP address `8.8.8.8`. Press Submit to see the results display on the web application.

        ![DVWA Ping 8.8.8.8](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/DVWA%20Ping%208.8.8.8.PNG)

     - This process is no different than if we went to the command line and typed that same command: `ping 8.8.8.8`

        ![Terminal Ping 8.8.8.8](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Terminal%20Ping%208.8.8.8.PNG)

3. Test if we can manipulate the input to cause an unintended result.

    - On the same webpage, enter the following command (payload) in the field: `8.8.8.8 && pwd`

    - This command uses two ampersands to add a second command to the original request:

      - Terminal `ping 8.8.8.8 && pwd`: 

        ![Terminal ping & pwd](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Terminal%20Ping%208.8.8.8-pwd.PNG)
  
      - DVWA `8.8.8.8 && pwd`:

        ![DVWA ping & pwd](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/DVWA%20Ping%208.8.8.8.-pwd.PNG)


4. Now that you have determined that Replicants new application is vulnerable to command injection, you are tasked with using the dot-dot-slash method to design two payloads that will display the contents of the following files:
   
    - DVWA `8.8.8.8 && cat /../etc/passwd`:
      
        ![DVWA ping & cat](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/DVWA%20ping-passwd.PNG)
    
    - Terminal `ping 8.8.8.8 && cat /../etc/passwd`:

        ![Terminal ping & cat](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Terminal%20Ping-passwd.PNG)

    - DVWA `8.8.8.8 && cat /../etc/hosts`:

        ![DVWA ping & cat](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/DVWA%20ping-hosts.PNG)

    - Terminal `ping 8.8.8.8 && cat /../etc/hosts`:

        ![Terminal ping & cat](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Terminal%20ping-hosts.PNG)
  

5. **Deliverable**: Take a screen shot confirming that this exploit was successfully executed and provide 2-3 sentences outlining mitigation strategies. 

  - Run with restricted permissions
    - This will reduce the number of users that can access the database. It will also secure the location of all the confidential files and directories. 
  - Don't use command line calls if possoble
    - Use APIs whenever possible

### Web Application 2: *A Brute Force to Be Reckoned With*

1. Complete the following steps to set up the activity. 

    - Open a terminal and run `sudo burpsuite`
    
    - Open a browser on Vagrant and navigate to the webpage <http://192.168.13.35/login.php>.
  
    -  The page should look like the following:

      - Login: `bee`

      - Password: `bug`

    - This will take you to the following page:

      ![bWAPP login](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/bWAPP%20login.PNG)

    - To access the application where we will perform our activity, enter in the following URL: <http://192.168.13.35/ba_insecure_login_1.php>

      - This will take you to the following page:

        ![bWAPP Broken Auth](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/bWAPP%20Broken%20Auth..PNG)

        ![BurpSuite Interception](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/BurpSuite%20Intercept.PNG)

        ![Cluster Bomb](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Clusterbomb.PNG)

        ![Payload 1](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/payload%201.PNG)

        ![Payload 2](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Payload%202.PNG)

        ![Successful Login](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Successful%20Burp%20Suite.PNG)
