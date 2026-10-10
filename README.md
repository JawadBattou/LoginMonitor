# LoginMonitor

This project reads a list of login log lines (username, IP, timestamp, status) and turns them into structured records. It then analyzes them to find failed attempts per user, locked accounts, the most suspicious IP, users who connect from multiple IPs, the busiest hour, and a list of security alerts.

## How to run

Make sure Python 3 is installed, then run this in the project folder: python assignment_starter_login_monitor.py

The script parses the sample logs and prints the summary report followed by the test output for each method.

## How busiest_hour() works

The method goes through every record in self.parsed_logs and pulls out the hour from the timestamp. A timestamp looks like "2026-09-10 08:15:02", so I split it on the space to separate date from time, take the time part, and slice the first two characters to get the hour like "08". I keep a dict where each hour is a key and the value is how many logins happened in that hour, using the same .get(hour,0)+1 we used vefore in failed attempts per user. After that, I loop through the dictionary keeping track of the highest count seen so far and which hour it belongs to. At the end I return that hour and its count as a tuple, so like ('08', 10).
