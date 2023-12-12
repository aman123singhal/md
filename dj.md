# S3 


Amazon S3 (Simple Storage Service) is like a huge online storage space provided by Amazon. It's a service that lets you store and retrieve any amount of data from anywhere on the internet. Here are its key features:

### 1. Storage :
 S3 offers a secure place to store your files, data, images, videos, or any digital content. It's like having a massive online hard drive where you can keep all your stuff.

### 2. Scalability :
 You can store as much or as little data as you need, and it can grow or shrink according to your requirements. It's like having a storage space that can expand to fit whatever you want to store.

### 3. Durability : 
S3 is designed to be highly reliable. Your data is replicated across multiple locations, so even if one part of it fails, your data stays safe and accessible. It's like having multiple backups to ensure your files are always available.

### 4. Security : 
S3 provides strong security features to protect your data. You can control who can access your stored information and set permissions to keep it private or share it selectively. It's like having a locked storage unit where only authorized people can enter.

### 5. Access Anywhere :
 You can access your stored data from anywhere with an internet connection. It's like having your files available whenever you need them, whether you're at home, in the office, or on vacation.

## There are 5 types of storages in S3

In Amazon S3 (Simple Storage Service), there are different storage classes or types, each designed for specific needs based on cost, availability, and durability. Here are some simplified explanations:

### 1. Standard :
 This is the default storage class. It's like keeping things in your room where they're easily accessible. It offers high availability, low latency, and durability, but it's slightly more expensive.

### 2. Infrequent Access (IA):
 Similar to storing things in a garage or attic that you don't need very often. It's a cheaper option than standard storage, but accessing the data may cost a little more and take slightly longer.

### 3. One Zone-IA :
 Like storing items in a nearby storage unit instead of a more secure place. It's cost-effective but stores data in a single availability zone, making it less resilient to outages compared to other classes.

### 4. Intelligent-Tiering :
 It's like having a smart storage system that automatically moves your data between frequent and infrequent access tiers. It's cost-effective as it optimizes storage costs based on usage patterns.

### 5. Glacier and Glacier Deep Archive: 
These are like long-term storage solutions where you store items in a storage unit far away, only accessing them very rarely. They're the cheapest options but take longer to retrieve data.

 ## How to create an S3 bucket.

 First we have to install aws cli (command line interface ) in our operating system, to install aws cli we will use command given below 

 (If this is your first time updating on Amazon Linux, to install the latest version of the AWS CLI, you must uninstall the pre-installed apt version using the following command:)

``````
$ sudo yum remove awscli
``````

(Output)
~~~
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'awscli' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 134 not upgraded.
~~~

Now we will download the installing file of aws cli steps are given below 

First download curl in your OS
``````
$ sudo apt install vim 
``````
(output)

~~~
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  vim-common vim-runtime vim-tiny
Suggested packages:
  ctags vim-doc vim-scripts indent
The following NEW packages will be installed:
  vim vim-runtime
The following packages will be upgraded:
  vim-common vim-tiny
