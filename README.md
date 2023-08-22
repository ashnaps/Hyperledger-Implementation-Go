# Hyperledger-Implementation-Go
- Prerequisites:
  1. Ubuntu OS/WSL
  2. Curl
  3. docker >=23.0, check out for docker deamon error/Docker desktop prompt: https://twitter.com/ashnaa_02/status/1693759379051614712
  4. docker-compose
  5. build-essential
  6. nodejs
  7. npm
  8. go
  9. WEFT library

# Running the network  
```markdown
export MICROFAB_CONFIG='{
"port": 8080,
"endorsing_organizations":[
{
"name": "ProducersOrg"
},
{
"name": "SellersOrg"
}
],
"channels":[
{
"name": "mango-channel",
"endorsing_organizations":[
"ProducersOrg",
"SellersOrg"
]
}
]
}'
```

```markdown
docker run -e MICROFAB_CONFIG -p 8080:8080 ibmcom/ibp-microfab
```
Or  
```markdown  
sudo docker run --name microfab --rm -ti -p 8080:8080 -e MICROFAB_CONFIG="${MICROFAB_CONFIG}" ibmcom/ibp-microfab
```

Output:  
![image](https://github.com/ashnaps/Hyperledger-Implementation-Go/assets/77959009/ec8c5856-dbe0-4bb1-86c0-8cbb47e19af9)  

  1. Create wallet & Gateways:
     ```markdown 
curl -s http://console.127-0-0-1.nip.io:8080/ak/api/v1/components | weft microfab -w ./_wallets -p ./_gateways -m ./_msp -f
```
![image](https://github.com/ashnaps/Hyperledger-Implementation-Go/assets/77959009/78d39060-7e20-45ce-a9e2-6a14856ba5e4)

 2. Installing Binaries:
```markdown
curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh | bash -s -- binary
```
Incase of errors:  
 - 1.	Try a different ISP, if it is Jio India.
   2.	Use a different DNS:
   	 - 1.	Run: `sudo nano /etc/hosts`
   	   2.	In the text editor (nano), scroll to the bottom of the file and add the following line:
   	   3.	`185.199.108.133 raw.githubusercontent.com`
   	   4.	This tells your system that when it tries to access raw.githubusercontent.com, it should use the IP address 185.199.108.133.
   	   5.	After adding the line, save the changes by pressing Ctrl + O (to write out) and then press Enter. To exit the text editor, press Ctrl + X.
   	   6.	You've now added the entry to the /etc/hosts file. Try the installation again to see if it resolves the issue.
   	       


  



```markdown
hello world
```
