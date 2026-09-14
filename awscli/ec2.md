https://docs.aws.amazon.com/cli/v1/userguide/cli-services-ec2-instances.html

** Launch your instance

aws ec2 run-instances --image-id ami-0f9629c639a701fa7 --count 1 --instance-type t2.micro --key-name collins-key --security-group-ids sg-0333685c0c1310bfa --subnet-id subnet-03842d23d59af4546

** Add a block device to your instance:

--block-device-mappings "[{\"DeviceName\":\"/dev/sdf\",\"Ebs\":{\"VolumeSize\":20,\"DeleteOnTermination\":false}}]"


** Add a tag to your instance:

aws ec2 create-tags --resources i-077540d0ff90f3af9 --tags Key=Name,Value=collins-instance Key=Dept,Value=DevOps

** List your instances:

aws ec2 describe-instances

aws ec2 describe-instances --filters "Name=instance-type,Values=t2.micro" --query "Reservations[].Instances[].InstanceId"

aws ec2 describe-instances --filters "Name=tag:Name,Values=MyInstance"

aws ec2 describe-instances --filters "Name=image-id,Values=ami-x0123456,ami-y0123456,ami-z0123456"

** Delete your instance:

aws ec2 terminate-instances --instance-ids i-5203422c
