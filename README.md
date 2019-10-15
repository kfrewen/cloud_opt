First you must configure an SSH key and import it to AWS

```bash
ssh-keygen -f ~/.ssh/id_aws
aws ec2 import-key-pair --key-name aws_key \
	--public-key-material file://~/.ssh/id_aws.pub
```

Then add the following to ~/.ssh/config:

```
Host *.compute.amazonaws.com
        User ubuntu
        IdentityFile ~/.ssh/id_aws
```

Then you can run the ansible playbook

```bash
ansible-playbook -i inventory aws_provisioning.yml
```
