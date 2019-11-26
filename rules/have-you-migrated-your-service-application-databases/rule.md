

---
authors:
  - id: 28
    title: Daragh Bannigan
  - id: 9
    title: William Yin
---




<span class='intro'> Depends on your SharePoint farm environments,&#160;you may need to upgrade some&#160;​service applications databases.<p></p> </span>

<p>​In our case, we have upgraded the below several service&#160;application databases&#58;</p><ul><li><span style="line-height&#58;1.6;">Secure Store</span><br></li><li><span style="line-height&#58;20px;">User Profiles</span><br></li><li><span style="line-height&#58;1.6;">Managed Metadata</span><br></li><li><span style="line-height&#58;1.6;">Business Connectivity Services</span><br></li></ul><p>Steps&#58;</p><p>1. Backup databases of SharePoint 2010 or&#160;2013 Service Application.</p><p>2. Restore and attach databases to SharePoint 2013 or&#160;2016 SQL server.</p><p>3. Create service application in SharePoint 2013 or&#160;2016​ Central Admin site with the restored database.</p><p>4. Test.</p><p>5. Done.</p>