2 upgraded, 2 newly installed, 0 to remove and 132 not upgraded.
Need to get 8,568 kB/9,359 kB of archives.
After this operation, 37.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim-runtime all 2:8.2.3995-1ubuntu2.13 [6,834 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim amd64 2:8.2.3995-1ubuntu2.13 [1,734 kB]
Fetched 8,568 kB in 5s (1,850 kB/s)
(Reading database ... 198714 files and directories currently installed.)
Preparing to unpack .../vim-tiny_2%3a8.2.3995-1ubuntu2.13_amd64.deb ...
Unpacking vim-tiny (2:8.2.3995-1ubuntu2.13) over (2:8.2.3995-1ubuntu2.10) ...
Preparing to unpack .../vim-common_2%3a8.2.3995-1ubuntu2.13_all.deb ...
Unpacking vim-common (2:8.2.3995-1ubuntu2.13) over (2:8.2.3995-1ubuntu2.10) ...
Selecting previously unselected package vim-runtime.
Preparing to unpack .../vim-runtime_2%3a8.2.3995-1ubuntu2.13_all.deb ...
Adding 'diversion of /usr/share/vim/vim82/doc/help.txt to /usr/share/vim/vim82/d
oc/help.txt.vim-tiny by vim-runtime'
Adding 'diversion of /usr/share/vim/vim82/doc/tags to /usr/share/vim/vim82/doc/t
ags.vim-tiny by vim-runtime'
Unpacking vim-runtime (2:8.2.3995-1ubuntu2.13) ...
Selecting previously unselected package vim.
Preparing to unpack .../vim_2%3a8.2.3995-1ubuntu2.13_amd64.deb ...
Unpacking vim (2:8.2.3995-1ubuntu2.13) ...
Setting up vim-common (2:8.2.3995-1ubuntu2.13) ...
Setting up vim-runtime (2:8.2.3995-1ubuntu2.13) ...
Setting up vim (2:8.2.3995-1ubuntu2.13) ...
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vim (vim) in a
uto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vimdiff (vimdi
ff) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rvim (rvim) in
 auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rview (rview) 
in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vi (vi) in aut
o mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/view (view) in
 auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/ex (ex) in aut
o mode
Setting up vim-tiny (2:8.2.3995-1ubuntu2.13) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
~~~

Now run the command to download installation file :-

Read the document for more information (click the link below and after opening the web page click on Linux)

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

``````
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
``````
(Output)
~~~
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 57.0M  100 57.0M    0     0  7678k      0  0:00:07  0:00:07 --:--:-- 9142k
~~~

In this above command :

- 'curl' is used for download the file from webpage 
- 'https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip' this part is the link of webpage 
- '-o awscliv2.zip': This part of the command tells curl to save the content retrieved from the URL "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" into a file named "awscliv2.zip".


Now we will unzip the installation file 

``````
$ unzip -u awscliv2.zip
``````
(output)
~~~
Archive:  awscliv2.zip
~~~

In the obove command :

- 'unzip' is used for the file 
- '-u' flag ensures that only newer files from the archive will overwrite existing files on the disk, preventing older files from replacing newer ones.
- 'awscliv2.zip' is the name of file 

Now we will run install command.

``````
$ sudo ./aws/install
``````
(output)

~~~
You can now run: /usr/local/bin/aws --version
~~~

Confirm the installation with the command below

``````
$ aws --version
``````

(output)
~~~
aws-cli/2.14.5 Python/3.11.6 Linux/6.2.0-37-generic exe/x86_64.ubuntu.22 prompt/off
~~~

Now we will make a free tier account on aws, to go on web page click the link below

https://aws.amazon.com/free/?gclid=CjwKCAiA98WrBhAYEiwA2WvhOkUT6q6YjNU727SmlZIHadsy4dTeJs6smePwj2b5hK12KFSDPjk5tRoChXkQAvD_BwE&trk=09863622-0e2a-4080-9bba-12d378e294&sc_channel=ps&ef_id=CjwKCAiA98WrBhAYEiwA2WvhOkUT6q6YjNU727SmlZIHadsy4dTeJs6smePwj2b5hK12KFSDPjk5tRoChXkQAvD_BwE:G:s&s_kwcid=AL!4422!3!453325184878!e!!g!!aws%20console!10712784862!111477280451

Now click on the Create free account as you can in the image below
![Alt text](<Screenshot from 2023-12-07 17-58-53.png>)

Now we will add our e-mail account and the aws account name that we want and click on the virefy e-mail address

![Alt text](1.png)

Now we will go and check our email inbox that we got an verification code or not 

![Alt text](2.1.png)

As we can see in the above image that we got verification code and now we will fill it on the aws console web page and click on the Verify.

![Alt text](2.png)

After it we will set a strong password for our asw account


![Alt text](3.png)

Fill the contact information 

![Alt text](4.png)

After fillng  all the contact information scroll down  and click on the continue 

![Alt text](5.png)

Now fil the billing information (it is free for 12 months but we have to fill the information) and press on verify and continue.

![Alt text](6.png)

Enter the OPT from your mobile Phone (that sent by aws)

![Alt text](7.png)

Now Confirm your identity as given below and click on continue

![Alt text](8.png)

![Alt text](9.png)

Now fill the OTP sent sent by the aws after compliting the above step and press continue.

![Alt text](10.png)

Now select support plan to "Basic support - free" and press continue 

![Alt text](11.png)

Now click on "Go to aws management console"

![Alt text](12.png)

Now click on the "Sign in to the console"

![Alt text](13.png)

Now fill up the cridentials (email and password of aws account)

![Alt text](15.png)

![Alt text](16.png)

You will get the web page like given below :-

![Alt text](17.png)

Now go to your terminal and make bucket to upload data in bucket.

### First we will configure aws cli with the help of command given below :-

~~~
$ aws configure
~~~
(output)

``````
AWS Access Key ID [None]:                             
AWS Secret Access Key [None]: 
Default region name [None]: 
Default output format [None]: 
``````
To find the Key ID, Secret Access Key, region name and output format go to your aws acconut, on the right side you can see your user name on the top click on that and select the Security Credentials :-

![Alt text](18.png)

After that scroll down and click on the option 'Create access key'

![Alt text](19.png)

Tick the "Continue to create access key' and click on "create access key"


![Alt text](20.png)

Now you can see your access key and secret access key :-

![Alt text](21.png)

To see the regiaon name go on the top(in the right corner) of the webpage of your aws account and click on the global and you can see all the available region.

![Alt text](22.png)

Now go back to terminal and run the fill the output of the comman given below 
~~~
$ aws configure 
~~~

~~~
AWS Access Key ID [None]: AKIAWARXAENS7BI6YGNO
AWS Secret Access Key [None]: hjsjghwg672358746ijdiuw7iyeuieuiy23
Default region name [None]: us-east-1
Default output format [None]: text
~~~

NOTE:- In the above output, In the section (AWS Secret Access Key [None]) you will go to the web page (whre you created your access key as you can see in the above image) see the secret access key by click on the show and copy it for the terminal.  

- In the section of 'Default region name' i have selected "us-east-1" region you can select it according to your need. 

- In the section of Default output format we will write "text" because we want the output in text format.


### Create an S3 bucket 

To make S3 bucket run the command given below:-

~~~
$ aws s3api create-bucket --bucket my.amanbucket --region us-east-1
~~~

(outout)

~~~
/my.amanbucket
~~~

Note :- Always create your bucket with  unique name.

In the above command :
- 'aws s3api' signifies the use of the AWS CLI to interact with the Amazon S3 service through its API.
- 'create-bucket' this part is used for creating a bucket.
- '--bucket' this part of command is used for giving the name to the bucket.
- 'my.amanbucke' this is the name of bucket.
- '--region' this part is to give the region name.
- 'us-east-1' this is the name of region.


To verify if the bucket was created successfully, list your buckets using the coomand given below :

~~~
$ aws s3api list-buckets
~~~

(output) 

~~~
BUCKETS 2023-12-11T10:24:19+00:00       my.amanbucket
OWNER   asinghal199714  b123d2151bd39381fb45a83b47204bde40297c868fef181efe41860fef4bb23c
~~~

As you can see in the above output bucket is successfully created.

In the above command :
- 'aws s3api' signifies the use of the AWS CLI to interact with the Amazon S3 service through its API.
- 'list-buckets' this part is to list the bucket that we created.

### Now we will apload a file in the bucket with help of commands given below :

First we will make a file on the Desktop to upload in the bucket:

~~~
$ cd Desktop
~~~

In the above command 'cd' is to change the directory or to go inside the directory and 'desktop' is the name of directory.

Now we will make a file with the name 'prometheus.yml'

~~~
$ touch prometheus.yml
~~~
In the above command touch is used for making directory and 'prometheus.yml' is the name of the file 

Let's check that the file is made or not.

~~~
$ ls 
~~~

(output)

~~~
amans  prometheus.yml
~~~

As you can see in the above output that  we have a file with the name 'prometheus.yml', So first I will check the path of my file with command given below :

~~~
$ pwd /prometheus.yml
~~~
(output)

~~~
/home/aman/Desktop
~~~

As we found the path of the file, i fill upload it in my bucket:

~~~
$ aws s3 cp /home/aman/Desktop/prometheus.yml s3://my.amanbucket/ 
~~~

(output)
~~~
upload: ./prometheus.yml to s3://my.amanbucket/prometheus.yml
~~~

In the above command :
- 'aws s3 cp' is used to copy the file in the bucket.
-  '/home/aman/Desktop/prometheus.yml' this is the path of file in the local machine.
- 's3://my.amanbucket/' this is the name of bucket.


To see the file is uploaded or not, use the command given below :

~~~
$ aws s3 ls s3://my.amanbucket/
~~~

(output)

~~~
                           PRE aman/
2023-12-11 17:20:17      12288 .prometheus.yml.swp
2023-12-12 11:09:46          0 prometheus.yml

~~~

As we can see in the above output that the file is uploaded in the bucket, file name is 'prometheus.yml'

### To download the file we uploaded, use the command below:

~~~
$ aws s3 cp s3://my.amanbucket/.prometheus.yml /home/aman/Downloads
~~~
(output)

~~~
download: s3://my.amanbucket/prometheus.yml to ./prometheus.yml
~~~

In the above command:

- 'aws s3 cp' is for downloading the data from the S3 bucket.
- 's3://my.amanbucket/prometheus.yml' is the path of the file in the S3 bucket.
- '/home/aman/Downloads' is the path of our local machine, where we want to download the file.

Now we will see that our is downloaded or not:

(first we will go in the directory whre we downloaded the file)
~~~
$ cd Downloads
~~~

Now check the file with the command given below:

~~~
$ ls 
~~~

(output)

~~~
prometheus.yml
~~~



