

---
authors:

---




<span class='intro'> ​​​​Without proper data cleansing, efforts spent in analysis and modelling are often wasted. &#160;This rule covers the important steps for getting your data in good shape before the hard work begins.<br> </span>

<p>​​Cleaning data is usually the first step in any data science project, and along with initially procuring the data, this step can take up a considerable amount of time. &#160;This rule will focus on techniques and steps required for data cleansing using Python in Azure Notebooks and using in-built functionality in the Azure Machine Learning Studio.</p><h3 class="ssw15-rteElement-H3">1. Inspect the data​<br></h3><p>Once the data has been imported, the first step is to visually and graphically inspect the data. &#160;In addition to getting a general understanding of the data, this step aims to uncover data outliers, data with formatting issues and columns where data is missing.<br></p><p>Using Python, data can be inspected in a tabular form by using the head and tail methods of a Pandas dataframe. &#160;These methods will output the first and last five rows of a dataframe (respectively),&#160;with an optional parameter&#160;allowing the five row default to be modified. &#160;In this step, we are looking for missing data (such as columns with NaN values) and columns where the formatting looks problematic.<br></p><p> 
   <img src="/PublishingImages/DataScience1.png" alt="" style="margin&#58;5px;width&#58;809px;" /> 
   <br> 
</p><p>Once we have a general sense of the data and have identified columns that contain features that are of interest to the data analysis, the next step is to&#160;plot the data to get a feeling for its distribution and to check for any outliers. &#160;The 'plot' method of dataframes supports a rich variety of ways to graphically present data.<br><br></p><p> 
   <img src="/PublishingImages/DataScience2.png" alt="" style="margin&#58;5px;width&#58;809px;" />​​ 
   <br> 
   <br> 
   <br> </p><p>For Azure Machine Learning projects, the context menu of a dataset can be used to Visualize the data available for modelling.<br></p><p> 
   <img src="/PublishingImages/DataScience3.png" alt="" style="margin&#58;5px;width&#58;809px;" /> 
   <br>Data is displayed in a tabular form, and by selecting a column, key statistics for that column can be inspected. &#160;Two graph types are available for the data - the default histogram view and a boxplot view. &#160;Using this screen, any problems with a dataset can be readily identified.<br></p><p> 
   <img src="/PublishingImages/DataScience4.png" alt="" style="margin&#58;5px;width&#58;809px;" />​<br><br></p><h3 class="ssw15-rteElement-H3">2. Decide on a strategy for dealing with ​​​missing data</h3><p>Missing, incomplete or suspect data can be dealt with in one of four&#160;ways&#58;</p><p></p><ol><li>​The data can be left as-is if it doesn't impact any analysis or modelling activities.<br></li><li>The rows with missing data can be excluded from the analysis. &#160;This is a good option if the percentage&#160;of rows with bad data is small&#160;​or the missing data cannot be&#160;​inferred or substituted for a&#160;​sensible value. &#160;This is often the case for non-numeric fields.<br></li><li>The data can be set to a default value such as zero for missing numeric fields or an empty string for text columns.<br></li><li>The data can be inferred based on other values in the dataset. &#160;This can range from simple calculations like mean or medium to highly advanced formulas like&#160;Multivariate Imputation by Chained&#160;Equations (MICE). &#160;These techniques will be covered below.<br></li></ol><h3 class="ssw15-rteElement-H3">Data Cleaning and&#160;Inference Techniques​ in Python<br></h3><p>​To exclude data from a Python dataframe, use a query expression to exclude the rows where the data is missing, and then re-assign the filtered dataframe back to the same variable. &#160;This will permanently remove the rows. &#160;This first code block creates a dataframe with a NaN value in one row&#58;<br></p><p class="ssw15-rteElement-CodeArea">import datetime​<br>import math​<br>import pandas as pd<br>import numpy as np<br><br>todays_date = datetime.datetime.now().date()<br>index = pd.date_range(todays_date-datetime.timedelta(10), periods=4, freq='D')<br>columns = ['A','B', 'C']<br>df = pd.DataFrame(index=index, columns=columns)<br>df = df.fillna(0)&#160;<br><br>df.set_value('2017-04-16', 'B', math.nan) #set one value in NaN<br><br>df.head()​<br></p><p class="ssw15-rteElement-P">Dataframe output&#58;<br></p><table cellspacing="0" width="100%" class="ssw15-rteTable-default" summary="5"><tbody><tr class="ssw15-rteTableHeaderRow-default"><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;150px;"> 
            <br> 
         </th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;100px;">​A<br></th><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;100px;">​B<br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;100px;">​C<br></th></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default" style="width&#58;150px;">​2017-04-14​<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">0<br></td><td class="ssw15-rteTableEvenCol-default" colspan="1" style="width&#58;100px;">0<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">0​<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default" style="width&#58;150px;">2​017-04-15<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">​0<br></td><td class="ssw15-rteTableEvenCol-default" colspan="1" style="width&#58;100px;">​0<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">​0<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default" style="width&#58;150px;">​2017-04-16<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">​0<br></td><td class="ssw15-rteTableEvenCol-default" colspan="1" style="width&#58;100px;">​NaN<br><br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">​0<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default" style="width&#58;150px;">​2017-04-17<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">0<br></td><td class="ssw15-rteTableEvenCol-default" colspan="1" style="width&#58;100px;">0<br></td><td class="ssw15-rteTableOddCol-default" style="width&#58;100px;">0​<br></td></tr></tbody></table><p class="ssw15-rteElement-P">​​​​​Filtering out this row is simple using a square bracket filter expression. &#160;Here we are filtering using the Numpy isfinite method on column B to exclude the problematic row&#58;<br></p><p class="ssw15-rteElement-CodeArea">df = df.loc[np.isfinite(df['B'])] #filter out the NaN row<br>df.head()​<br></p><p class="ssw15-rteElement-P">Dataframe output&#58;​<br></p><table cellspacing="0" width="100%" class="ssw15-rteTable-default"><tbody><tr class="ssw15-rteTableHeaderRow-default"><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;25%;">​<br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;25%;">​A<br></th><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;25%;">​B<br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;25%;">​C<br></th></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​2017-04-14​<br></td><td class="ssw15-rteTableOddCol-default">​0​​​<br></td><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​0<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​2​017-04-15<br></td><td class="ssw15-rteTableOddCol-default">​0<br></td><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​0<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​2017-04-17<br></td><td class="ssw15-rteTableOddCol-default">​0<br></td><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​0<br></td></tr></tbody></table><p> 
   <br>There is also inbuilt functionality in a dataframe to fill values by interpolation&#160;or by taking the mean value of a column. &#160;In the dataframe sample below, it is clear that this is a relationship between row values, with each row showing an increase in the values of each column, making interpolation a valid technique for filling missing data.<br></p><p>This first code sample great a dataframe with a number of rows with incomplete data.<br></p><p class="ssw15-rteElement-CodeArea">df2 = pd.DataFrame(&#123;'Col1'&#58; [1, 2, np.nan, 4.8, 6],'Col2'&#58; [11, np.nan, np.nan, 16, 28]&#125;)<br>df2</p><table cellspacing="0" width="100%" class="ssw15-rteTable-default"><tbody><tr class="ssw15-rteTableHeaderRow-default"><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​​<br><br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col1<br></th><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col2<br></th></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​1.0<br></td><td class="ssw15-rteTableEvenCol-default">​11.0<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​1<br></td><td class="ssw15-rteTableOddCol-default">​2.0<br></td><td class="ssw15-rteTableEvenCol-default">​NaN<br><br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​2<br></td><td class="ssw15-rteTableOddCol-default">​NaN<br><br></td><td class="ssw15-rteTableEvenCol-default">​NaN<br><br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​3<br></td><td class="ssw15-rteTableOddCol-default">​4.8<br></td><td class="ssw15-rteTableEvenCol-default">16.0<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default" rowspan="1">​4<br></td><td class="ssw15-rteTableOddCol-default" rowspan="1">​6.0<br></td><td class="ssw15-rteTableEvenCol-default" rowspan="1">​28.0<br></td></tr></tbody></table><p class="ssw15-rteElement-P">​​​​The dataframe's&#160;inbuilt&#160;interpolate method is then used to fill the missing values. &#160;The default behaviour of&#160;interpolate is to use a linear interpolation, but a number of more advanced algorithms are also available. &#160;See the <a href="http&#58;//pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.interpolate.html">interpolation documentation​</a> for more information.<br></p><p class="ssw15-rteElement-CodeArea">df2 = df2.interpolate()<br>df2</p><table cellspacing="0" width="100%" class="ssw15-rteTable-default"><tbody><tr class="ssw15-rteTableHeaderRow-default"><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​​<br><br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col1<br></th><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col2<br></th></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​1.0<br></td><td class="ssw15-rteTableEvenCol-default">​11.0<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​1<br></td><td class="ssw15-rteTableOddCol-default">​2.0<br></td><td class="ssw15-rteTableEvenCol-default">​12.66667<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​2<br></td><td class="ssw15-rteTableOddCol-default">​3.4<br></td><td class="ssw15-rteTableEvenCol-default">​14.33333<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​3<br></td><td class="ssw15-rteTableOddCol-default">​4.8<br></td><td class="ssw15-rteTableEvenCol-default">16.0<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default" rowspan="1">​4<br></td><td class="ssw15-rteTableOddCol-default" rowspan="1">​6.0<br></td><td class="ssw15-rteTableEvenCol-default" rowspan="1">​28.0<br></td></tr></tbody></table>​In this code sample, the mean value of a column is used to fill missing data.<br>
