# ECS Container draining
Amazon EC2 Container Service (Amazon ECS) is a container management service that makes it easy to run, stop, and manage Docker containers on a cluster of Amazon EC2 instances.  When you run tasks using Amazon ECS, you place them on a cluster, which is a logical grouping of EC2 instances. Amazon ECS downloads your container images from a registry that you specify, and runs those images on the container instances within your cluster.

There are times when EC2 instances need to be removed from the cluster, for example cluster scale-down or updating an AMI. Today we have delivered Container Instance Draining to simplify these scenarios. The draining state prevents new tasks from being started on the container instance, notifies the service scheduler to move tasks that are running on the instance to other instances in the cluster, and enables you to wait until tasks have successfully moved before terminating the instance.  



# Overview of steps
1. Download the CloudFormation template

2. Launch the CloudFormation template that creates the following AWS resources:

* The VPC and associated network elements (subnets, security groups, route table, etc)
* ECS Cluster, ECS service, a sample ECS task definition
* Auto scaling group with two EC2 instances and a termination lifecycle hook
* Lambda function, permissions to invoke lambda, and lambda execution roles
* SNS topic, policy

For the full solution overview visit [Blog link](https://aws.amazon.com/blogs/compute/how-to-automate-container-instance-draining-in-amazon-ecs).

## CloudFormation template
 - cform/ecs.yaml

***

Copyright 2016-2017 Amazon.com, Inc. or its affiliates. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License. A copy of the License is located at

http://aws.amazon.com/apache2.0/

or in the "license" file accompanying this file. This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
