

---
authors:
  - id: 1
    title: Adam Cogan
  - id: 32
    title: Mehmet Ozdemir
---




<span class='intro'> <p>With CRM4, customizations cannot be undone and are cumulative, e.g.​&#160;if you add an attribute on a form and deploy, there is no easy way to remove the attribute from the entity. We have a <a target="_blank" href="http&#58;//www.ssw.com.au/SSW/Standards/BetterSoftwareSuggestions/CRM.aspx#RemoveAttributeOnForm">suggestion to CRM on this issue</a>.</p> </span>

 <p>In order to remove the attribute, what you have to do&#58;</p>
            <ol>
                <li>If attribute is not a required field then go to step 3.</li>
                <li>Set attribute to be not required field</li>
                <li>Save and publish the changes</li>
                <li>Remove attribute from the form</li>
                <li>Save and publish the changes</li>
                <li>Remove attribute from the entity</li>
                <li>Save and publish the changes</li>
            </ol>
            <p>Because of this reason, we have to take extra care in tracking and maintaining the CRM customization changes. So the solution&#58;</p>
            <ol>
                <li>Make someone (that person is called CRM Champion) in charge of schema changes</li>
                <li>Define security roles so that only this person can make customization changes</li>
                <li>Everyone else has to send customization changes to the CRM Champion in development team</li>
            </ol><div><span style="line-height&#58;20.99431800842285px;">On larger scale projects, functional design documentation governs the customization and on multiple member project teams, it’s normally the BA(s), who are in charge of designing and configuring CRM.&#160;</span><span style="font-size&#58;13px;line-height&#58;20.99431800842285px;">Developers rarely configure the system unless acting in a BA capacity.</span></div>

