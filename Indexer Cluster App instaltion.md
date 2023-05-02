### Step-1: Download the Add-on/App from Splunkbase
### Step-2: Copy the Downloaded Add-on/App package from local to Cluster Master using scp command
```bash
scp -i newkey.pem splunk-add-on-for-cisco-asa_510.tgz ec2-user@ec2-18-219-17-214.us-east-2.compute.amazonaws.com:/tmp
```
### Step-3: Login to Cluster Master backend & Navigate to /tmp folder
```bash
ssh -i "newkey.pem" ec2-user@ec2-18-219-17-214.us-east-2.compute.amazonaws.com
sudo su - splunk
cd /tmp
ls
ll -ltr
```

### Step-4: Extract the Add-on/App Package 
```bash
tar -xvf splunk-add-on-for-cisco-asa_510.tgz
```

### Step-5: Navigate inside the Add-on/App folder & Remove unwanted config files 

1. Remove the eventgen.conf files and all files in the samples folder.
2. Remove the inputs.conf and inputs.conf.spec files, if the add-on contains them. Exception: If you are collecting data locally from the machines running your indexers, keep these files.
3. Remove the database.conf file, if it contains one.


```bash
cd Splunk_TA_cisco-asa
ll -lrt
```

Note: Sometimes the App may not have the config file which we are looking to delete

### Step-6: Copy the Add-on/App folder to manager-apps folder

manager-apps folder: /opt/splunk/etc/manager-apps/

```bash
cp -rf /tmp/Splunk_TA_cisco-asa /opt/splunk/etc/manager-apps/

cd /opt/splunk/etc/manager-apps/

ll -ltr
```

Now the Add-on/App is copied to Manager-apps folder


### Step-7: Login to Cluster Manager web/UI & Navigate to Indexer Clustering Dashboard

Navigation: Settings >> Indexer Clustering

Note: Make sure all of the status are green.

Navigation: Edit >> Configure bundle actions

### Step-8: Validate and Check Restart

Click "Validate and Check Restart" button >> Click the button in popup as well.

It will take few seconds and show you the "Last Validate and Check Restart:  Successful".

### Step-9: Bundle push

Click "Push" button >> Click "Push Changes" button in the popup as well.

It will say "Rolling Restart is in progress", and finally "Last Push: Successful"

### Step-10: Login to any one of the indexer UI & check if the add-on/app is present.

Login and Go to Manage Apps (hint: Top left there will be a gear icon)

here you can see the add-on/app is installed