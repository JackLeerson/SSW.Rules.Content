

---
authors:
  - id: 3
    title: Eric Phan
---




<span class='intro'> 
  <span style="line-height&#58;20px;font-family&#58;verdana, arial, helvetica, sans-serif;color&#58;#333333;font-size&#58;12px;">In Scrum, you work only on tasks in a sprint, and the task must belong to a committed PBI. As such, when you check in code in TFS, you should associate&#160;it with the task you are working on rather than the PBI.</span> 
 </span>

The reason behind this is that doing so provides a better way to track change sets in a sprint and give full traceability for work done during the sprint.
<div><span class="ms-rteCustom-GreyBox">Change set 123 was associated to PBI&#160;'As an end user I want to be able to lookup&#160;customers'<br></span>​<br><span class="ms-rteCustom-FigureBad">Bad Example - The change set was associated to a User Story not a Task</span></div>
<div><span class="ms-rteCustom-GreyBox">Change Set 123 was associated to Task 'Create database fields for customer' which is part of PBI​&#160;'As an end user I want to be able to lookup&#160;customers​<br></span><span class="ms-rteCustom-FigureGood">Good Example - The change set was associated to a Task</span></div>


