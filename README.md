Download Link: https://assignmentchef.com/product/solved-cse-231-project-9
<br>
<h2>Assignment Overview</h2>

(learning objectives)

This assignment will give you more experience on the use of:

<ul>

 <li>lists</li>

 <li>dictionaries</li>

 <li>data structures</li>

 <li>functions</li>

 <li>iteration</li>

 <li>data analysis</li>

</ul>




The goal of this project is to analyze data relevant to the recent Novel Coronavirus (nCoV) outbreak.

<strong> </strong>

<h2>Assignment Background</h2>

<strong> </strong>

The 2019-nCoV is a newly discovered contagious virus that is causing respiratory infections. It is confirmed to be a zoonotic virus, meaning it can spread from person to person, and was first known to cause a human infection in December 2019. Any further information about the situation should only be acquired from trusted sources such as the <a href="https://www.cdc.gov/coronavirus/2019-nCoV/summary.html">CDC</a><a href="https://www.cdc.gov/coronavirus/2019-nCoV/summary.html">.</a>

<strong> </strong>

<h2>Project Description</h2>




This project focuses on analyzing <a href="https://www.kaggle.com/sudalairajkumar/novel-corona-virus-2019-dataset/data">a publicly available dataset</a> containing information about the spread of nCoV. Since this is an active situation, this dataset is constantly being updated with the latest figures. However, for our purposes, we will use a static version of the dataset provided to you with this project (Another file (ncov_small.csvncov.csv)). This static version was lasted updated on March  was last updated February 5th. 18<sup>th</sup>. <strong> </strong>

<h2>open_file() -&gt; fp</h2>




This function takes no parameters and returns a file pointer to the data file.  You likely have a copy from a previous project.  It repeatedly prompts for a file until one is successfully opened.  It <em>should</em> have a try-except statement. By default (when the user does not provide a filename), this function opens the file ‘ncov.csv’.




<strong> </strong>

<strong> </strong>

<strong> </strong>

<h2>build_dictionary(fp) -&gt; dictionary</h2>




This function accepts the previously generated file pointer as input and returns the required dictionary. You have to use csv.reader to read the data file since the area name has a comma. This function iterates over the CSV reader and within each iteration, extracts the needed data and then creates a dictionary that holds all of the data. Remember to skip the header line. Also, the order of countries and areas in the dictionary will be the same as the order observed in the CSV file. This dictionary is then returned by the function. The data to be extracted is:




Country – column 3

Area – column 2

Last update – column 4

Cases – column 5

Deaths – column 6

Recovered – column 7




The structure of the dictionary is as follows:

{country: [{area : (last_update, cases, deaths, recovered)},…]}

The dictionary contains a list of dictionaries. Each dictionary within the list has the key as the area within the country and value as a tuple. This tuple contains last updated date, numbers of cases, number of deaths, and number of recovered respectively.




For example:

<table width="637">

 <tbody>

  <tr>

   <td width="70">1</td>

   <td width="116">Area</td>

   <td width="112">Country/Region</td>

   <td width="110">Last Update</td>

   <td width="80">Confirmed</td>

   <td width="70">Deaths</td>

   <td width="80">Recovered</td>

  </tr>

  <tr>

   <td width="70">54</td>

   <td width="116">Chicago, IL</td>

   <td width="112">US</td>

   <td width="110">2/1/2020 19:43</td>

   <td width="80">2</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">55</td>

   <td width="116">San Benito, CA</td>

   <td width="112">US</td>

   <td width="110">2/3/2020 3:53</td>

   <td width="80">2</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">56</td>

   <td width="116">Santa Clara, CA</td>

   <td width="112">US</td>

   <td width="110">2/3/2020 0:43</td>

   <td width="80">2</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">67</td>

   <td width="116">Boston, MA</td>

   <td width="112">US</td>

   <td width="110">2/1/2020 19:43</td>

   <td width="80">1</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">68</td>

   <td width="116">Los Angeles, CA</td>

   <td width="112">US</td>

   <td width="110">2/1/2020 19:53</td>

   <td width="80">1</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">69</td>

   <td width="116">Orange, CA</td>

   <td width="112">US</td>

   <td width="110">2/1/2020 19:53</td>

   <td width="80">1</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">70</td>

   <td width="116">Seattle, WA</td>

   <td width="112">US</td>

   <td width="110">2/1/2020 19:43</td>

   <td width="80">1</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

  <tr>

   <td width="70">71</td>

   <td width="116">Tempe, AZ</td>

   <td width="112">US</td>

   <td width="110">2/1/2020 19:43</td>

   <td width="80">1</td>

   <td width="70">0</td>

   <td width="80">0</td>

  </tr>

 </tbody>

