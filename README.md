ngx_http_report_module
======================

a key-value based udp for nginx report module

##Installation

    $ ./configure --add-module=/path/to/ngx_http_report_module 

##Synopsis

   http  {
        
        [...]
        log_format  nginx_report 'typeid=1000217&appid=1000129&releaseversion=$host&commandid=$uri&resultcode=$status&tmcost=$request_time&reqsize=$request_length&rspsize=$bytes_sent&frequency=10&serverip=$server_addr&user_ip=$remote_addr&backend_ip=$upstream_addr';
        report_rate 10; # report frequency setting
        [...]
        
   }

    server {
    
        [...]
        report_tag  $host;
        access_report 127.0.0.1:8000 nginx_report;  # report_server ip:port
        
        [...]
    }


## Report data format

   tag=192.168.1.201&typeid=1000217&appid=1000129&releaseversion=192.168.1.201&commandid=/index.html&resultcode=304&tmcost=0.000&reqsize=484&rspsize=179&frequency=20&serverip=192.168.1.201&user_ip=192.168.1.109&backend_ip=-
   
## Urls
1. https://github.com/fluent/nginx-fluentd-module
