

---
authors:
  - id: 1
    title: Adam Cogan
  - id: 17
    title: Ryan Tee
---




<span class='intro'> Stored procedure names in code should always be prefixed with the owner (usually dbo). This is because if the owner is not specified, SQL Server will look for a procedure with that name for the currently logged on user first, creating a performance hit. 
 </span>


  <dl class="badCode">
    <dt style="width&#58;92.63%;height&#58;76px;">
    <pre>SqlCommand sqlcmd = new SqlCommand(); sqlcmd.CommandText = &quot;<span style="background-color&#58;rgb(255, 0, 0);">
                    proc_InsertCustomer</span>&quot; sqlcmd.CommandType
                    = CommandType.StoredProcedure; sqlcmd.Connection = sqlcon;</pre>
    </dt>
    <dd>Bad Example </dd>
</dl>
<dl class="goodCode">
    <dt style="width&#58;93.1%;height&#58;80px;">
    <pre>SqlCommand sqlcmd = new SqlCommand(); sqlcmd.CommandText = &quot;
                     <span style="background-color&#58;rgb(0, 255, 0);">dbo.proc_InsertCustomer</span>&quot;; sqlcmd.CommandType
                     = CommandType.StoredProcedure; sqlcmd.Connection = sqlcon;</pre>
    </dt>
    <dd>Good Example </dd>
</dl>
<table id="table4" class="clsSSWProductTable" cellspacing="2" summary="Code Auditor" cellpadding="2">
    <tbody>
        <tr>
            <td>We have a program called <a href="http&#58;//www.ssw.com.au/ssw/CodeAuditor/Default.aspx">SSW Code Auditor</a> to check for this rule.</td>
        </tr>
    </tbody>
</table>


