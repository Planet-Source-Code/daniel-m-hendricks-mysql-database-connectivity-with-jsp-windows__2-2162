<div align="center">

## MySQL Database Connectivity with JSP \(Windows\)


</div>

### Description

A tutorial on how to get started with JavaServer pages using Sun's Tomcat web server (a Jakarta variant) and connecting to a MySQL database to retrieve data. Provided as a jumpstart for practicing with real-world applications. Tutorial is intended for users who may have had previous web/database experience but would like to get their feet wet in JSP. (Updated October 04, 2002)
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Daniel M\. Hendricks](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/daniel-m-hendricks.md)
**Level**          |Intermediate
**User Rating**    |4.6 (143 globes from 31 users)
**Compatibility**  |Java \(JDK 1\.1\), Java \(JDK 1\.2\)
**Category**       |[Databases/ JDBC](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/databases-jdbc__2-61.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/daniel-m-hendricks-mysql-database-connectivity-with-jsp-windows__2-2162/archive/master.zip)





### Source Code


<br><p><font face="Arial" size="2"><font face="Times New Roman" size="3">This
tutorial will show you how to connect to a MySQL database using JSP (JavaServer
Pages) under Windows and Tomcat web server.&nbsp; If you run into problems or find
errors, please let me know so I can fine-tune this document.&nbsp; This document will
probably be most useful for those who have done web scripting with MySQL
databases before but would like to get started with JSP/Servlets programming.&nbsp;
Database connectivity provides a good foundation for learning any new language,
as you can practice making real-world applications in a database environment.</font><font face="Times New Roman">
</font></p>
<p><b><font face="Arial, Helvetica" size="2">Requirements:</font></b></p>
<ol>
 <li><font face="Times New Roman" size="3">MySQL<br>
 <a href="http://www.mysql.com" target="_blank">http://www.mysql.com</a></font>
 </li>
 <li><font face="Times New Roman" size="3">Tomcat - version 4.1.12 Standard
 used for this tutorial<br>
 <a href="http://jakarta.apache.org/site/binindex.html" target="_blank">
 http://jakarta.apache.org/site/binindex.html</a></font> </li>
 <li><font face="Times New Roman" size="3">Java 2 JRE - version 1.4.1 used for
 this tutorial<br>
 <a href="http://java.sun.com/j2se/1.4.1/download.html">
 http://java.sun.com/j2se/1.4.1/download.html</a></font> </li>
 <li><font face="Times New Roman">MySQL Connector/J</font><font face="Times New Roman" size="3">
 - version 2 used for this tutorial<br>
 <a href="http://www.mysql.com/downloads/api-jdbc.html">
 http://www.mysql.com/downloads/api-jdbc.html</a></font> </li>
</ol>
<p><b><font face="Arial, Helvetica" size="2">Assumptions:</font></b></p>
<ol>
 <li><font face="Times New Roman" size="3">It is assumed that you already have
 a MySQL database installed and a table to pull data from.</font> </li>
 <li><font face="Times New Roman" size="3">It assumes you understand SQL, and
 probably have done some web/database scripting with other languages.</font>
 </li>
 <li><font face="Times New Roman" size="3">The author uses the folder C:\Tomcat
 as the folder where Tomcat will be extracted, however, you can place the
 distribution files anywhere you wish.</font> </li>
 <li><font face="Times New Roman" size="3">You know the basics of programming
 Java.&nbsp; If you do not, I <b>highly</b> recommend you check out Sun's
 <a href="http://java.sun.com/docs/books/tutorial/" target="_blank">Java
 Tutorial</a>.&nbsp;</font> </li>
</ol>
<p><b><font face="Arial, Helvetica" size="3">Section A - Installation</font></b></p>
<ol>
 <li><font face="Times New Roman" size="3">Install the Java 2 JRE.&nbsp; I put mine
 in </font><font face="Courier New" size="2">C:\java\jre</font><font face="Times New Roman" size="3">,
 which will be used in this tutorial, but you can put your anywhere you like.&nbsp;</font>
 </li>
 <li><font face="Times New Roman" size="3">Extract the Tomcat distribution
 files to a folder.&nbsp; The default is </font><font face="Courier New" size="2">
 jakarta-tomcat-4.1.12</font><font face="Times New Roman" size="3">, but I
 chose to put the files in </font><font face="Courier New" size="2">C:\Tomcat</font><font face="Times New Roman" size="3">.</font>
 </li>
 <li><font face="Times New Roman" size="3">Copy the MySQL Connector JAR file to
 the </font><font face="Courier New" size="2">C:\Tomcat\common\lib</font><font face="Times New Roman" size="3">
 folder (ie, mysql-connector-java-2.0.14.jar).</font> </li>
</ol>
<p><font face="Arial, Helvetica" size="3"><b>Section B - Environmental Variables</b></font></p>
<p><font face="Times New Roman" size="3">Add the following environmental
variables to Windows:</font></p>
<div align="left">
 <table border="0">
  <tr>
   <td width="30">&nbsp;</td>
   <td><font face="Courier New" size="2">JAVA_HOME=C:\java\jre<br>
   TOMCAT_HOME=C:\Tomcat</font></td>
  </tr>
 </table>
