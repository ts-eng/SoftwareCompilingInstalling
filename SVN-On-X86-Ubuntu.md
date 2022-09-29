$ sudo apt-get update  
$ sudo apt-get install subversion  
$ mkdir -p ~/svn/repository  
$ chmod -R 777 ~/svn/repository  
$ svnadmin create ~/svn/repository   

$ mv ~/svn/repository/conf/svnserve.conf ~/svn/repository/conf/svnserve.conf.bak  
$ cp ~/svn/repository/conf/svnserve.conf.bak ~/svn/repository/conf/svnserve.conf  
$ vim ~/svn/repository/conf/svnserve.conf  

anon-access = none  
auth-access = write  
password-db = passwd  
authz-db = authz  

$ mv ~/svn/repository/conf/authz ~/svn/repository/conf/authz.bak  
$ cp ~/svn/repository/conf/authz.bak ~/svn/repository/conf/authz  
$ vim ~/svn/repository/conf/authz  

admin = zkw  
[repository:/]  
@admin = rw  
* =  

$ mv ~/svn/repository/conf/passwd ~/svn/repository/conf/passwd.bak  
$ cp ~/svn/repository/conf/passwd.bak ~/svn/repository/conf/passwd  
$ vim ~/svn/repository/conf/passwd  

zkw = ZKW123  

$ svnserve -d -r ~/svn  
$ ps -aux|grep svnserve  
$ killall svnserve  
