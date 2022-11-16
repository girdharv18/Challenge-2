# Query the Metadata of an Instance within AWS and provide a JSON formatted output

### What is Metadata?

Instance metadata is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into categories, for example, host name, events, and security groups.

### Command to query the Instance Metadata:

You can query that information through Instance Metadata (169.254.169.254).
```
$ curl http://169.254.169.254/latest/meta-data/
{
ami-id
ami-launch-index
ami-manifest-path
auth-identity-credentials/
block-device-mapping/
events/
hostname
identity-credentials/
instance-action
instance-id
instance-life-cycle
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
public-keys/
reservation-id
security-groups
services/
}
```
### Important:

Although you can only access instance metadata and user data from within the instance itself, the data is not protected by authentication or cryptographic methods. Anyone who has direct access to the instance, and potentially any software running on the instance, can view its metadata. Therefore, you should not store sensitive data, such as passwords or long-lived encryption keys, as user data.

### Example:

```
$ curl http://169.254.169.254/latest/meta-data/security-groups

$ aws iam list-users --output json

```

### Outputs

jsonsg

{
    "Users": [
        {
            "UserName": "girdhar",
            "PasswordLastUsed": "2022-11-16T05:53:13Z",
            "CreateDate": "2022-08-07T07:35:53Z",
            "UserId": "ABCDEFGH4567IJKLM",
            "Path": "/",
            "Arn": "arn:aws:iam::1234567890:user/girdhar"
        },
        {
            "UserName": "temporary",
            "Path": "/",
            "CreateDate": "2022-11-16T07:37:41Z",
            "UserId": "PQRSTUV012349WXYZ",
            "Arn": "arn:aws:iam::9876543210:user/temporary"
        }
    ]
}