</table>




The dictionary will be:




{‘US’:

[{‘Chicago, IL’: (‘2/1/2020 19:43’, 2, 0, 0)}, {‘San Benito,

CA’: (‘2/3/2020 3:53’, 2, 0, 0)}, {‘Santa Clara, CA’: (‘2/3/2020

0:43’, 2, 0, 0)}, {‘Boston, MA’: (‘2/1/2020 19:43’, 1, 0, 0)}, {‘Los Angeles, CA’: (‘2/1/2020 19:53’, 1, 0, 0)}, {‘Orange, CA’:

(‘2/1/2020 19:53’, 1, 0, 0)}, {‘Seattle, WA’: (‘2/1/2020 19:43’,

1, 0, 0)}, {‘Tempe, AZ’: (‘2/1/2020 19:43’, 1, 0, 0)}] }




A missing entry for area should be treated as ‘N/A’ in the dictionary. Example:

{‘Belgium’: [{‘N/A’: (‘2/4/2020 15:43’, 1, 0, 0)}]} <strong>top_affected_by_spread(dictionary) -&gt; list </strong>




This function accepts the data dictionary as created by the function above and returns a <em>sorted </em>list (in descending order) of the top 10 countries with the most areas affected by nCoV. The returned list will contain 10 tuples, each tuple containing the country name and total areas affected in that country. For example, in the case of Australia (“ncov_small.csv”), the tuple will be as follows:




(‘Australia’, 4)




There are 4 affected areas in Australia as shown  in the dictionary:




[{‘New South Wales’: (‘2/1/2020 18:12’, 4, 0, 2)}, {‘Victoria’:

(‘2/1/2020 18:12’, 4, 0, 0)}, {‘Queensland’: (‘2/4/2020 16:53’,

3, 0, 0)}, {‘South Australia’: (‘2/2/2020 22:33’, 2, 0, 0)}]




Remember to sort before returning the list, first by most affected (descending) and then in alphabetical order (ascending) to break ties. You will find itemgetter() useful here. You should remember that your primary key is the total areas affected.




<h2>top_affected_by_numbers(dictionary) -&gt; list</h2>




This function accepts the data dictionary and produces a sorted list of the top 10 countries with the most total people affected within every country. This is similar to the previous function, except that instead of counting the total areas affected, we are counting the total people affected in each country. For these counts, we use the numbers in the ‘cases’ column. The returned sorted list (in descending order) will contain key-value pairs such that each key is a country and the corresponding value is the number of cases observed within that country. For example, in the case of Australia and Malaysia, the tuple will be as follows:




[(‘Australia’, 13),(‘Malaysia’: 10)]

<h2> affected_states_in_country(dictionary, string) -&gt; set</h2>




This function takes in the data dictionary and the name of a country (string) and returns a set of affected areas within a country (if you are curious, the function name contains the word “states” which is what we started with but changed descriptions to be “areas” as new data came in—the function name wasn’t changed). The function should return an empty set if the user enters a non-existent country name. The string representing the country may be any mixture of cases, e.g. “China” is equivalent to “cHiNa” which is equivalent to “chiNA” etc.




<h2>is_affected(dictionary, string) -&gt; Boolean</h2>




