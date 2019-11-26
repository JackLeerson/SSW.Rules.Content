

---
authors:
  - id: 1
    title: Adam Cogan
---




<span class='intro'> <p class="ssw15-rteElement-P">​Ok, once a project gets going, you can end up dealing with many people on the client side. From the Boss to the Business Decision Maker (we call them the &quot;Product Owner&quot;) through to Mary the receptionist (aka &quot;users&quot;), everyone has something to say about the software as it is being developed. However, when you are working on a Time &amp; Materials basis in a rapid development environment with continually changing specs, you have to be certain that the work you are doing is authorised by the person who signs the cheques.
<br></p> </span>

<div class="greyBox">
      <strong>To&#58;</strong> Angelo;<br> 
      <strong>Cc&#58;</strong> John, Sophie<br> 
      <strong>Subject&#58; </strong>Changes Requested by Sophie<p>As per our conversation, Sophie has requested the following changes to your application&#58; modifying rptContractRenewal to include the &quot;MaidenName&quot; field from the ClientContact Table, and positioning right next to the Surname field.</p><p>Please let us know ASAP if you don't want this problem fixed.</p><p>Thanks, <br>John<br> 
         <a href="http&#58;//www.ssw.com.au/" target="_blank"> www.ssw.com.au</a></p></div><dd class="ssw15-rteElement-FigureNormal">​Figure&#58; Sample Change Request Confirmation email  </dd><span style="line-height&#58;1.6;">So, say Alan from Accounts would like the Username and Password authentication to have a &quot;remember me&quot; checkbox for the Accounts module. This sounds reasonable, but it doesn't mean that you should charge right in and start coding.</span><p>As an example, this is how we govern this process&#58;</p><ul><li>At the beginning of the project one of the client staff is assigned as Product Owner. This person has full authority from the Business Decision Maker of the client as to what work is IN or OUT. Every new item of work must be authorized by this Product Owner.</li><li>Whenever someone who ISN'T the Product Owner makes a request for work, the Product Owner must be CC'd. If Mary the receptionist has not done this, the developer sends the email again to himself, and CC's the Product Owner (CC'ing other relevant people - if they may give feedback on the task) to let them know about the request.</li><li>We make the assumption that the task is good to go, so it is the Product Owner's job to make sure that they reply ASAP if they don't want the problem fixed.</li></ul>

