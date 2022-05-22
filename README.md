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
