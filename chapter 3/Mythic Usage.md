navigate to https://127.0.0.1:7443 to log in (see Figure 3-5). You can find the
mythic_admin password in the .env file of the Mythic directory.
![[page136_img1.jpeg]]
After you are logged in, navigate to the Agents & C2 section on the left panel, as illustrated in Figure 3-6. You will need to edit the C2 profile to include the certificates you previously generated.
![[page137_img1.jpeg]]
Prior to editing the profile configuration, you will need to update the values for the profile by clicking the Clipboard icon and editing the fullchain.pem and privkey.pem files and adding in the domain certificates generated from Example 3-5. Simply copy the value from ``/etc/letsencrypt/live/yourdomain.com/fullchain.pem`` and add it into the fullchain.pem file. The same step can be done for the
privkey.pem from ``/etc/letsencrypt/live/yourdomain.com/privkey.pem``. Figure 3-7 illustrates where you can find those files in the C2 configuration.
![[page139_img1.jpeg]]
Next, you will edit the config to ensure that it does not use the default options. You can customize this part as you want, as illustrated in Figure 3-8. For this example, you can use similar headers as Microsoft-IIS/10.0, as demonstrated in Example 3-10.
![[page140_img1.jpeg]]
```
{
	"instances": [
		{
			"ServerHeaders": {
				"Server": "Microsoft-IIS/10.0",
				"Cache-Control": "max-age=0, no-cache",
				"Pragma": "no-cache",
				"Connection": "keep-alive",
				"Content-Type": "text/html; charset=utf-8"
			},
		"port": 443,
		"key_path": "privkey.pem",
		"cert_path": "fullchain.pem",
		"debug": false,
		"use_ssl": true
		}
	]
}
```
Next, you need to stop and start your profile to ensure the
changes went into effect 
![[page141_img1.jpeg]]
Then you can test your traffic flow by hitting your CDN
endpoint. In this case, you should receive a 405 response, which
indicates the traffic is passing through properly because you
are not specifying a specific endpoint on the server; however, it
shows the traffic hits end to end
```
curl -I https://examplenameplaceholder.azureedge.net
HTTP/2 405
date: Sun, 23 Jun 2024 20:20:25 GMT
content-type: text/plain
content-length: 22
x-azure-ref: <snipped>
x-fd-int-roxy-purgeid: 0
x-cache: TCP_MISS
```
the target payload will be appollo and the output will be winexe
![[page144_img1.jpeg]]
Ultimately, an operator determines which commands are built
into the agent and can add or remove which ones are included
in the payload

now you got a payload that you can download

 ## NOTE
>In a real scenario, you would need to alter the C2 agent because it’s heavily signatured and also would need to make additional modifications to obfuscate your shellcode for delivery to bypass protections in place for an endpoint. 
>We will discuss potential options to obfuscate your shellcode in Chapter 4.

## ⬅️ Navigation
← Back to [[Mythic Framework]]

