```
This is change won't work
/etc/default/jenkins

Ubuntu 12 onwards


/usr/lib/systemd/system/jenkins.service
Environment="JENKINS_PORT=9090"
sudo systemctl daemon-reload
sudo systemctl stop jenkins
sudo systemctl start jenkins

```
