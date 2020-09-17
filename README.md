# Create an Attendance Spreadsheet Using Zoom Reports
I have fifty students. I need to know which students attend lectures and labs. It's possible to download a usage report from Zoom for each class, but aggregating many classes with students can be challenging. Students can also log into the class with a different name or user email compouding the aggregation difficulty.

## Python Does the Aggregation
I wrote a script to aggregate student names and emails and extend it by class dates. Rather than "yes/no" attendance, the table is instead filled with class attendance time (minutes). 

|       Name        |       Email        | 1-Sep | 3-Sep | 4-Sep | 8-Sep | 10-Sep | 11-Sep |
|-------------------|--------------------|-------|-------|-------|-------|--------|--------|
| Student 1         | student1@email.com |    45 |    55 |    55 |    15 |     50 |     35 |
| Student 2         |                    |       |       |    45 |       |        |     66 |
| Student 3         | stud3@email.com    |    15 |       |       |       |        |        |
| Student 3         | student3@email.com |    45 |       |    55 |    18 |     54 |        |
| Student Student 3 |                    |       |       |       |       |        |     45 |

*Table 1: This table aggregates 6 Zoom "Usage Report". A report for each date.*

## Usage
Download Zoom Usage Reports for each class. Select both checkmark boxes, 'Export with Meeting Data' and 'Show Unique Users.' The reports may need to be renamed if the meeting is a reoccurring meeting. The meeting id is part of the filename. Save all reports to the same folder. They should be .csv files.

Change the directory in the script to the folder where the reports have been saved. 

Run script. The output is a report entitled "Class.attendance.up.to.2020-09-05.txt" saved in the same folder as the usage reports.

![Find Zoom Usage Reports](https://github.com/har1eyk/Create-Attenance-List-Using-Zoom/blob/master/Find.Zoom.usage.reports.png)
*Fig 1: Sign into Zoom. Select 'Reports' > 'Usage'*

![Find Zoom Usage Reports](https://github.com/har1eyk/Create-Attendance-List-Using-Zoom/blob/master/Export.mtg.data.and.show.unique.users.png)
*Fig 2: Select both checkmarks when prompted, then download.*

## Testing
I've created three meeting reports under the folder "Test_Data". Cloning this repository to a local drive and running the Python script "calculate.attendance.from.Zoom.usage.reports.py" will create an attendance report.

I've also included a Jupyter Notebook for debugging purposes. 

The attendance report generated with the data under "Test_Data" should look like this:


|   |      Name      |           Email           | 9/1/2020 | 9/3/2020 | 9/5/2020 |
|---|----------------|---------------------------|----------|----------|----------|
| 0 | Aaron Harrison | sclark@hotmail.com        | 0        | 0        | 0        |
| 1 | Andrew         | sbell@freeman.com         | NR       | NR       | 19       |
| 2 | Andrew         | NR                        | NR       | 52       | 52       |
| 3 | Andrew Cobb    | juliekane@james-davis.org | 52       | NR       | NR       |

*Table 2: This table is the report generated by the Python script and the usage reports under "Test_Data". NR = 'no record'. This report contains fake names and emails.*