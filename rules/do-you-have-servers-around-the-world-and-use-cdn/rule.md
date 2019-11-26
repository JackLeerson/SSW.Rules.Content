

---
authors:
  - id: 1
    title: Adam Cogan
---




<span class='intro'> ​​​​Having a very popular website is great. The only problem is where to host it. If you host it in your local country then it is very fast for your local market but what about the market on the other side of the world? The solution to this is to use a Content Delivery Network (CDN)<br> </span>

<p>The solution is to have an origin server (can be multiple for loadbalancing)&#160;and Content Delivery Nodes in locations that have many users accessing the website.&#160;Users will be delivered content from the closest Node. This is possible with the help of Bind DNS server and a list of IP addresses and the country of origin.​<br><br></p><p>​CDN is provided by many cloud providers such as WPEngine, Azure, CloudFlare but can also be achieved by using opensource software such as​ JSDelivr​, Cdnjs and many others​.<br></p><p><br></p><p>It can also be achieved using IIS Outbound Rewrite rules. For example https&#58;//ssw.com.au/ could be change to https&#58;//us.ssw.com.au/ and be directed to another IIS server.<br></p>

