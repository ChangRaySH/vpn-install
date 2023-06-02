# vpn-install
1. shadowsocks server下载安装  
install shadowsocks  
chmod +x shadowsocks-all.sh  
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.l  
/etc/init.d/shadowsocks-python start | stop | restart | status   
修改配置  
vim /etc/shadowsocks-python/config.json  
2. 客户端下载安装    
3. 网络加速  
利用 TCP BBR 拥塞控制算法，实现服务器访问网速的提升。  
wget --no-check-certificate -O bbr.sh https://github.com/ChangRaySH/vpn-install/blob/main/bbr.sh  
chmod +x bbr.sh  
./bbr.sh  
sysctl net.ipv4.tcp_available_congestion_controlet.ipv4.tcp_available_congestion_control =reno cubic bbr  
4. 多用户配置  
vi /etc/shadowsocks.json  
{  
“server”:“0.0.0.0”,  
“server_port”:11660,  
“local_address”:“127.0.0.1”,  
“local_port”:1080,  
"port_password": {  
"6234": "password1", #端口+密码，相当于账户+密码  
"6235": "password2",  
"6236": "password3",  
"6237": "password4"  
},  
"timeout":300,  
"method":"aes-256-cfb",  
"fast_open": false  
}  
