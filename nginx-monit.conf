check host nginx with address YourDomain.com
    if failed port 80 protocol http
        then exec "/sbin/sysctl -w net.ipv4.icmp_echo_ignore_all=1"
    else if succeeded
        then exec "/sbin/sysctl -w net.ipv4.icmp_echo_ignore_all=0"
