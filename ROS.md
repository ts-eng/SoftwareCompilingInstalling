
# ROS installation

## Set up your keys

$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
gpg: no valid OpenPGP data found.

solution: https://blog.csdn.net/quantum7/article/details/123856236
$ curl -O https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: (7) Failed to connect to raw.githubusercontent.com port 443 after 1 ms: Connection refused

solution: https://blog.51cto.com/u_3826358/3832035
$ sudo mv /etc/hosts /etc/hosts.bak
$ sudo cp /etc/hosts.bak /etc/hosts
$ sudo vi /etc/hosts
185.199.108.133 raw.githubusercontent.com
185.199.109.133 raw.githubusercontent.com
185.199.110.133 raw.githubusercontent.com
185.199.111.133 raw.githubusercontent.com

$ curl -O https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc
$ sudo apt-key add ros.asc
OK
