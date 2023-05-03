Download Link: https://assignmentchef.com/product/solved-cpsc375-project-2-linear-modeling-on-apache-spark-platform
<br>



The goal of this project is to redo the linear modeling of only the best model from your Project 1 but on an Apache Spark platform. You should use R’s sparklyr package to talk to an Apache Spark instance. The two tasks are:

<ol>

 <li>Install sparklyr and Apache Spark on your computer</li>

 <li>Run R code that uses Spark to redo the linear modeling</li>

</ol>

Note that it is not required to redo the exploratory data analysis in Project 1.

Installing sparklyr and Apache Spark :

It is easiest to install from within RStudio (assuming that the tidyverse library is also installed).

<ol>

 <li>Install package “sparklyr”</li>

 <li>Load the sparklyr library and install Apache Spark using sparklyr:</li>

</ol>

○ library(sparklyr)

○ spark_install()




This should work in either Windows or Linux. More detailed instructions for installing on Linux from scratch is included at the end.

Linear modeling in Spark

This code will be very similar to the code shown in class. Use the same data file from Project 1.

&gt; mylocaldata &lt;- read_csv

(“http://staff.pubhealth.ku.dk/~tag/Teaching/share/data/Bodyfat.csv”)

&gt; library(sparklyr)

&gt; sc &lt;- spark_connect(master = “local”)

&gt; myremotedata &lt;-​ copy_to(sc, mylocaldata​ )​

&gt; mymodel &lt;- ml_linear_regression(x=myremotedata ​ , formula =​ bodyfat ~ Weight + Height) &gt; summary(mymodel)

<em> </em>

You will edit the above code to use the specific variables you used and perform any transformations that you used.




<strong>Appendix</strong>. Installation on Linux/Tuffix:​

You may want to try out “Tuffix”, the Titan-branded version of Ubuntu 18.04.  Instructions on how to install Tuffix or a Tuffix-based VM are in the Tuffix Titanium Community for Students, <a href="https://communities.fullerton.edu/course/view.php?id=1547">https://communities.fullerton.edu/course/view.php?id=1547</a> <u>​ </u>(also the best venue to receive help with Tuffix). It is easiest to install into a Linux (virtual) machine. Then install R or Rstudio, install the sparklyr package inside R/Rstudio, and then use sparklyr’s install.spark() function to do the Spark installation.

<ol>

 <li>To install R, from the Linux command line:</li>

</ol>

&gt; sudo apt install r-base

<ol start="2">

 <li>To install RStudio:</li>

</ol>

&gt;    Download the latest version (as a .deb file) from <a href="https://www.rstudio.com/products/rstudio/download/#download">https://www.rstudio.com/products/rstudio/download/#download</a>

&gt; sudo apt install gdebi

&gt; sudo gdebi &lt;location of downloaded rstudio .deb file&gt;

<ol start="3">

 <li>Make sure Java 8 is used.</li>

</ol>

&gt; sudo apt install openjdk-8-jdk

&gt; sudo update-alternatives –config java

■    This will show all currently installed versions of Java. Select Java 8 (openjdk-8-jdk)

<ol start="4">

 <li>Install the sparklyr package inside R/Rstudio:</li>

</ol>

&gt; install.packages(“tidyverse”)

■    If there are errors during installation of tidyverse, make sure these libraries are installed

<ol>

 <li>sudo apt-get install libxml2-dev

  <ul>

   <li>(for package xml2)</li>

  </ul></li>

 <li>sudo apt-get install libcurl4-gnutls-dev

  <ul>

   <li>(for package curl)</li>

  </ul></li>

</ol>

&gt; install.packages(“sparklyr”)




<ol start="5">

 <li>Install spark from inside R/Rstudio<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a></li>

</ol>

&gt; library(sparklyr)

&gt; install.spark()







<a href="#_ftnref1" name="_ftn1">[1]</a> The above instructions install spark to a local folder. You can also install to a system-wide​            folder, a install a specific version of Spark, or use an existing installation of Spark.


