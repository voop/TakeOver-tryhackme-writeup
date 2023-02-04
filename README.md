# Writeups
TakeOver tryhackme writeup
Room Description:
![image](https://user-images.githubusercontent.com/56643982/216768528-8e28a847-8af6-45cc-acd0-d653c20945b9.png)


Hello there,

    I am the CEO and one of the co-founders offuturevera.thm.
    In Futurevera, we believe that the future is in space.
    We do a lot of space research and writeblogs about it.
    We used to help students with space questions, but we are rebuilding oursupport.

Recently blackhat hackers approached us saying they could take over and are asking us for a big ransom. Please help us to find what they can take over.

Hint: Don’t forget to add the /IP in /etc/hosts for futurevera.thm ; )

Our website is located at https://futurevera.thm


1. Connect to TryHackMe’s VPN and Make sure to add the subdomains to /etc/hosts with the corresponding IP
2. Type https://futurevera.thm/ in your browser but you will get a warning prompt, click on advance and accept the risk. 
3. Subdomain Enumeration through gobuster displays a subdomain portal.futurevera.thmas below:

gobuster vhost -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u futurevera.thm 

4. From the description they write blogs on the website and that the support page was in development, so we need to explore these two pages. Since we can’t access them directly we add them in /etc/hosts as below: 

echo "10.10.17.229 blog.futurevera.thm support.futurevera.thm >> /etc/hosts

With these two added; explore the following approaches:
1. Open and check the certificate of support.futurevera.thm, the DNS name field is where your flag is located
![image](https://user-images.githubusercontent.com/56643982/216769029-bb407772-32d7-4290-835c-cd6d28c228b8.png)

2.Try opening the support.futurevera.thm from the browser, you get a warning prompt and you will find a hint that there exists one more subdomain namely: 

secrethelpdesk934752.support.futurevera.thm

Add this to /etc/hosts and open the website and you will get the flag
