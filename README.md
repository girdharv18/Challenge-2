# Query the Metadata of an Instance within AWS and provide a JSON formatted output

### What is Metadata?

Instance metadata is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into categories, for example, host name, events, and security groups.

### Sometimes we want to retrieve EC2 instances' Region information

You can query that information through Instance Metadata (169.254.169.254).
```
$ curl --silent http://169.254.169.254/latest/dynamic/instance-identity/document
{
  "privateIp" : "172.31.2.15",
  "instanceId" : "i-12341ee8",
  "billingProducts" : null,
  "instanceType" : "t2.small",
  "accountId" : "1234567890",
  "pendingTime" : "2015-11-03T03:09:54Z",
  "imageId" : "ami-383c1956",
  "kernelId" : null,
  "ramdiskId" : null,
  "architecture" : "x86_64",
  "region" : "ap-northeast-1", # <- region
  "version" : "2010-08-31",
  "availabilityZone" : "ap-northeast-1c",
  "devpayProductCodes" : null
}
```
Response's JSON has a `region` key, so if you just want to get region, filter the key with `jq`.

```
$ sudo yum install -y jq
$ curl --silent http://169.254.169.254/latest/dynamic/instance-identity/document | jq -r .region
