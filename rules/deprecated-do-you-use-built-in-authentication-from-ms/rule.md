

---
authors:
  - id: 1
    title: Adam Cogan
---




<span class='intro'> <p class="ssw15-rteElement-GreyBox">​This rule has been replaced by&#160; ​<a href="/_layouts/15/FIXUPREDIRECT.ASPX?WebId=3dfc0e07-e23a-4cbb-aac2-e778b71166a2&amp;TermSetId=07da3ddf-0924-4cd2-a6d4-a4809ae20160&amp;TermId=afa18fb5-a263-4538-a54e-02c8bd78ad67">Do you choose the best method of authentication for your situation?​​​​</a></p> </span>

<p style="text-decoration&#58;line-through;">Assuming you want&#58;</p><ul style="text-decoration&#58;line-through;"><li>Full blown user management</li><li>Nice Controls eg. Login, Change Password</li><li>To be able to implement authentication without a Security Consultant to check</li></ul><p style="text-decoration&#58;line-through;">The options are&#58;</p><h3 style="text-decoration&#58;line-through;">Option 1&#58; ASP.Net Membership provider (original)</h3><p style="text-decoration&#58;line-through;">Use their ugly table structure.</p><p style="text-decoration&#58;line-through;">Resilient to errors/attacks/omissions. &quot;Better the devil you know, than the one you don't&quot;.</p><p style="text-decoration&#58;line-through;">So if it is simple, straightforward, standardized, integrated well with the existing platform, well documented, and sufficient for your current requirements - why would someone want to go and do something custom?</p><p style="text-decoration&#58;line-through;">No OAuth eg. Facebook</p><h3 style="text-decoration&#58;line-through;">Option 2&#58; <a href="http&#58;//www.asp.net/" target="_blank">ASP.NET</a> Membership provider (custom)</h3><p style="text-decoration&#58;line-through;">(Inherits from Option 1)</p><p style="text-decoration&#58;line-through;">Typically if you want to use your own database tables (even non SQL)</p><p style="text-decoration&#58;line-through;">Easy. A typical implementation of a custom membership or role provider is a simple SELECT query against a database.</p><p style="text-decoration&#58;line-through;">Potentially a glorified ValidateUser/GetRoles method.</p><p style="text-decoration&#58;line-through;">Little messy if you <strong>don’t</strong> want full blown user management. Then you must leave a number of NotImplementedException methods (because you are not going to administer the store through the provider). In that case implement a base class, leave 28 methods not implemented, implement ValidateUser that takes two strings and returns a bool ;)</p><p style="text-decoration&#58;line-through;">Most clients have more concerns about them making mistakes in the custom security code, that would compromise the security of the application, then about using a bloated existing platform security mechanism correctly (when there are thousands of samples and documentation out there about how to do so correctly).</p><p style="text-decoration&#58;line-through;">Yes to OAuth eg. Facebook</p><p style="text-decoration&#58;line-through;">Hard to unit test.</p><h3 style="text-decoration&#58;line-through;">Option 3&#58; Universal provider (Updated ASP.NET Membership provider)</h3><p style="text-decoration&#58;line-through;">(Inherits from Option 1)</p><p style="text-decoration&#58;line-through;">Use their table structure.</p><p style="text-decoration&#58;line-through;">The default for VS 2012 Web Forms</p><p style="text-decoration&#58;line-through;">Universal Providers are intended for cases where you have an existing ASP.NET Membership Provider and you want to use it with another SQL Server database backend (other than SQL Server).</p><p style="text-decoration&#58;line-through;">Yes to OAuth eg. Facebook (out of the box)</p><h3 style="text-decoration&#58;line-through;">Option 4&#58; SimpleMembershipProvider (New)</h3><p style="text-decoration&#58;line-through;">(Inherits from Option 1)</p><p style="text-decoration&#58;line-through;">Use their table structure.</p><p style="text-decoration&#58;line-through;">The default for VS 2012 MVC 4 templates.</p><p style="text-decoration&#58;line-through;">Yes to OAuth eg. Facebook (out of the box)</p><p style="text-decoration&#58;line-through;"><strong>Note&#58;</strong> If you need to use for Web Forms see <a href="http&#58;//blogs.msmvps.com/luisabreu/blog/2012/09/24/adding-the-simplemembership-provider-to-an-asp-net-web-forms-app/" target="_blank">Adding the SimpleMembership provider to an ASP.NET Web Forms app</a>.</p><h3 style="text-decoration&#58;line-through;">Option 5&#58; Use “Membership Reboot” on GitHub (a Gurus one) (RECOMMENDED)</h3><p style="text-decoration&#58;line-through;">A solid, more flexible and open source alternative to the ASP.NET membership provider</p><p style="text-decoration&#58;line-through;">Typically if you want to use your own database tables (even non SQL)</p><p style="text-decoration&#58;line-through;"><strong>Description&#58;</strong> <a href="http&#58;//brockallen.com/2012/09/02/think-twice-about-using-membershipprovider-and-simplemembership/" target="_blank">Think twice about using MembershipProvider (and SimpleMembership)</a></p><p style="text-decoration&#58;line-through;"><strong>Source&#58;</strong> <a href="https&#58;//github.com/brockallen/BrockAllen.MembershipReboot" target="_blank">https&#58;//github.com/brockallen/BrockAllen.MembershipReboot</a></p><p style="text-decoration&#58;line-through;">This OSS account management library manages these sorts of things for you&#58;</p><ul style="text-decoration&#58;line-through;"><li>PBKDF2 (Proper password storage)</li><li>Password reset</li><li>Account lockout for password guessing</li><li>Account confirmation via email, etc</li></ul><p style="text-decoration&#58;line-through;">Bonus&#58;</p><ul style="text-decoration&#58;line-through;"><li>It is multi-tenant</li><li>It is claims aware (some complicated security thing from Microsoft that will revolutionize security)</li></ul><p style="text-decoration&#58;line-through;">The design is different than ASP.NET Membership in that the security goo is packaged separately from the persistence (the database). You’d not normally need to change the security stuff (though it is extensible).</p><p style="text-decoration&#58;line-through;">You implement a repository if you want a custom storage (or you can just use EF and whatever EF-enabled DB you want).</p><h3 style="text-decoration&#58;line-through;">Option 6&#58; Roll your own</h3><p style="text-decoration&#58;line-through;">Risk, Risk, Risk... Unless you are a security consultant you are likely to leave a security hole.</p><p style="text-decoration&#58;line-through;">Of course you should not roll your own security. This option is building your own authentication and authorization routines to tie into FormsAuth (instead of using providers).</p><p style="text-decoration&#58;line-through;">The ASP.NET membership provider is wired in at a deep level in the ASP.NET pipeline. A roll your own solution loses you the benefits of leveraging this integration eg. In Silverlight and the WebAPI</p><p style="text-decoration&#58;line-through;">An example of completely removing ASP.NET Membership Providers&#58; <a href="http&#58;//www.devproconnections.com/article/aspnet2/Kicking-ASP-NET-Providers-to-the-Curb-129584" target="_blank">Kicking ASP.NET Providers to the Curb</a> - And that actually works fine, but with one big, ugly, drawback. The site is able to authenticate and authorize as needed, but you drop in a few .ashx or other things like Elmah, CacheManagement, etc, and then tried to restrict access to them... it obviously is not able to.</p><p style="text-decoration&#58;line-through;"><strong>Note&#58;</strong> Gurus use Windows Identity Foundation (and IdentityModel).</p>

