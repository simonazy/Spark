# How to launching EMR cluster from command line
### Below example creates a 3 Node EMR cluster with 1 master and 2 slave Nodes.

    aws emr create-cluster \
    --applications Name=Ganglia Name=Spark Name=Zeppelin \
    --ebs-root-volume-size 10 \
    --ec2-attributes \
    '{"KeyName":<cluster-name>,"InstanceProfile":<IAMROLE>,"SubnetId":<subnet-id>,"EmrManagedSlaveSecurityGroup":<slave-security-group-id>,"EmrManagedMasterSecurityGroup":<master-security-group-id>}' \
    --service-role IAMROLE \
    --enable-debugging \
    --release-label <emr release version e.g emr-5.29.0> \
    --log-uri <s3-bucket-path-for-logging> \
    --name <cluster-name> \
    --instance-groups \
    '[ \
    {"InstanceCount":1,"EbsConfiguration":{"EbsBlockDeviceConfigs":[{"VolumeSpecification":{"SizeInGB":32,"VolumeType":"gp2"},"VolumesPerInstance":2}]},"InstanceGroupType":"MASTER","InstanceType":"m5.xlarge","Name":"Master Instance Group"}, \
    {"InstanceCount":2,"EbsConfiguration":{"EbsBlockDeviceConfigs":[{"VolumeSpecification":{"SizeInGB":32,"VolumeType":"gp2"},"VolumesPerInstance":2}]},"InstanceGroupType":"CORE","InstanceType":"m5.xlarge","Name":"Core Instance Group"}\
    ]' \
    --scale-down-behavior TERMINATE_AT_TASK_COMPLETION \
    --region us-east-1

# EMR workflow

![image](https://user-images.githubusercontent.com/56880104/142663511-3422296d-df4c-4c3b-9bea-c8f7c5eaed51.png)

# AWS s3 CLI Cheat Sheet

![image](https://user-images.githubusercontent.com/56880104/142663554-e778982d-6a3f-4ce6-a113-d942c4ac3587.png)

# More reference:
[Getting started with Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html#emr-getting-started-plan-and-configure), [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