</div>
<p><font face="Times New Roman" size="3">You can set environmental variables in
Windows 2000/XP by going to:<br>
Righy-click My Computer -&gt; Properties -&gt; Advanced -&gt; Environmental Variables</font></p>
<p><font face="Times New Roman" size="3">You can set environmental variables in
Windows NT 4 by going to:<br>
Righy-click My Computer -&gt; Properties -&gt; Environment&nbsp;</font></p>
<p><b><font face="Arial, Helvetica" size="3">Section C - Working with Tomcat</font></b></p>
<p align="left"><font face="Times New Roman" size="3">To start the server,
execute </font><font face="Courier New" size="2">startup.bat</font><font face="Times New Roman" size="3">.&nbsp;
To stop the server, execute </font><font face="Courier New" size="2">
shutdown.bat </font><font face="Times New Roman" size="3">in the </font>
<font face="Courier New" size="2">C:\Tomcat\bin</font><font face="Times New Roman" size="3">
folder.</font></p>
<p><font face="Times New Roman" size="3">By default, the Tomcat web server is
access at this URL:<br>
</font><a href="http://localhost:8080/"><font face="Times New Roman" size="3">
http://localhost:8080/</font></a></p>
<p><font face="Times New Roman" size="3">The root folder of the server is
located in:</font><br>
<font face="Courier New" size="2">C:\Tomcat\webapps\ROOT</font></p>
<p><font face="Times New Roman" size="3">The root and default port can be
changed in this file:</font><br>
<font face="Courier New" size="2">C:\Tomcat\conf\server.xml</font></p>
<p><font face="Arial, Helvetica" size="3"><b>Section D - Write Your Code!</b></font></p>
<p><font face="Times New Roman" size="3">You can now start writing your JSP
scripts.&nbsp; Save it in a file with a JSP extension and place it in the ROOT
folder.&nbsp; I have provided a simple JSP script that demonstrates how to connect to
a list data from a MySQL database.</font></p>
<font color="#ff0000" size="2"><b>
<p><font face="Courier New">&lt;%</font></b></font><font face="Courier New"><font size="2">@
page import=</font><font color="#0000f0" size="2">&quot;java.sql.*&quot;</font><font size="2">
<b>%&gt;</b></font><font color="#ff0000" size="2"><b><br>
&lt;%</b></font><font size="2"><br>
String connectionURL = </font><font color="#0000f0" size="2">&quot;jdbc:mysql://localhost:3306/mydatabase?user=;password=&quot;</font><font size="2">;<br>
Connection connection = </font><font color="#800000" size="2"><b>null</b></font><font size="2">;<br>
Statement statement = </font><font color="#800000" size="2"><b>null</b></font><font size="2">;<br>
ResultSet rs = </font><font color="#800000" size="2"><b>null</b></font><font size="2">;<br>
</font></font><font color="#ff0000" size="2"><b><font face="Courier New">%&gt;</font></p>
</b></font>
<p><font face="Courier New" color="#0000c0" size="2">&lt;html&gt;&lt;body&gt;</font></p>
<b><font color="#ff0000" size="2">
<p><font face="Courier New">&lt;%</font></font><font face="Courier New" size="2"><br>
Class</font></b><font face="Courier New"><font size="2">.forName(</font><font color="#0000f0" size="2">&quot;com.mysql.jdbc.Driver&quot;</font><font size="2">).newInstance();<br>
connection = DriverManager.getConnection(connectionURL, </font>
<font color="#0000f0" size="2">&quot;&quot;</font><font size="2">, </font>
<font color="#0000f0" size="2">&quot;&quot;</font><font size="2">);<br>
statement = connection.createStatement();<br>
rs = statement.executeQuery(</font><font color="#0000f0" size="2">&quot;SELECT * FROM
mytable&quot;</font><font size="2">);</font></font></p>
<p><font face="Courier New"><font size="2"><b>while</b> (rs.next()) {<br>
out.println(rs.getString(</font><font color="#0000f0" size="2">&quot;myfield&quot;</font><font size="2">)+</font><font color="#0000f0" size="2">&quot;&lt;br&gt;&quot;</font><font size="2">);<br>
}</font></font></p>
<p><font face="Courier New" size="2">rs.close();</font><font color="#ff0000" size="2"><b><font face="Courier New"><br>
%&gt;</font></p>
</b></font>
<p><font face="Courier New" color="#0000c0" size="2">&lt;/body&gt;&lt;/html&gt;</font></p>
<p>&nbsp;<br>
<font face="Times New Roman" size="3">Obviously, you will want to change the <i>
username</i> and <i>password</i> to match your database.&nbsp; Also, the <i>
mydatabase</i> value in the connectionURL represents the name of the MySQL
database.&nbsp; Change appropriately.&nbsp; Finally, change the <i>mytable </i>and <i>
myfield</i> values in the script to match a table and field that exist within
your database.&nbsp; If the public is granted access to the database, you can use
this as your connectionURL:</font></p>
<p><font face="Courier New"><font size="2">String connectionURL = </font>
<font color="#0000f0" size="2">&quot;jdbc:mysql://localhost:3306/mydatabase&quot;</font><font size="2">;</font></font></p>
<p><font face="Times New Roman" size="3">Happy coding!</font></p>
</font>

