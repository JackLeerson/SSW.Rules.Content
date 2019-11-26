

---
authors:
  - id: 1
    title: Adam Cogan
  - id: 46
    title: Danijel Malik
---




<span class='intro'> ​The real value of the code health system is that is made improvements in code quality more visible to the team and managers. By including several steps to the build process, the results of the analysers included in previous steps can be extracted out and summarised in a report spanning the project's lifetime.&#160;<br> </span>

<h3 class="ssw15-rteElement-H3">​​Related Steps to Code Health&#58;​​​<br></h3><ul><li><a href="/_layouts/15/FIXUPREDIRECT.ASPX?WebId=3dfc0e07-e23a-4cbb-aac2-e778b71166a2&amp;TermSetId=07da3ddf-0924-4cd2-a6d4-a4809ae20160&amp;TermId=1e14fbd6-0c72-4791-9c79-893de1fdd89e">Do you use the Code Health Extensions in VS Code?​</a><br></li><li><a href="/_layouts/15/FIXUPREDIRECT.ASPX?WebId=3dfc0e07-e23a-4cbb-aac2-e778b71166a2&amp;TermSetId=07da3ddf-0924-4cd2-a6d4-a4809ae20160&amp;TermId=9e155c90-0502-447a-a1a3-fb2b1580982a">Do you use the Code Health Extensions in Visual Studio?</a><br></li></ul><p></p><h3 class="ssw15-rteElement-H3">​What Steps to Include in the B​​​uild Definition​</h3><p class="ssw15-rteElement-P">​​Summary&#58;<br></p><ol class="ssw15-rteElement-P"><li>Ensure &quot;Restore NuGet Packages&quot; &amp; &quot;Build Solution&quot; are in the build definition to run the Roslyn analysers.<br></li><li>Add several npm and command line steps to the build definition to run tslint. (On premises builds require an additional step).<br></li><li>Include an identifying variable &quot;PrimaryBuild&quot; to the build definition.<br></li><li>Check the build is running without issues.​​​<br></li></ol><p>The resulting build&#160;should look like this.<br></p><dl class="ssw15-rteElement-ImageArea">​​​​​<img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-Build-Good-1.png" alt="VSO-Build-Good-1.png" style="margin&#58;5px;width&#58;808px;" /></dl><dd class="ssw15-rteElement-FigureGood">Figu​​re&#58;&#160;​Good Example - Build Passing with no summa​​​ry issues<br></dd><dl class="ssw15-rteElement-ImageArea">​​​<br><span class="ssw15-rteStyle-Highlight">Ensure&#160;utilisation of TeamBuild2015 or higher. (No support for XAML builds)</span><br>Edit the build definition on &lt;CompanyName&gt;.visualstudio.com, and add the following build tasks.<br>If your project does not contain TypeScript files, then you do not need to include the TSLint build tasks.<br></dl><dl class="ssw15-rteElement-ImageArea"><img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-BuildDefinition-V3.png" alt="VSO-BuildDefinition-V3.png" style="margin&#58;5px;width&#58;808px;" /></dl><dd class="ssw15-rteElement-FigureGood">Figure&#58; Good Examp​​​​​​le -&#160;Steps ​​added to&#160;build definition.<br></dd><dl class="ssw15-rteElement-ImageArea">​​​​<img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-DirectoryExampleV2.png" alt="VSO-DirectoryExampleV2.png" style="margin&#58;5px;width&#58;808px;" /></dl><dd class="ssw15-rteElement-FigureNormal">Figure&#58; Exa​mp​​​le director​​y for TSLint run commands<br></dd><p><br>Under advanced for the Command Line tasks, the Working Directory can be specified if necessary.<br></p><p><span class="ssw15-rteStyle-Caption">TsLint​</span><br><strong>Npm&#160;</strong>- Install tslint and typescript<br><span class="ssw15-rteStyle-IndentText"><strong>Name​&#58;</strong>&#160;npm install tslint</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>​​​Working Folder&#58;</strong>&#160;&lt;Top Directory&gt;</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Npm Command&#58;</strong>&#160;install</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Arguments&#58;&#160;</strong>-g tslint typescript</span><br><br><strong>Command Line</strong>&#160;- Check the version&#160;​​​(Useful to determine rule discrepancies across builds)<br><span class="ssw15-rteStyle-IndentText"><strong>Name​&#58; </strong>Check tslint version</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Tool&#58;&#160;</strong>tslint</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Arguments&#58;</strong>&#160;-v</span><br><br><strong>Command Line</strong>&#160;-&#160;Builds a default configuration file for the build (Without it issues can differ between build and development environment<br><span class="ssw15-rteStyle-IndentText"><strong>Name​&#58;&#160;</strong>Create tslint config file</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Tool&#58;&#160;</strong>tslint</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Arguments&#58;</strong>&#160;--init</span><br class="ssw15-rteStyle-IndentText"><br><strong>Command Line&#160;</strong>- Run tslint, force is required to stop the build from crashing (TSLint will return and exit code of 1 regardless of if issues exist)<br><span class="ssw15-rteStyle-IndentText"><strong>Name​&#58;</strong>&#160;​Run&#160;tslint</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Tool&#58;​&#160;</strong>TSLint</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>Arguments&#58;</strong>&#160;--force &lt;Solution Directory&gt;/**/*.ts&#123;,x&#125;</span><br><br>If your build is being hosted, then the config file must be reloaded every time.&#160;<span class="ssw15-rteStyle-Highlight">If your build is running on premises</span>, the config file will attempt to load over the existing one and break the build.<br>If this is the case, just add a step to delete your config file after the scan is complete.​<br></p><dl class="ssw15-rteElement-ImageArea"><img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-RemoveConfig.png" alt="VSO-RemoveConfig.png" style="margin&#58;5px;width&#58;808px;" /><span style="color&#58;#555555;font-size&#58;0.9rem;font-weight&#58;bold;">Figure&#58; Command line​ s​​​tep to remove the&#160;config file (tslint.json) after the linter has run</span><br></dl><p class="ssw15-rteElement-P">​<br><strong>Command Line</strong>&#160;- Remove the tslint config file, as it will break future scan if the build is on premises if a config file already exists and an attempt to add another one is made.<br><span class="ssw15-rteStyle-IndentText"><strong>​​​Name​&#58;&#160;</strong>​Remove tslint config</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText"><strong>​Tool&#58;​&#160;</strong>del</span><br class="ssw15-rteStyle-IndentText"><span class="ssw15-rteStyle-IndentText">​<strong>Arguments&#58;</strong>&#160;tslint.json​</span></p><p>Once complete, save the build definition and run the build.​<br>Then check the build is successful.<br>If the build fails (due to errors), these should be corrected in the development environment.&#160;</p><div class="ssw15-rteElement-ContentBlock-SSW-Only">​​​​At the moment, it is fine to leave the warnings in the build, since the defined standard of rules is not set</div><h3 class="ssw15-rteElement-H3">​​​​​​Include &quot;PrimaryBuild&quot; variable<br></h3><p>​For the purposes of reporting, a unique tag must be added to the build definition which the Code Health steps have been applied to. ​<br>This is done with the <span class="ssw15-rteStyle-Highlight">addition of a variable (Name = PrimaryBuild, Value = true)​</span></p><dl class="ssw15-rteElement-ImageArea"><img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-AddVariableTag.png" alt="VSO-AddVariableTag.png" style="margin&#58;5px;width&#58;808px;" /></dl><dd class="ssw15-rteElement-FigureNormal">Figure&#58; Steps to add PrimaryBuild​​ variable to build definition​​​​​​​​​​​​<br></dd><h3 class="ssw15-rteElement-H3">Check the build is running without issues<br></h3><dl class="ssw15-rteElement-ImageArea">​<img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-Build-Bad-1.png" alt="VSO-Build-Bad-1.png" style="margin&#58;5px;width&#58;808px;" /></dl><dd class="ssw15-rteElement-FigureBad">Figu​re&#58; Bad Code with a Good Code Health Implementation​ - B​uild broke due to com​​​pile errors. Must fix to proceed.​</dd><dl class="ssw15-rteElement-ImageArea">​​​<img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-Build-Ok-1.png" alt="VSO-Build-Ok-1.png" style="margin&#58;5px;" /></dl><dd class="ssw15-rteElement-FigureBad">​​​​​​​​​​Figure&#58; Bad Code with a Good Code Health Implementation&#160;-&#160;​Successful​​​​ build with warnings.&#160;​These should be reprioritised as errors, or removed​<br></dd><dl class="ssw15-rteElement-ImageArea">​​​​​​​​<img src="/SiteAssets/do-you-run-the-code-health-checks-in-your-visualstudio-com-continuous-integration-build/VSO-Build-Good-1.png" alt="VSO-Build-Good-1.png" style="margin&#58;5px;width&#58;808px;" /></dl><dd class="ssw15-rteElement-FigureGood">​​​​​​​​​Figure&#58;&#160;&#160;Good&#160;Code with a Good Code Health Implementation&#160;- Successful​ build with ​​​no warnings.<br></dd><p>​<br></p>

