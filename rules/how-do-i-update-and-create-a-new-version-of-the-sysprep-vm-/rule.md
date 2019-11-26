

---
authors:
  - id: 1
    title: Adam Cogan
---




<span class='intro'> When MS releases a new service pack, or new Windows update, we install these to the master image and create a new version of the Sysprep image for future VMs.  </span>

<ol><li>&#160;Update SQL Server service packs </li>
<li>Update Windows Server 2003 service packs </li>
<li>Update Windows </li>
<li>Update VS.NET service packs </li>
<li>Update SharePoint service packs </li>
<li>Update MS Office SharePoint Designer service packs </li></ol>
<p>To create a new VM&#58; </p>
<ol><li>Make a copy of the master.vhd, rename it to the next version </li>
<li>Create a VM using this new vhd </li>
<li>Copy additional setup files to D&#58;\install\ </li>
<li>Modify the scripts in D&#58;\scripts\ </li>
<li>When finished, power down the VM. Make a copy of this and rename it to sysprep-vNext.vhd </li>
<li>Create a new VM using this new vhd </li>
<li>Start it up, and then run the sysprep command in D&#58;\sysprep\ </li>
<li>This will generalize the computer's settings and shut it down </li>
<li>Don't start up the VM again - or it'll run the start up scripts </li>
<li>Zz old copies of the master.vhd and sysprep.vhd </li></ol>

