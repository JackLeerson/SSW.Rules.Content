

---
authors:
  - id: 1
    title: Adam Cogan
---




<span class='intro'> <p>Many companies have more than one web applications running under different versions of .NET framework in different subdomains, or even in different domains. They want to let the user sign in once and stay logged in when switching to a different web site, and this is SSO (Single Sign-On).</p><p>In ASP.NET the logged-in user status is persisted by storing the cookie on the client computer, base on this mechanism, they are two possible solutions​&#58;<br></p><br> </span>

<ol><li>​​Share one cookie across the web applications.&#160;<br>The Forms authentication cookie is nothing but the container for forms authentication ticket. The ticket is encrypted and signed using the &lt;machineKey&gt; configuration element of the server's Machine.config file. So if the web applications are hosted on the same machine, the point is to create a shared authentication cookie. Configure the web.config and create the cookie manually can achieve this.&#160;<br>Following scenarios may suit this solution
   <ul><li>SSO for parent and child application in the virtual sub-directory</li><li>SSO for two applications in two sub-domains of the same domain</li></ul></li><li>Create its own cookie for each site by calling a page which can create cookie in its own domain.&#160;<br>If the web applications are hosted on different machine, it is not possibly to share a cookie. In this case each site will need to create its own cookie, call the other sites and ask them to create their own ones.&#160;<br>Following scenarios may suit this solution.
   <ul><li>SSO for two applications in different domains</li></ul></li></ol>
​​<br>

