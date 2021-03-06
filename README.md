ngx_lmdb
==========
[ngx_lmdb](https://github.com/rryqszq4/ngx_lmdb) - Embedded lmdb for nginx-module.

Requirement
-----------
- lmdb
- nginx-1.6.3+

Installation
-------
```sh
$ git clone https://github.com/rryqszq4/ngx_lmdb.git

$ wget 'http://nginx.org/download/nginx-1.6.3.tar.gz'
$ tar -zxvf nginx-1.6.3.tar.gz
$ cd nginx-1.6.3

$ export LMDB_INC=/path/to/lmdb
$ export LMDB_LIB=/path/to/lmdb

$ ./configure --user=www --group=www \
              --prefix=/path/to/nginx \
              --add-module=/path/to/ngx_lmdb
$ make
$ make install
```

Synopsis
--------
nginx config:
```nginx
user www www;
worker_processes  4;

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;
    
        location /lmdb_get {
                lmdb_database /home/www/lmdb/testdb;
                lmdb_get;
        }

        location /lmdb_put {
                lmdb_database /home/www/lmdb/testdb;
                lmdb_put;
        }

        location /lmdb_del {
                lmdb_database /home/www/lmdb/testdb;
                lmdb_del;
        }
        
    }
}
```

Copyright and License
---------------------
BSD 2-Clause License

Copyright (c) 2017, rryqszq4 <rryqszq@gmail.com>  
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this
  list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice,
  this list of conditions and the following disclaimer in the documentation
  and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.