# packsync

* Description

The packsync ansible scripts are a set of cron scheduled scripts that run on each ec2 instance hosting wordpress every 5 minutes. They do the following

1. Detect if files have been modified in the last 5 minutes, excluding upload directory
2. If they have:
3. Upload new wordpress package to S3
4. Get inventory of all afctive ec2 instances
5. Apply new wordpress package to all ec2 instances

* Usage

The packsync scripts are run by cron and configured by the webinit scripts. However you can run these manually yourself with the following command

NOTE: This script is intended to run under root user. Uses a combination of local and remote calls

ansible-playbook -i inventory/localwebstack init-packsync.yml -vvvv --extra-vars "mywordpresssite_db_wp_name=<wp_db_name> mywordpresssite_s3_utilities=<s3_bucket>"