This function takes in the data dictionary and the name of a country (string) and returns a

Boolean (True or False) depending on whether a country is affected by nCoV. A country is affected by nCoV, if it is in the dictionary.  The string representing the country may be any mixture of cases, e.g. “China” is equivalent to “cHiNa” which is equivalent to “chiNA” etc.




<h2>plot_by_numbers(list, list) -&gt; plot</h2>

This function is provided. You do not need to modify the source code for this function. However, you do need to invoke this function at the appropriate place. This function accepts a list of countries and a list of numbers corresponding to those countries and generates a graph using this data.




<h2>main()</h2>




Begin by opening the file and building the master_dictionary by calling the appropriate functions. The main function prints the provided BANNER and MENU and then asks the user to make a choice between the various available options shown in the menu. If the user inputs something other than an integer, print an error message and reprompt.




If the choice is 1, the program compiles a list of countries with the most (top) areas affected by calling the appropriate function and then displays the results to the user in descending order. Use the following string formatting: “{:&lt;20s} {:5d}”

It then asks the user if they want to plot the results. Depending on user’s response, plot can be displayed. Plot only the top 5 countries and their corresponding area counts.  Make a list of countries and a list of their counts to use as arguments to the plotting function.




If the choice is 2, the program compiles a list of countries with the most people affected by calling the appropriate function and then displays the results to the user in descending order.  Use the following string formatting: “{:&lt;20s} {:5d}”

It then asks the user if they want to plot the results. Depending on user’s response, plot can be displayed. While plotting, plot the 5 most affected countries <em>starting from the 2<sup>nd</sup> most affected country</em>. That is ignore the top, most-affected country. The graph becomes difficult to visualize otherwise with a high concentration of infections in Mainland China (at the time we collected the data).




If the choice is 3, the program prompts for a country, compiles a list of areas affected within that country (from the set returned by affected_states_in_country ) and displays the names of areas affected <strong>in alphabetic order</strong> along with counters such as [01] and [02]. Use the following string formatting: “[{:02d}] {:&lt;30s}”




If the choice is 4, the user is asked to input the name of a country. The program will display one of two strings depending on whether the country is affected. Check the strings.txt file to obtain these strings.




<strong>Note</strong>: the program needs to catch exceptions in all the input sequences. For example, if the choice is not 1,2,3,4 or 5, then an error message is displayed, and user is asked for input again. Similarly, for country name in choice 3, if the user enters an invalid country name then an error message is displayed.

<strong> </strong>

<h3>Assignment Deliverables</h3>

The deliverable for this assignment is the following file:

proj09.py – the source code for your Python program

Be sure to use the specified file name and to submit it for grading via the <strong>Mimir </strong>before the project deadline.

<strong> </strong>

<h3>Assignment Notes</h3>




<ol>

 <li>Use itemgetter() from the operator module to specify the key for sorting.</li>

 <li>Items 1-9 of the Coding Standard will be enforced for this project.</li>

</ol>




<strong> </strong>

<h3>Suggested Procedure</h3>

<strong> </strong>

<ul>

 <li><em>Solve the problem using pencil and paper first.</em> You cannot write a program until you have figured out how to solve the problem.  This first step is best done collaboratively with another student.  However, once the discussion turns to Python specifics and the subsequent writing of Python statements, you must work on your own.</li>

</ul>




<ul>

 <li>Write a simple version of the program. Run the program and track down any errors.</li>

</ul>




<ul>

 <li>Use the debugger available in Spyder to locate and resolve errors. Set breakpoints right before the instructions where you perceive the program begins and then step through the code one instruction at a time. While doing this, keep an eye on the ‘variable explorer’ window in Spyder to observe the change in variables.</li>

</ul>




<ul>

 <li>Use the <strong>Mimir</strong> system to turn in the first version of your program.</li>

</ul>




<ul>

 <li>Cycle through the steps to incrementally develop your program:

  <ul>

   <li>Edit your program to add new capabilities.</li>

   <li>Run the program and fix any errors.</li>

  </ul></li>

