Nginx requests timing monitoring (Munin plugin)
======================

Basicly one of the most intresting parameters of your web server (after server load and request rate on port 80) is request process time.
Using this plugin you can control average time to process requests by nginx server.

## Installation

 1. Copy plugin script to munin plugin directory (/etc/munin/plugins)
 
 2. Set up Nginx config 
 
    – Add 
   ```
   log_format monitor '$msec $request_time $status $bytes_sent $request';
   ``` 
    to http section
    
    – Add logging to each section you want to monitor
    
   ```
   access_log  /var/log/nginx/<section name>.monitor.log  monitor;
   ```
    
 3. Restart nginx
 
 4. Restart munin-node
 
## Tuning

 – It's recommended to use different log for static and dynamic (proxied) content
 
 – You can use as much logs as you want. Each log file with .monitor.log will be processed
 
 – Log rotation each day strongly recommended

### Useful links

[[http://munin-monitoring.org][Munin]]
[[http://nginx.org][nginx]] HTTP server
