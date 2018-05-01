---
title: "terraform-aws-elastic-beanstalk-environment"
excerpt: "Terraform module to provision AWS Elastic Beanstalk environment"
---
# Terraform AWS Elastic Beanstalk Environment 

|||
|------|------|
|GitHub Repo|https://github.com/cloudposse/terraform-aws-elastic-beanstalk-environment|
|Terraform Module|terraform-aws-elastic-beanstalk-environment |
|Release|[![Release](https://img.shields.io/github/release/cloudposse/terraform-aws-elastic-beanstalk-environment.svg)](https://github.com/cloudposse/terraform-aws-elastic-beanstalk-environment/releases)|
|Build Status|[![Build Status](https://travis-ci.org/cloudposse/terraform-aws-elastic-beanstalk-environment.svg)](https://travis-ci.org/cloudposse/terraform-aws-elastic-beanstalk-environment)|

# Variables

|Name|Default|Description|Required|
|------|------|------|------|
|alb_zone_id|{}|ALB zone id|
|update_level|"minor"|The highest level of update to apply with managed platform updates. patch for patch version updates only. minor for both minor and patch version updates|
|instance_refresh_enabled|"true"|Enable weekly instance replacement.|
|delimiter|"-"|Delimiter to be used between `name`, `namespace`, `stage`, etc.|
|env_default_key|"DEFAULT_ENV_%d"|Default ENV variable key for Elastic Beanstalk `aws:elasticbeanstalk:application:environment` setting|
|env_default_value|"UNSET"|Default ENV variable value for Elastic Beanstalk `aws:elasticbeanstalk:application:environment` setting|
|env_vars|{}|Map of custom ENV variables to be provided to the Jenkins application running on Elastic Beanstalk, e.g. `env_vars = { JENKINS_USER = 'admin' JENKINS_PASS = 'xxxxxx' }`|
|config_document|{ \"CloudWatchMetrics\": {}, \"Version\": 1} (none)|A JSON document describing the environment and instance metrics to publish to CloudWatch [Read more](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/health-enhanced-cloudwatch.html#health-enhanced-cloudwatch-configdocument)|
|healthcheck_url|"/healthcheck"|Application Health Check URL. Elastic Beanstalk will call this URL to check the health of the application running on EC2 instances|
|http_listener_enabled|"false"|Enable port 80 (http)|
|ssh_source_restriction|"0.0.0.0/0"|Used to lock down SSH access to the EC2 instances. You can specify a CIDR or a security group id|
|app|__REQUIRED__|EBS application name|
|instance_type|"t2.micro"|Instances type|
|associate_public_ip_address|"false"|Specifies whether to launch instances in your VPC with public IP addresses.|
|keypair|__REQUIRED__|Name of SSH key that will be deployed on Elastic Beanstalk and DataPipeline instance. The key should be present in AWS|
|root_volume_size|"8"|The size of the EBS root volume|
|root_volume_type|"gp2"|The type of the EBS root volume|
|availability_zones|"Any 2"|Choose the    lancer SSL certificate ARN. The certificate must be present in AWS Certificate Manager|
|loadbalancer_type|"classic"|Load Balancer type, e.g. 'application' or 'classic'|
|name|"app"|Solution name, e.g. 'app' or 'jenkins'|
|namespace|"global"|Namespace, which could be your organization name, e.g. 'cp' or 'cloudposse'|
|notification_endpoint|""|Notification endpoint|
|attributes|[]|Additional attributes (e.g. `policy` or `role`)|
|notification_protocol|"email"|Notification protocol|
|notification_topic_arn|""|Notification topic arn|
|notification_topic_name|""|Notification topic name|
|private_subnets|__REQUIRED__|List of private subnets to place EC2 instances|
|public_subnets|__REQUIRED__|List of public subnets to place Elastic Load Balancer|
|security_groups|__REQUIRED__|List of security groups to be allowed to connect to the EC2 instances|
|solution_stack_name|""|Elastic Beanstalk stack, e.g. Docker, Go, Node, Java, IIS. [Read more](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.platforms.html)|
|ssh_listener_enabled|"false"|Enable ssh port|
|ssh_listener_port|"22"|SSH port|
|stage|"default"|Stage, e.g. 'prod', 'staging', 'dev', or 'test'|
|autoscale_lower_bound|"20"|Minimum level of autoscale metric to add instance|
|tags|{}|Additional tags (e.g. `map('BusinessUnit`,`XYZ`)|
|tier|"WebServer"|Elastic Beanstalk Environment tier, e.g. ('WebServer', 'Worker')|
|rolling_update_type|"Health"|Set it to 'Immutable' to apply the configuration change to a fresh group of instances [Read more](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.rollingupdates.html)|
|updating_max_batch|"1"|Maximum count of instances up during update|
|updating_min_in_service|"1"|Minimum count of instances up during update|
|vpc_id|__REQUIRED__|ID of the VPC in which to provision the AWS resources|
|wait_for_ready_timeout|"20m"|
|zone_id|""|Route53 parent zone ID. The module will create sub-domain DNS records in the parent zone for the EB environment|
|autoscale_max|"3"|Maximum instances in charge|
|autoscale_min|"2"|Minumum instances in charge|
|autoscale_upper_bound|"80"|Maximum level of autoscale metric to remove instance|
|config_source|""|S3 source for config|
|preferred_start_time|"Sun:10:00"|Configure a maintenance window for managed actions in UTC|

# Outputs

|Name|Description|
|------|------|
|ec2_instance_profile_role_name|Instance IAM role name|
|elb_dns_name|ELB technical host|
|elb_zone_id|ELB zone id|
|host|DNS hostname|
|name|Name|
|security_group_id|Security group id|