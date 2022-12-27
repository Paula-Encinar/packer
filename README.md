# packer
2 important topics, builders and communicators. 

## How to build an AMI in AWS

There are three options: 

- amazon-ebs: Create EBS-backed AMIs by launching a source AMI and re-packaging it into a new AMI after provisioning. If in doubt, use this builder, which is the easiest to get started with.

- amazon-instance: Create instance-store AMIs by launching and provisioning a source instance, then rebundling it and uploading it to S3.
- amazon-chroot: Create EBS-backed AMIs from an existing EC2 instance by mounting the root device and using a Chroot environment to provision that device. This is an advanced builder and should not be used by newcomers. However, it is also the fastest way to build an EBS-backed AMI since no new EC2 instance needs to be launched.
- amazon-ebssurrogate - Create EBS -backed AMIs from scratch. Works similarly to the chroot builder but does not require running in AWS. This is an advanced builder and should not be used by newcomers.

### Amazon EBS Volume Builder
The Amazon Plugin is able to create Amazon EBS Volumes which are preinitialized with a filesystem and data.

- amazon-ebsvolume - Create EBS volumes by launching a source AMI with block devices mapped. Provision the instance, then destroy it, retaining the EBS volumes and or Snapshot.

### Autenthication 

There are some options, I used to use Environment Variables. 

### Communicators

Communicators are the mechanism Packer uses to upload files, executer scripts, etc. with the machine being created. Communicators are configured within the builder section.

- none: no communicators
- ssh 
- winrm

Also for example for docker builder there are docker communicator that uses docker exec or docker cp. 

## Command 

Initialize my Packer configuration: 

``packer init . ``

Format template: 

``packer fmt .``

Syntactically validation:

``packer validate .``

Build packer image: 

`` packer build aws-ubuntu-pkr.hcl``