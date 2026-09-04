# Creating an S3 Bucket with Terraform


**Author:** Mahmoud Alshaer  
**Email:** mahmoudalshaer8.a@gmail.com

---

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use Terraform to launch an S3 bucket. The goal is to install and set up Terraform, troubleshoot any errors, and successfuly apply the Terraform configuration to launch a bucket.

### Tools and concepts

Services I used were Terraform, S3, IAM, AW CLI. Key concepts I learnt include infrastructure as code, creating configuration files, modularity of code, using providers, plugins, state files, and lock files .

### Project reflection

This project took me approximately 1 hour. The most challenging part was customizing the S3 configuration using the Terraform documentation. It was most rewarding to see the image uploaded into the S3 bucket.

I chose to do this project today because learning Terraform is a very valuable skill and this project was the perfect gateway to start my learning journey with IaC and Terraform.

---

## Introducing Terraform

Terraform is a tool for managing our IT resources using code. Terraform is used for processing a configuration file that has been prepared that details the desired state of the infrastructure, Terraform then creates to set that desired state.

Terraform is one of the most popular tools used for infrastructure as code (IaC), which is a way to manage IT infrastructure instead of manually managing resources IaC automates that process with code.

Terraform uses configuration files to understand the desired state of the infrastructure. main.tf is the main configuration file that I will use in Terraform to describe that desired state.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

The configuration is structured in blocks instead of a single block of code. The advantage of doing this is the ability to work on updating different parts of main.tf without affecting other parts.

### My main.tf configuration has three blocks

The first block indicates that I am using AWS as the provider for this infrastructure. The second block provisions an amazon S3 bucket and gives it a unique name. The third block manages the buckets permissions which means blocking all public access.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_ljvh9876)

---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to look for ways I can customize my buckets configurations. The documentation shows example configurations, all the available parameters for a resource and usage rules.

I chose to customise my bucket by adding tags. because that lets me identify the project that I launched it for later on. When I launch my bucket, I can verify my customization by visiting the tags panel in the S3 console for this bucket.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_ffe757cd3)

---

## Terraform commands

I ran 'terraform init' to initialize Terraform. This means getting it to set up the backend to store state files and install the necessary plugins.

Next, I ran 'terraform plan' to get Terraform to compare the infrastructure in the main.tf file against my infrastructures current state then share back the execution plan.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

When I tried to plan my Terraform configuration, I received an error message that says "no valid credential sources found". because my terminal wasn't set up with AWS credentials yet. This needs to be set up to use the AWS provider plugin.

To resolve my error, first I installed AWS CLI, which is AWS' command line tool for interacting with an AWS environment instead of using the Managment Console the CLI lets me use text commands to do the same things.

I set up AWS access keys so that I have a way to login to my AWS account over the CLI. Once the access key id and the secret access key id are passed through aws configure the terminal now has the necessary AWS credentials.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

I ran 'terraform apply' to get Terraform to apply the changes it showed me when I ran terraform plan. Running 'terraform apply' will affect my AWS account by creating 2 resources, an S3 bucket and its set of permission settings.

The sequence of running terraform init, plan, and apply is crucial because you need to initialize Terraform first before getting to make any comparison between main.tf and the current infrastructure, or to connect to AWS in the first place.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I created a new resource block to upload an image called libad.jpg into the S3 bucket. The image will be uploaded straight away without being nested in a subfolder in the bucket.

We need to run terraform apply again because we have update the Terraform configuration file, which means there are changes that Terraform needs to review and compare with the current infrastructure again. This time only 1 new resource is created (image).

To validate that I've updated my configuration successfully, I checked the S3 bucket and confimred that a new image is inside. I also downloaded the image, and confirmed that it was the correct image that was initially uploaded.

![Image](http://nextwork.ai/encouraged_lavender_brave_salak/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
