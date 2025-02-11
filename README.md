
Cross-Platform Agile.NET 
======== 

<img src="squirrel_logo.png" border="0" height="250" width="300">
The Cross Platform Agile Data Analytics for .NET 
------------------------------------------------
<img src="https://www.pocketsolution.net/img/mac-linux-windows.png"/>

Squirrel is built on .NET Standard 2.0

<!--<a href="Squirrel"><img src="https://raw.github.com/sudipto80/Squirrel/newb/img/icon_26718.png" align="left" t="100" width="100" ></a>-->


Why this?
------------
Data Analytics and Big Data, are now the buzz words of the industry. Today many Businesses want to drive their businesses using Data Analytics – by gaining insights from their data. Aesthetically pleasing data visualizations with agility are key for effective discovery of insights. And better insight requires a bunch of special skills – an expertise in the field of [Data Science](http://en.wikipedia.org/wiki/Data_science). But are Data Scientists easy to come by?
Most of the datasets used by the businesses are not anywhere near Big. Actually they are Tiny to Medium. A typical dataset has only few thousand rows! 

|Dataset Size| Name |
:------------|:------|
|Dataset that can fit in your mobile phone |Tiny |
|Dataset that can fit in your laptop (1GB) |Small |
|Dataset that can fit in your workstation (4 GB) |Medium |
|Dataset that can fit in your server | Large |
|When clusters of your servers struggle| Big|


Businesses are so sold up to the idea of Big data (it has almost become a status symbol) that they ignore the power of small data tools developed in-house in deriving their insights. So could software developers replace the need of the Data Scientist in answering most questions that involve Tiny or Medium datasets?
Business users (Operational Managers, System Engineers, Financial and Planning Analysts, DevOps, etc.), often want to initiate the analysis and gain insight into the business on their personal devices. But they cannot because of the special skills and training needed to perform such actions. Their outlook thus remains limited by the canned reports/insights offered by their backend. Could a Business user acquire, generate and visualize data of his choice, without knowing the details of data organization or query syntax?

This is not only answers the above questions but also tries to fulfill the lack of a good data processing and analytics tool or framework to the large .NET developer ecosystem.

This seeks to simplify the task of discovering insights by bringing to the software developer a templatized design style for answering most common problems in data science. Readymade functions bring the agility in developing a solution or a storyline from any data.

This brings the application closer to the Business user by delivering the ability to acquire and visualize data from a variety of sources to their personal devices. We envision smart abilities that would bring agile data analytic solution development and delivery to near real time.

The framework development is very active right now and early adopters can benefit by shaping up the design by requesting features. It's is a simple and easy to use interface for querying and reporting of data. APIs for Data acquisition, Data filtering, Data cleansing, etc. provide simple solution, often in one step, for many real world problems. 

Data analytics solution development follows a templatized design style. As a Data Scientist would, a software developer using too would solve a data analytics problem by stacking his solution starting with Data acquisition, followed by Data modeling & cleansing and then topping up with appropriate Data visualization. Applying Bootstrap to the visualization is automatic, bringing agility to development without compromising on quality of user experience. The following figure describes a stacked template of function blocks that aptly summarizes solution development.

Here is a high level block diagram of all the components.
<img src="squirrel_block.png"/>

Key Design Philosophy
---------------------
Here are couple of design decisions that have been the guiding principle for the choice of internal data structure for ```Table``` data structure to make data accessing/manipulating more intuitive and efficient at the same time.
* Each row in the table should be available by zero based integer indexing as we do in arrays and ```List<T>``` So if a table ```birthRates``` exists then we should be able to get to 10th row by the syntax ```birthRates[9]```
* A column at a given index should be available by the column name index. So if we have a table ```StockValues``` that stores average stock values in a year of different companies where the row depicts the year and the column depicts the company for which the stock price is stored, then we should be able to get the stock price for Microsoft (Symbol “MSFT”) for 5th year as ```StockValues[4][“MSFT”]```
* Value at row ```“k”``` (Expressed as an integer) and column ```“m”``` (Expressed as a string) has to be accessible by either of the syntax ```table[k][“m”]``` or ```table[“m”][k]```.


API Overview
------------

1. **BasicStatistics** - Basic statistical functions like Median, Range, Standard Deviation, Kurtosis, etc.
2. **CustomComparers** - Several customized comparators for sorting data.
3. **DataAcqusition** - Data loaded/dumped from/to various formats, e.g. CSV, TSV, HTML, ARFF, etc.
4. **DatabaseConnectors** - Data can be loaded from popular DB repositories by using the connectors for SQL Server and MongoDB.
5. **DataCleansers** - Extraction/Removal of outliers or data that matches specific boolean criteria.
6. **OrderedTable** - A data structure to hold sort results temporarily.
7. **Table** - An ubiquitous data structure used to encapsulate the data. Several APIs are part of the *Table* -
   * Filter data using regular expressions or SQL clause.
   * Sort data based on columns and their values.
   * Programmatic manipulation i.e. deletion, updation and insertion of data.
   * Merge data columns; Find subsets and exclusive or common rows in tables.
   * Other utilities to split or drop data columns; Find rows that meet a specific statistical critieria, e.g. top 10, below average, etc.
   * Natural queries

[Here](https://raw.github.com/sudipto80/Squirrel/newb/doc/TableAPI.chm) is the detailed API documentation.

Dependency
----------

There is a dependency for [NCalc2](https://github.com/sklose/NCalc2) for the following methods 
```csharp
AddColumn() 
AddRows()
AddRowsByShortHand()
``` 

NuGet Package
-------------
![image](https://user-images.githubusercontent.com/1287634/182864139-eaa07abf-4ff7-46cd-82cc-798ea39c2b1c.png)


You can integrate the package using NuGet by giving the following command</br>

```
PM> Install-Package TableAPI 
```

[Here is the NuGet Package page](https://www.nuget.org/packages/TableAPI/)

Although the package is named `TableAPI` the namespaces to import is 

```csharp

using Squirrel

``` 

and in F# 

```fsharp 

open Squirrel
open Squirrel.FSharp

```

Unit Tests
----------
To run unit tests. Use the following .NET CLI command 

```batch
dotnet test SquirrelTests/
``` 


