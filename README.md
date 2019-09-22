# Setting up EC2
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html

# Running Apache on EC2 Free 
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-LAMP.html

# Free option : Setting up SSL with Let's Encrypt
https://docs.aws.amazon.com/en_pv/AWSEC2/latest/UserGuide/SSL-on-amazon-linux-2.html

# Expensive option : Setup HTTPS via AWS Application Load Balancer (AWS ALB)
https://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancer-getting-started.html
https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-elb-load-balancer.html

# Installing .NET Core 2.1.2 on AWS Linux AMI 
Connect via PuTTY and execute following:
`wget https://download.microsoft.com/download/5/D/F/5DF4B836-7DFD-4CCF-AC96-101E2A4C7421/dotnet-sdk-2.1.2-linux-x64.tar.gz
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-2.1.2-linux-x64.tar.gz -C $HOME/dotnet
dotnet --version`

See https://github.com/dotnet/core/issues/930 and https://github.com/dotnet/core/blob/master/release-notes/download-archives/2.1.2-sdk-download.md

# .NET Core
https://www.youtube.com/watch?v=lDI_7Ev6Hg8
https://docs.microsoft.com/en-us/dotnet/core/linux-prerequisites?tabs=netcore2x for AMI follow CentOS 7.1
https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/linux-apache?view=aspnetcore-2.1&tabs=aspnetcore2x Host ASP.NET Core on Linux with Apache
https://httpd.apache.org/docs/2.4/vhosts/examples.html Apache VirtualHost Examples

# Deleting log files
1) PuTTY to the instance
2) Check for free space: `df -hT /dev/xvda1` 
3) Switch to super user: `sudo su`
4) Go to logs folder: `cd /var/log` 
5) Delete logs: `find -type f -name '*.log-*' -delete`
7) Delete Apache logs:
`sudo systemctl stop httpd 
cd /etc/httpd/
find -type f -name '*.log' -delete
sudo systemctl start httpd`

# Check journal example
`sudo journalctl -fu kestrel-awscoretest.service`

# Reastart Appache:
`sudo systemctl restart httpd`
