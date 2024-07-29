# Connecting Two Routers on One Home Network
To improve the wifi connectivity across the home network, connecting two routers to one Home Internet offer a diligent solution. 
Two routers needs to be connected with an Ethernet cable permanently. This way the secondary router access the internet from the primary router. 

1. **Main Router Setting:**
   1. Make sure **DHCP is enabled** in this router. 
      - Netgear Router: It will available at Lan Settings > DHCP
      - TP-Link Deco: It will be at Mobile App > More > Advanced > DHCP
   2. Take a note of the existing IP address (ex: 192.162.1.1) and Subnet mask (ex: 255.255.255.0).
   3. Starting IP address to be updated for the DHCP. Set it to somethign greater that 10. 
       - Generic Router: Change from the previous value 192.168.1.1 to 198.168.1.20
       - My Deco Router: 192.168.68.50 to 192.168.71.250
    4. Save Settings. 

2. **Secondary Router Setting:**
   1. Make sure **DHCP is Disabled** in this router.
      - Netgear R4600: R4600 > Advanced > LAN Setup > Uncheck "Use Router as DHCP Server"
   2. Change IP address same as the IP address of the **Main router** except the last part to **.2**. Set the Subnet mask same as the Main router (ex: 255.255.255.0). 
      - Update IP Address to 192.168.1.1 from 192.168.1.**2** and **Save**.
   3. Access the router with the new IP address
      - Netgear Ex: http://192.168.1.2/start.htm
      - Deco Ex: http://192.168.68.51/start.htm

For more detailed walk-through, follow this [YouTube video](https://www.youtube.com/watch?v=mNh1r2_nKI8)