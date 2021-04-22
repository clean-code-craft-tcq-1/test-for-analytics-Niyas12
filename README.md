# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.

Fill the parts marked '' in the **Tasks** section below.

## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.-

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Utilty for notification controller
3. utility to read csv file
4. read access to csv file
5. pdf converter utilitiy


(add more if needed)

### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter |  No           | pdf converter will be used from a 3rd party
Counting the breaches       |  Yes          | to count the breaches in a month 
Detecting trends            | Yes           | to recoerd if reading is continously increasing for 30 minutes
Notification utility        |  No           | notification ultity is developed from another team.  

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
2. Write "Invalid input" to the PDF when the csv doesn't contain expected data
3. Write "minimum","maximum","breache count","trends" for each report
4. Write "no data" to PDF when csv is empty
5. Generate a fake pdf when for one week
6. Check fake notification has been sent when a new report is available
7. Write "0" to the PDF is there is no breaches. 
8. Check "record trends" is incremented when reading is increasing for 30 minutes
9. Return "Success" when  notification is triggered as expected.
10. Write "Failure" when server can not be connected
11. Write "success" when server is connected



(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input              | Output                      | Faked/mocked part
|--------------------------|--------------      |-----------------------------|---
Read input from server     | csv file           | internal data-structure     | Fake the server store
Validate input             | csv data           | valid / invalid             | None - it's a pure function
Notify report availability | report             | success/failed              | mock the notification controller
Report inaccessible server | server credetials  | success/failed              | fake server
Find minimum and maximum   | csv file           |       min,max value         | None - it's a pure function
Detect trend               | csv file           | date/time                   | None - it's a pure function
Write to PDF               | report data        | PDF file                    | fake the PDF converter
