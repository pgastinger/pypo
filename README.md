# pypo
Python SNMP poller for troubleshooting purposes with a REST api and live charts

Most of the popular network management tools have a 5min poll interval, which is way very long. It maybe ok for collecting values for statistical purposes, but it ain't helpful for troubleshooting and for finding performance bottlenecks. 

Consider following problem:
You are collecting bandwidth metrics (ifinbps, ifoutbps) for a Cisco switch port with the regular 5min poll interval. You typically can see the average port utilization with many tools (Cacti, Icinga). If the link utilization is at 100% for a couple of seconds, you won't see this (micro) burst in your 5min average values. You may see a slight increase, but not necessarily. 

This small project is meant to be a short-term troubleshooting tool. It will collect SNMP oids every 10sec, will store the values in a whisper database and will offer them to miscellaneous clients using a REST api.

I did not want to reinvent the wheel, so I picked mainly open source components, like:
- sqlalchemy
- whisper
- pysnmp
- flask
- highcharts
