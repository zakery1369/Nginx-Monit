## Nginx Monitoring
![Monit Nginx](https://raw.githubusercontent.com/zakery1369/pics/master/Monit-Nginx.png)

## Install Monit

1.Install Monit.
```bash
sudo apt install monit
```

## Nginx monitoring Configuration

Go to the Monit directory `/etc/monit/conf.d` and create the following configuration file.

```bash
vim nginx-monit.conf
```
2.Add the following configuration to the `nginx-monit.conf` file.

```bash
check host nginx with address YourDomain.com
    if failed port 80 protocol http
        then exec "/sbin/sysctl -w net.ipv4.icmp_echo_ignore_all=1"
    else if succeeded
        then exec "/sbin/sysctl -w net.ipv4.icmp_echo_ignore_all=0"
```

3.To change the service check interval, modify the set daemon variable in the `/etc/monit/monitrc` file.

```bash
set daemon 5    #check services at 5 seconds intervals
```

## Verification

4.Verify the Monit configuration syntax.

```bash
sudo monit -t
```

5.If the syntax is valid, restart Monit to apply the configuration changes.
```bash
sudo systemctl restart monit
```
