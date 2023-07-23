# Wireshark-Analysis
## Investigating possible intrustions using Wireshark

![Wireshark - 1](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/0e782c27-2790-47e7-9209-e4b05e8bbcd0)

<p>
In our first investigation we can see ARP traffic is asking for the MAC address of the subnet IP addresses to be sent to 192.168.56.1. This can help a bad actor indentify online systems when the ARP request is replied to.
</p>
<br />

![Wireshark - 3](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/45377541-7fba-4c42-a433-a591f84155fc)

<p>
Next, we can look into a tcp stream and find that the attacker is attemping to connect from an IP address of 192.168.56.111. As we can see they attempted to login using the username of "anonymous" and a password of "IEUser@", which ultimately failed.
</p>
<br />

![Wireshark - 4](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/0506c3cd-07d7-4cf1-bca9-3aa681b96ae0)

<p>
The attacker then sends a 404 page to the client(192.168.56.1). We can use Wireshark to retrieve the HTML file and generate the 404 webpage that the client is seeing. Then we will export packet 4612 that has a robots.txt filename.
</p>
<br />

![Wireshark - 5](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/9a375106-14d2-475f-ba4d-3ca0add9442b)

<p>
When we open the file it shows the server, version, and port number that the webpage is coming from. The server is Apache 2.4.38 and port number is 80(http).
</p>
<br />

![Wireshark - 7](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/edcb6bce-7379-4f8c-9b64-bb27543564a8)

<p>
In the second investigation we see the same source and destination IP addresses with a source port of 80 and destination port of 36806.
</p>
<br />

![Wireshark - 8](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/03ff1799-0f54-4bf6-92f6-155cf540329e)

<p>
Next we will investigate another http object, this time we will be looking at a zip file named "cr4ckx0r.zip" and export it to get more details about it.
</p>
<br />

![Wireshark-9](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/60be317f-5581-4920-b82b-125420e4808c)

<p>
Once we have the zip file exported we can check the md5 hash value of the file in the Linux command line. We want to get the md5 hash value to compared files later and make sure there are no changes to the file.
</p>
<br />

![Wireshark - 10](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/85a06ad1-b8b2-40f0-834e-eab699dbf466)

<p>
Inside of the zip file we find another file named "hashcat".
</p>
<br />

![Wireshark  - 11](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/9d3a01e0-156a-4b35-bca6-de2b0b5165aa)

<p>
Finally we export the file "hashcat" out of the zip file into our investigation directory and find the md5 hash value the same way we did for the zip file.
</p>
<br />
