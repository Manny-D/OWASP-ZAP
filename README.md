# Web Server Testing with OWASP ZAP

![OWASP ZAP](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/57ca2d3a-248c-4609-adff-a0434ecffabe)


## Description
This project is based on a pre-built Python web server and vulnerable web server (DVWA), from an online training course, to teach about web application attacks using the free vulnerability scanning tool [OWASP ZAP](https://www.zaproxy.org) - aka Zed Attack Proxy.

### Starting the Python Web Server:

![Python and Vulnerable Web Server](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/541f25dc-85ef-4a89-9a75-9ae0411c8d93)

</br>

### Firing up OWASP ZAP!

![ZAP and Session options](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/4cfcfc29-a121-464e-9e86-58944a7ad421)

</br>

### Python Web Server Scan:

Select Automated Scan -> enter our LINUX IP and Port 65412 as the URL to attack <br>

![Screenshot 2024-04-28 at 4 18 27 PM](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/44274f9c-6ba5-4d9f-b062-4e9d3745ef54) <br>

![Screenshot 2024-04-28 at 4 19 20 PM](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/99a4a058-51d9-43f8-acec-fa77cd1ca1c3)

then, select "Use traditional spider" -> select "Attack" -> once the crawling and scanning are complete, select Alerts:

![ZAP Results](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/613b4c82-3494-4c3f-a9b5-992021c01243)

ZAP does a pretty good job of finding easy to identify vulnerabilites, however it's worth noting that the automated tools do not always catch everything!

</br>

### Web Application Scan

Let’s open a Terminal as Administrator

![Terminal Admin](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/47924475-5c7d-438a-9ccd-3cf39684b4ca)

Upon receiving the (UAC) User Account Control Prompt, select Yes.

Now, we'll run the DVWA Docker image using the following:

![Docker DVWA ](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/a057342f-193f-4c1b-874c-e12aa2ef0be3)

Open another Command Prompt window -> run ipconfig -> note your IP address

<br/>

#### Interacting with DVWA via Chrome

Browsers normally connect directly to the internet. In this lab, we'll intercept and analyze web traffic by routing Chrome through ZAP. To achieve this, we need to configure Chrome to use ZAP as its proxy.

![ZAP Proxy Config](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/2fc38cea-5974-4458-a66c-8bb69cb3e2d9)


Let's navigate to the IP address, via Chrome, that we documented a few moments ago with ipconfig - eg. http://<YOUR_IP> 

Ignore the error message (caused by proxy interception), select "Advanced", then "Proceed to <YOUR_IP> (unsafe)" to continue.

![Warning Proceed](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/88454019-dbe0-4bdc-83ad-0c6bbc1d230c)

Next, there is a prompt to login. I continued with the credentials provided during the course. 

<br/>

#### Create / Reset Database

For the first run, we need to configure the database by clicking on the Create / Reset Database button, then logging back in:

![ZAP DB Config](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/191d8faf-2107-482e-b508-c803a0e15e4d)

Navigate back to ZAP and here we can see that it's now capturing site data. While this could be done manually by navigatting to every page, that would be time consuming! 
Instead, we can use crawling or spidering a website, which ZAP can do for us automatically!!

![Spidering](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/1d16c617-dc2b-4bb7-8b31-be9686537ace)

When the pop-up appears, select Start Scan

<br/>

#### Actively scanning the site for vulnerabilities.

To start the active scan:

![Active Scan](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/c60951c0-51bd-49f0-8289-bad72943be3e)

and when prompted, select Start Scan

Example of the active scan running:

![AS Running](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/0a4b940c-8a72-402f-b2d6-5cecaa853316)

Once the scan is completed, select Alerts to see the results:

![AS Alerts](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/eb2c5bb1-4d42-4e22-9ece-b955a12b08bf)

<br/>

### Missed items

While Zap can find 'easy' items, it can't catch everything. In the course, we learned that it can miss things like: 

#### Command Injections 

![Command Injections](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/88bd2870-8732-43fe-8a7b-3ff5f7125c07)

#### and SQL Injections:

![SQL Injections](https://github.com/Manny-D/Web-Application-Testing-OWASP-ZAP/assets/99146530/52257a44-63d2-4b70-8c25-ee3714d7a1e3)

<br/>

## Conclusion 
While automated tools like OWASP ZAP are invaluable for identifying common web application vulnerabilities, their reliance on predefined patterns can miss complex issues or novel attacks.  For a comprehensive security assessment, these tools should be complemented by human expertise and manual testing.
