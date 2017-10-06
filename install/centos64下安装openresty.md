centos6.4下安装openresty
先创建目录：mkdir -p /usr/openresty    cd /usr/openresty
1、安装依赖库
yum install readline-devel pcre-devel openssl-devel gcc
2、下载openresty
wget --no-check-certificate https://openresty.org/download/openresty-1.11.2.2.tar.gz
wget openresty.org/download/ngx_openresty-1.7.7.2.tar.gz
tar -zxf ngx_openresty-1.7.7.2.tar.gz
ngx_openresty-1.7.7.2/bundle目录里存放着nginx核心和很多第三方模块，比如有我们需要的Lua和LuaJIT
3、安装LuaJIT
cd bundle/LuaJIT-2.1-20150120/
make clean && make && make install
ln -sf luajit-2.1.0-alpha /usr/local/bin/luajit
4、下载ngx_cache_purge模块，该模块用于清理nginx缓存
cd /usr/servers/ngx_openresty-1.7.7.2/bundle
wget https://github.com/FRiCKLE/ngx_cache_purge/archive/2.3.tar.gz
tar -xvf 2.3.tar.gz （tar -xvf 2.3）
5、[root@hp ngx_openresty-1.7.7.2]# ./configure，默认配置，openresty会安装在/usr/local/openresty
6、make
7、make install
8、设置环境变量：
PATH=/usr/local/openresty/nginx/sbin:$PATH
export PATH
9、查看版本
nginx -v
如果出现nginx version: openresty/1.11.2.2，则安装成功
10、启动nginx
/usr/local/openrestry/nginx/sbin/nginx
接下来该配置nginx+lua开发环境了
