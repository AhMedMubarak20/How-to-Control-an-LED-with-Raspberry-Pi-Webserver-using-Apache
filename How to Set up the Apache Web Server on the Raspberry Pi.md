# How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache

Apache is an open-source web server launched and maintained by the Apache foundation and it is used to access different web pages. For the readers who do not know about the working of the web server, a web server finds the webpage according to the provided URL or HTTP and after clearing the security checks it displays the webpage.
In this write-up, we will learn the installation procedure of the Apache web server on the Raspberry Pi operating system and also learn how a web page is accessed using the Apache web server.

How to install an Apache web server on Raspberry Pi
Before setting up the Apache server, we will first update and upgrade all the packages up to date of the Raspberry Pi using the apt package manager command:

$ sudo apt update && sudo apt upgrade -y
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/f1be2535-1468-4860-af13-869caf93ff9e)


Now, we will check the status of the Apache server using the systemctl command:

$ sudo systemctl status apache2
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/8fac371d-a158-4399-8c36-0feaab5facf4)

The output means that the Apache server has not been pre-installed, so we will install it using the apt package manager:

$ sudo apt install apache2 -y
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/89151e55-6e0f-4380-8f1d-1e8701310ddf)


To confirm the installation of the Apache server on the Raspberry Pi, we will find out the status of Apache2 using the command:

$ sudo systemctl status apache2
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/8ea3bf19-a30a-470f-ac8d-4a7cfff97a23)

Now, we will type the IP address of the Raspberry Pi device in the URL bar of the web browser to check the running status of the Apache2, to know the IP address of the device, use the command:

$ hostname -I
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/42e6a932-7583-4db2-8d1a-9f63174d0f52)


Type the 192.168.18.218 (or simply type “localhost”) in the URL bar of the Chromium web browser of the Raspberry Pi:
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/7f052bc4-8501-4c3c-a0d3-27580385ded1)


The default Apache2 web page is displayed and confirms the installation of the Apache2 on Raspberry Pi.


How to set up the Apache2 server on the Raspberry Pi
For the configuration of the Apache2, we have to make the changes in the file /var/www/html, but before making the changes, we will add our Raspberry Pi user, Pi, to the www-data group(default group of Apache2) using the command:

$ sudo usermod -a -G www-data pi
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/f9b22d03-2c45-4c5d-b97e-0ab8fb894ab6)

After adding the user “Pi” to the group “www-data”, we will transfer all the ownership privileges of /var/www/html to the “www-data” group using the command:

$ sudo chown -R -f www-data /var/www/html
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/9aa2d9fc-2559-4d0b-952a-e69be3f306bc)

To save the changes, reboot the Raspberry Pi using the command:

$ reboot
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/0fba0472-5fb0-4b9b-96fc-a7a234f3ebc9)


How to install the PHP on Raspberry Pi
We can make websites using HTML and CSS only but those will be static websites whereas PHP is used to create dynamic websites, moreover, we cannot run it on our local machine therefore we create a virtual server in our local machine using Apache or xampp. It is primarily used to manipulate databases. It is popular because it is platform independent and can easily be integrated with many database management systems.package of the Raspberry Pi repository using the command:

$ sudo apt install php libapache2-mod-php -y
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/22e64f0d-ac09-4c12-ad80-2d07a93a772c)

Restart the Apache2 server using the systemctl command:

$ sudo systemctl restart apache2


Now we will create a Webpage with the help of PHP with the name of “linuxhint.php” using the nano editor:

$ sudo nano /var/www/html/linuxhint.php
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/487157b0-0867-4a53-91fd-bebc5dc35633)

We will display the “Welcome to the LinuxHint” and for this we will type the following php script in the file opened:

<?PHP
    echo "Welcome to the LinuxHint”;
?>
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/2ed4f3e1-fd0a-499a-893b-1d937812f807)

Exit the nano editor by saving the file using the shortcut key CTRL+X, and then go to the chromium browser and type the following address in the URL bar:


http://localhost/linuxhint.php
![image](https://github.com/AhMedMubarak20/How-to-Control-an-LED-with-Raspberry-Pi-Webserver-using-Apache/assets/76844219/3ce9ef3b-c972-4e2f-85e0-83e4ff3a41ba)

We can see the web page which was created by us has been opened.
