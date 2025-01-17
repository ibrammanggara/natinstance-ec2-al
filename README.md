# natinstance-ec2-al


Connect to your instance and run the following commands:

    sudo yum install iptables-services -y
    sudo systemctl enable iptables
    sudo systemctl start iptables
    sudo vim /etc/sysctl.d/custom-ip.conf 
    #net.ipv4.ip_forward=1
    sudo sysctl -p /etc/sysctl.d/custom-ip.conf
    netstat -i (primary network interface is enX0)
    sudo /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    sudo /sbin/iptables -F FORWARD
    sudo service iptables save

disable:

    vim /etc/sysctl.d/custom-ip.conf 
    net.ipv4.ip_forward=0
    sudo sysctl -p /etc/sysctl.d/custom-ip.conf