<p class="ssw15-rteElement-CodeArea">df3&#160;= pd.DataFrame(&#123;'Col1'&#58; [1, 2, np.nan, 4.8, 6],'Col2'&#58; [11, np.nan, np.nan, 16, 28]&#125;)<br>df3<br></p><table cellspacing="0" width="100%" class="ssw15-rteTable-default"><tbody><tr class="ssw15-rteTableHeaderRow-default"><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​​<br><br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col1​<br><br></th><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col2<br></th></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​1.0<br></td><td class="ssw15-rteTableEvenCol-default">​11.0<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​1<br></td><td class="ssw15-rteTableOddCol-default">​2.0<br></td><td class="ssw15-rteTableEvenCol-default">​NaN<br><br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​2<br></td><td class="ssw15-rteTableOddCol-default">​NaN<br><br></td><td class="ssw15-rteTableEvenCol-default">​NaN<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​3<br></td><td class="ssw15-rteTableOddCol-default">​4.8<br></td><td class="ssw15-rteTableEvenCol-default">16.0<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default" rowspan="1">​4<br></td><td class="ssw15-rteTableOddCol-default" rowspan="1">​6.0<br></td><td class="ssw15-rteTableEvenCol-default" rowspan="1">​28.0<br></td></tr></tbody></table><p class="ssw15-rteElement-CodeArea">df3 = df3.fillna(df3.mean())<br>df3<br></p><table cellspacing="0" width="100%" class="ssw15-rteTable-default"><tbody><tr class="ssw15-rteTableHeaderRow-default"><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​​<br><br></th><th class="ssw15-rteTableHeaderOddCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col1<br></th><th class="ssw15-rteTableHeaderEvenCol-default" rowspan="1" colspan="1" style="width&#58;33.3333%;">​Col2<br></th></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​0<br></td><td class="ssw15-rteTableOddCol-default">​1.0<br></td><td class="ssw15-rteTableEvenCol-default">​11.0<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​1<br></td><td class="ssw15-rteTableOddCol-default">​2.0<br></td><td class="ssw15-rteTableEvenCol-default">18.33<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default">​2<br></td><td class="ssw15-rteTableOddCol-default">​3.45<br></td><td class="ssw15-rteTableEvenCol-default">​18.33​<br></td></tr><tr class="ssw15-rteTableEvenRow-default"><td class="ssw15-rteTableEvenCol-default">​3<br></td><td class="ssw15-rteTableOddCol-default">​4.8<br></td><td class="ssw15-rteTableEvenCol-default">16.0<br></td></tr><tr class="ssw15-rteTableOddRow-default"><td class="ssw15-rteTableEvenCol-default" rowspan="1">​4<br></td><td class="ssw15-rteTableOddCol-default" rowspan="1">​6.0<br></td><td class="ssw15-rteTableEvenCol-default" rowspan="1">​28.0<br></td></tr></tbody></table>​<h3 class="ssw15-rteElement-H3">Data Cleaning and&#160;Inference&#160;Techniques​ in Azure Machine Learning<br></h3><p>Azure ML has a specific step for cleaning missing data. &#160;The step allows the relevant columns to be selected, the minimum and maximum missing value ratios and the cleaning mode to be used. &#160;The ratios are used to control when cleaning is applied - the default values of 0 and 1 allow cleaning to be applied on all rows, but if the cleaning should only be applied in cases where 20% to 30% of the values are missing, the values would be set to 0.2 for the minimum and 0.3 for the maximum.<br></p><p>In addition to the simple cleaning methods such as removing the row or replacing it with the mean, much more complex methods such as Replace with MICE are available. &#160;MICE stands for&#160;Multivariate Imputation using Chained Equations, and is an inference technique that uses the distribution of values across all columns to calculate the best fitting substitution for missing values. &#160;For example, to fill in the missing values in a&#160;person's&#160;weight column, the information in other columns such as gender and age will be used to predict the best fit for the missing data. &#160;The academic paper&#160;<a href="https&#58;//www.ncbi.nlm.nih.gov/pmc/articles/PMC3074241/">Multiple Imputation by Chained Equations&#58; What is it and how does it work?​</a> gives a great explanation​ of the workings of the MICE algorithm.<br><br><br></p><p><img src="/PublishingImages/DataScience5.png" alt="" style="margin&#58;5px;" /><br></p><h3 class="ssw15-rteElement-H3">Next Steps​​<br><br></h3>Once your data is clean, the next steps are to either move into <a href="/_layouts/15/FIXUPREDIRECT.ASPX?WebId=3dfc0e07-e23a-4cbb-aac2-e778b71166a2&amp;TermSetId=07da3ddf-0924-4cd2-a6d4-a4809ae20160&amp;TermId=469a0a07-5674-4325-9a0d-b4017fd2aaca">in-depth analysis in a Azure Notebook </a>or to use <a href="/_layouts/15/FIXUPREDIRECT.ASPX?WebId=3dfc0e07-e23a-4cbb-aac2-e778b71166a2&amp;TermSetId=07da3ddf-0924-4cd2-a6d4-a4809ae20160&amp;TermId=eee0badc-5ce6-4008-9fea-994699b4e62c">Azure Machine Learning to look at advanced data prediction and classification​</a>.<br><br><br><br><br><br><br><br><br><br><br><br><br>

