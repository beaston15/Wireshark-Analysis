# Wireshark-Analysis
## Investigating possible intrustions using Wireshark

<p>![Wireshark - 1](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/ef90d326-63d8-4d72-81fa-2131545bd645)</p>
<p>
In our first investigation we can see ARP traffic is asking for the MAC address of the subnet IP addresses to be sent to 192.168.56.1. This can help a bad actor indentify online systems when the ARP request is replied to.
</p>
<br />

![Wireshark - 3](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/02ba5d2e-7f92-4e79-a1fb-67291a6897e8)
<p>
Next, we can look into a tcp stream and find that the attacker is attemping to connect from an IP address of 192.168.56.111. As we can see they attempted to login using the username of "anonymous" and a password of "IEUser@", which ultimately failed.
</p>
<br />

![Wireshark - 4](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/50857f01-6c96-4c25-b25c-1d6f4cb01edd)
<p>
The attacker then sends a 404 page to the client(192.168.56.1). We can use Wireshark to retrieve the HTML file and generate the 404 webpage that the client is seeing. Then we will export packet 4612 that has a robots.txt filename.
</p>
<br />

![Wireshark - 5](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/5b1009a7-4f3d-4e92-986b-329fbbd55862)
<p>
When we open the file it shows the server, version, and port number that the webpage is coming from. The server is Apache 2.4.38 and port number is 80(http).
</p>
<br />


![Wireshark - 7](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/7f48d4cb-74a6-4efa-84b8-4f89f97492ef)
<p>
In the second investigation we see the same source and destination IP addresses with a source port of 80 and destination port of 36806.
</p>
<br />

![Wireshark - 8](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/08025dca-a2c8-43b8-87c2-68e38384c532)
<p>
Next we will investigate another http object, this time we will be looking at a zip file named "cr4ckx0r.zip" and export it to get more details about it.
</p>
<br />

![Wireshark-9](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/747dee9e-27d6-49ad-adad-e1ae3fbe371a)
<p>
Once we have the zip file exported we can check the md5 hash value of the file. We want to get the md5 hash value to compared files later and make sure there are no changes to the file.
</p>
<br />

![Wireshark - 10](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/41ff998e-695f-4de0-8523-68c74dd5a253)
<p>
Inside of the zip file we find another file named "hashcat".
</p>
<br />

![Wireshark  - 11](https://github.com/beaston15/Wireshark-Analysis/assets/121417326/420ed48c-c1f7-466c-a454-9c6fac166d30)
<p>
Finally we export the file "hashcat" out of the zip file into our investigation directory and find the md5 hash value the same way we did for the zip file.
</p>
<br />
