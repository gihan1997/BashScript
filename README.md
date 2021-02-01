# BashScript
$ grep "user hoover" /var/log/auth.log
pam_unix(sshd:session): session opened for user hoover by (uid=0)
pam_unix(sshd:session): session closed for user hoover
$ grep "4792" /var/log/auth.log
$ grep -P "(?<=port\s)4792" /var/log/auth.log
Accepted password for hoover from 10.0.2.2 port 4792 ssh2
$ grep -B 3 -A 2 'Invalid user' /var/log/auth.log$ tail -f /var/log/auth.log | grep 'Invalid user'
Apr 30 19:49:48 ip-172-31-11-241 sshd[6512]: Invalid user ubnt from 219.140.64.136
Apr 30 19:49:49 ip-172-31-11-241 sshd[6514]: Invalid user admin from 219.140.64.13
pam_unix(su:auth): authentication failure; logname=hoover uid=1000 euid=0 tty=/dev/pts/0 ruser=hoover rhost=  user=root
$ awk '/sshd.*invalid user/ { print $9 }' /var/log/auth.log
guest
