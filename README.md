# pushNotificationConcurrencyTestPlan

This JMeter test plan is designed to test the performance of a push notifications system by simulating various scenarios of creating, updating, and deleting notifications. The tests focus on concurrency and parallel execution to measure how the system behaves under different loads.

## Table of Contents</br>
Prerequisites</br>
Installation</br>
Test Plan Overview</br>
CSV Files</br>
Running the Test Plan</br>
Customizations</br>
Performance Metrics</br>
Contributing

## Prerequisites
Apache JMeter: Version 5.6.3 or later </br>
Java: Version 8 or higher </br>
JMeter Plugins: Install the Parallel Controller Plugin manually or via the JMeter Plugins Manager </br>
Download the test data files and place them in the correct path </br>

## Installation
Clone the repository:
```bash
git clone https://github.com/minijamigara/push-notifications-test-plan.git
cd push-notifications-test-plan
```
Use this commands to execute tests via terminal
```bash
./jmeter -n -t /home/administrator/Performance/PushNotification/PushNotificationTestPlan.jmx -l /home/administrator/Performance/results.jtl
```



Launch JMeter </br>
Open the PushNotificationTestPlan.jmx file located in the project directory </br>
Ensure that the CSV Data Set Config points to the correct CSV files in your local repository </br>

# Test Plan Overview
1. Post - concurrency (for same employee) </br>
Description: Simulates concurrent POST requests to create notifications for the same employee. </br>
Thread Group Properties: </br>
Number of Threads (Users): 500 </br>
Ramp-up Period: 5 seconds </br>
Loop Count: 1 </br>
Components: </br>
HTTP Request: Sends the POST request. </br>
CSV Data Set Config: Uses a CSV file for dynamic data (e.g., employee IDs, notification content). </br>
View Results Tree, Summary Report, Aggregate Report: Monitor results during and after the test. </br>
2. Post - concurrency (for different employees)  </br>
Description: Simulates concurrent POST requests for different employees.  </br>
Similar to the first test, but it uses different employee IDs from the CSV file.  </br>
3. Post-Delete Concurrency Thread Group  </br>
Description: Executes POST and DELETE requests concurrently for notifications in parallel using a Parallel Controller.  </br>
Components:  </br>
HTTP POST Request: Creates a new notification.  </br>
HTTP DELETE Request: Deletes an existing notification.  </br>
Parallel Controller: Ensures concurrent execution. </br>
View Results Tree, Summary Report, Aggregate Report: Collect test results.  </br>
4. Patch - Concurrency Thread Group  </br>
Description: Simulates concurrent PATCH requests for modifying notifications.  </br>
5. Delete - concurrency (for same employee)  </br>
Description: Simulates concurrent DELETE requests for the same employee's notifications.  </br>


## Customizations
1. API Endpoint </br>
Ensure the HTTP Request elements are configured to point to your API endpoint (base URL, path, and query parameters). </br>
2. CSV Data </br>
Customize the CSV files to match your test data, such as employee IDs or notification content. </br>
3. Thread Group Parameters </br>
You can adjust the Number of Threads, Ramp-up Period, and Loop Count for each thread group to simulate different loads. </br>

## Performance Metrics
During the test execution, monitor the following metrics: </br>

Average Response Time: Time taken by the server to respond to requests. </br>
Throughput: Number of requests processed per second. </br>
Error Rate: Percentage of failed requests. </br>



