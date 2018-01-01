# packsync

* Description

The packsync ansible scripts are a set of cron scheduled scripts that run on each ec2 instance hosting wordpress every 5 minutes. They do the following

1. Detect if files have been modified in the last 5 minutes, excluding upload directory
2. If they have: 
3. Get inventory of all active ec2's
4. Create a new wordpress package
5. Copy and apply new wordpress package to all active ec2 hosts
6. Upload new wordpress package to utilities bucket for future ec2 hosts

find /opt/wordpress/ -type f -mmin 10