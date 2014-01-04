---
layout: post
title: " Count IP Addresses in Access Log File"
date: 2014-01-04 10:46:32 +0700
comments: true
categories: English
---

Leader: Hey Bob. Recently, Our server was nearly overloaded by a web spider that was severely stupid and malfunctioning 
you must find which IP address was making the most requests and block cmnd.
Bod: Ok. One bash line will solve it.

``` 
sudo tail -10000 /var/log/nginx/thiendia.com.log | awk ‘{print $1}’ | sort | uniq -c | sort -g

```

line explain:

tail -10000 /var/log/nginx/thiendia.com.log => grep last 10000 lines in access log of webserver
awk ‘{print $1}’ : grep first collum of access_log
sort | uniq -c | sort -g : prefix ips by the number of occurrence then compare according to general numerical value

example output:
69:   124.115.3.33
96:   124.115.5.169
6996:   66.219.73.236
9669:   74.204.11.20


