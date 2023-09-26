# change-GCP_IAP_SSH_PORT
how to change in GCP the SSH port for IAP

First, ensure firewall rule [1] is created allowing both 22 and your custom port. 22 can later be removed.

1) SSH via port 22
2) edit the PORT line - uncomment and add your port number
```
sudo vi /etc/ssh/sshd_config
```
3) Restart ssh service
```
sudo service ssh restart
```

4) SSH via IAP with the new port
```
gcloud compute ssh <MY_VM_NAME> --tunnel-through-iap --ssh-flag="-p <MY_PORT_NUMBER>" --zone us-central1-a
```

[1] https://cloud.google.com/iap/docs/using-tcp-forwarding#create-firewall-rule