</ul>




<ul>

 <li>Use the <strong>Mimir</strong> system to submit your final version.</li>

</ul>




<ul>

 <li>Be sure to log out when you leave the room, if you’re working in a public lab.</li>

</ul>

<strong>             </strong>







|  |   | |  `—-.|  `–‘  |        /

|__| __|  ______| ______/      __/







Data file: random.csv Error. Try again.




Data file:







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 34

Error. Try again.







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>




Choice: idowhatiwant Error. Try again.







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 5

Stay at home. Protect your community against COVID-19 |  |   | |  `—-.|  `–‘  |        /

|__| __|  ______| ______/      __/







Data file: ncov_small.csv







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 1

Country              Areas affected

—————————————-

Mainland China          31

US                       8

Australia                4

Canada                   3

Belgium                  1 Cambodia                 1 Finland                  1

France                   1

Germany                  1

Hong Kong                1




Plot? (y/n) n







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 5

Stay at home. Protect your community against COVID-19 |  |   | |  `—-.|  `–‘  |        /

|__| __|  ______| ______/      __/







Data file: ncov.csv







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 2

Country              People affected

—————————————-

Mainland China       80906

Italy                35713

Iran                 17361

Spain                13910

Germany              12332

France               10841

US                    8460

South Korea           8413

UK                    3480

Netherlands           3191

Plot? (y/n) n







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 5

Stay at home. Protect your community against COVID-19

<strong>             </strong>










.__   __.   ______   ______   ____    ____ |   |  |  /      | /  __         /   /

|   |  | |  ,—-‘|  |  |  |     /   /  |  . `  | |  |     |  |  |  |         /

|  |   | |  `—-.|  `–‘  |        /

|__| __|  ______| ______/      __/




Data file:







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 3

Country name: us

——————————

Affected area

——————————

<ul>

 <li>Alabama</li>

 <li>Alameda County, CA</li>

 <li>Alaska</li>

 <li>Arizona</li>

 <li>Arkansas</li>

 <li>Ashland, NE</li>

 <li>Bennington County, VT</li>

 <li>Bergen County, NJ</li>

 <li>Berkeley, CA</li>

 <li>Berkshire County, MA</li>

 <li>Boston, MA</li>

 <li>Broward County, FL</li>

 <li>California</li>

 <li>Carver County, MN</li>

 <li>Charleston County, SC [16] Charlotte County, FL           [17] Chatham County, NC</li>

 <li>Cherokee County, GA</li>

 <li>Chicago, IL</li>

 <li>Clark County, NV</li>

 <li>Clark County, WA</li>

 <li>Cobb County, GA</li>

 <li>Collin County, TX</li>

 <li>Colorado</li>

 <li>Connecticut</li>

 <li>Contra Costa County, CA</li>

 <li>Cook County, IL</li>

 <li>Davidson County, TN</li>

 <li>Davis County, UT [30] Delaware                       [31] Delaware County, PA</li>

 <li>Denver County, CO</li>

 <li>Diamond Princess cruise ship</li>

 <li>District of Columbia</li>

 <li>Douglas County, CO</li>

 <li>Douglas County, NE</li>

 <li>Douglas County, OR</li>

 <li>El Paso County, CO</li>

 <li>Fairfax County, VA</li>

 <li>Fairfield County, CT</li>

 <li>Fayette County, KY</li>

 <li>Florida</li>

 <li>Floyd County, GA</li>

 <li>Fort Bend County, TX</li>

 <li>Fresno County, CA</li>

 <li>Fulton County, GA</li>

 <li>Georgia</li>

 <li>Grafton County, NH</li>

 <li>Grand Princess</li>

 <li>Grand Princess Cruise Ship</li>

 <li>Grant County, WA</li>

 <li>Guam</li>

 <li>Harford County, MD</li>

 <li>Harris County, TX</li>

 <li>Harrison County, KY</li>

 <li>Hawaii</li>

 <li>Hendricks County, IN</li>

 <li>Hillsborough, FL</li>

 <li>Honolulu County, HI</li>

 <li>Hudson County, NJ</li>

 <li>Humboldt County, CA</li>

 <li>Idaho</li>

 <li>Illinois</li>

 <li>Indiana [65] Iowa                           [66] Jackson County, OR</li>

 <li>Jefferson County, KY</li>

 <li>Jefferson County, WA</li>

 <li>Jefferson Parish, LA</li>

 <li>Johnson County, IA</li>

 <li>Johnson County, KS</li>

 <li>Kansas</li>

 <li>Kentucky</li>

 <li>Kershaw County, SC</li>

 <li>King County, WA</li>

 <li>Kittitas County, WA</li>

 <li>Klamath County, OR [78] Lackland, TX</li>

 <li>Lackland, TX (From Diamond Princess)</li>

 <li>Lee County, FL</li>

 <li>Los Angeles, CA</li>

 <li>Louisiana</li>

 <li>Madera County, CA</li>

 <li>Madison, WI</li>

 <li>Maine</li>

 <li>Manatee County, FL</li>

 <li>Maricopa County, AZ</li>

 <li>Marion County, IN</li>

</ul>

<h3>To many titles to show in this document! See Mimir test for full view or “output4.txt”)</h3>







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 3




Country name: randoville

—————————— Error. Country not found.







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 3




Country name: india

——————————

Affected area

——————————

[01] N/A







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected [3] Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 5

Stay at home. Protect your community against COVID-19

<strong> </strong>

<h3>Test 5</h3>







.__   __.   ______   ______   ____    ____

|   |  |  /      | /  __         /   /

|   |  | |  ,—-‘|  |  |  |     /   /

|  . `  | |  |     |  |  |  |         /

