-------- How to Run this playbook ---------

ansible-playbook launch_ec2.yml -e region=ap-south-1 -e vpc_id={your vpc id} -e instance_type=t2.micro -e keypair={you key file name} -e count=1 -e volume_size=10 -e vpc_subnet_id={your subnet id}
