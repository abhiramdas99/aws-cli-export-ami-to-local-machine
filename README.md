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
- Create a bucket with
```git
$ aws s3api create-bucket --bucket abhiramdas99-ami-backup --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1
{
    "Location": "http://abhiramdas99-ami-backup.s3.amazonaws.com/"
}
```
