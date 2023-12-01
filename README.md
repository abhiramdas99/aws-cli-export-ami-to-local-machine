# aws-cli-export-ami-to-local-machine
Export ami throught command line 

- create a iam user 
- provide the programatically access and download the seccret key and secret
- configure the aws
```git
$ aws configure
AWS Access Key ID [****************JF36]: AKIA6N5YMX3PM*********
AWS Secret Access Key [****************Hvev]: xWd+Sx6P6PiKUHycEv5CpRZem******
Default region name [us-east-1]: ap-south-1
Default output format [json]: json
```
- Create a bucket
```git
$ aws s3api create-bucket --bucket abhiramdas99-ami-backup --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1
{
    "Location": "http://abhiramdas99-ami-backup.s3.amazonaws.com/"
}
```
- Store the ami in bucket ( make sure you have a ami of your machine 
``git
$ aws ec2 create-store-image-task --image-id ami-0e1662b79e85f27fd --bucket abhiramdas99-ami-backup
{
    "ObjectKey": "ami-0e1662b79e85f27fd.bin"
}
```
- copy the amit o your local machine
```git
$ aws s3 cp s3://abhiramdas99-ami-backup/ami-0e1662b79e85f27fd.bin /c/my_desk/kilowott/client_projects/*******/
download: s3://abhiramdas99-ami-backup/ami-0e1662b79e85f27fd.bin to ..\..\my_desk\kilowott\client_projects\*****\ami-0e1662b79e85f27fd.bin
```
# cleaning aws
- remove the bucket
```git
$ aws s3 rb --force s3://abhiramdas99-ami-backup
delete: s3://abhiramdas99-ami-backup/ami-0e1662b79e85f27fd.bin
remove_bucket: abhiramdas99-ami-backup
```
- check the bucket is there or not
```git
MAINPC+abhir@MAINPC MINGW64 ~
$ aws s3 ls
2022-11-13 21:15:27 elasticbeanstalk-ap-south-1-991987285726

MAINPC+abhir@MAINPC MINGW64 ~
$
```
finally delete the ec2 machine 
![image](https://github.com/abhiramdas99/aws-cli-export-ami-to-local-machine/assets/62290469/b92ee436-2856-4d80-91ad-1929de958582)



