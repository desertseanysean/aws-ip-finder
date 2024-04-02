# aws-ip-finder
Ever needed to find a public IP in your AWS accounts ? It might be "easy" when you have 1 account but what if you have 20, 50, 100+ accounts ?

This script gather Public IP information for AWS services and returns a list of the findings.

### How to install
```
git clone https://github.com/groorj/aws-ip-finder.git
cd aws-ip-finder
pip install -r requirements.txt
```
### Requirements
- Python3
- PyYAML
- Boto3

### Configuration
Edit the file config.yml in order to configure your parameters.

```
profile_name: my-profile-name
assertions:
  regions:
    - sa-east-1
    - us-east-1
    services:
      - ec2
      - natgateway
      - rds
```
- **profile_name**: `This is the AWS profile name that you use with your account located at ~/.aws/credentials`
- **regions**: `A list of regions that you want this script to craw and get data for`
- **services**: `A list of services to query for Public IPs`. Current options are: `ec2`, `natgateway`, `rds`

### Running
`python3 -tt aws-ip-finder.py config.yml`

### Output

```
{'service': 'ec2', 'public_ip': '52.222.90.111', 'resource_id': 'i-0b2a765034c6bb4d1'}
{'service': 'ec2', 'public_ip': '52.0.222.10', 'resource_id': 'i-09cd7765e86d2de02'}
{'service': 'ec2', 'public_ip': '52.2.111.9', 'resource_id': 'i-06701765f0a50c19b'}
```

### Notes
You can create as many configuration files as you want and provide it as an argument to the aws-ip-finder.py script.