|  |   | |  `—-.|  `–‘  |        /

|__| __|  ______| ______/      __/







Data file:







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 4




Country name: grenada

—————————— grenada is not affected.







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: vietnam Error. Try again.







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 3




Country name: vietnam

——————————

Affected area

——————————

[01] N/A







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 4




Country name: poland

—————————— poland is affected.







<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 5

Stay at home. Protect your community against COVID-19  <strong>Test 6 (plotting; no Mimir test) </strong>







.__   __.   ______   ______   ____    ____

|   |  |  /      | /  __         /   /

|   |  | |  ,—-‘|  |  |  |     /   /

|  . `  | |  |     |  |  |  |         /

|  |   | |  `—-.|  `–‘  |        /

|__| __|  ______| ______/      __/




Data file:




<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 1

Country              Areas affected

—————————————-

US                     193

Mainland China          31

Canada                  16

France                  10

Australia                9

UK                       7

Netherlands              4

Denmark                  3

Germany                  2

Others                   2

Plot? (y/n) y










<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 2

Country              People affected

—————————————-

Mainland China       80906

Italy                35713

Iran                 17361

Spain                13910

Germany              12332

France               10841

US                    8462

South Korea           8413

UK                    3480

Netherlands           3191




Plot? (y/n) y










<ul>

 <li>Countries with most areas infected</li>

 <li>Countries with most people affected</li>

 <li>Affected areas in a country</li>

 <li>Check if a country is affected</li>

 <li>Exit</li>

</ul>

Choice: 5

Stay at home. Protect your community against COVID-19 <strong> Grading Rubric</strong>




Computer Project #09       Scoring Summary General Requirements:




4 pts

Coding Standard 1-9

(descriptive comments, function headers, etc…)




Function Tests:

3 pts open_file (no Mimir test) 7 pts build_dictionary()

6 pts top_affected_by_spread()

6 pts top_affected_by_numbers()

6 pts affected_states_in_country()

2 pts is_affected

Program Tests 3 pts Test1

5 pts Test2

5 pts Test3

5 pts Test4

5 pts Test5

3 pts Test6 (plotting; manual, no Mimir test)

-2 for plotting


