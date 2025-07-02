# Module 4 Hello World Cloud Formation Stack

## Topics Learned in Module 4
- How to choose your AWS region.
- AWS Global Infrastructure
- IaC and AWS Cloud Formation

## Project Description
This simple project demonstrates how to create and deploy an AWS CloudFormation stack to explore the AWS global infrastructure model. By launching a "Hello World" stack in multiple regions, it reinforces key cloud concepts such as AWS Regions, Availability Zones, and the fundamentals of Infrastructure as Code (IaC) — all without provisioning any billable resources. The template used outputs a regional message, allowing you to observe how CloudFormation interacts with different regional environments in a safe, free-tier-friendly way.

## Steps
### 1. Create a CloudFormation Template
- A cloud formation template is a text-based document (.json or .yaml) that act as a blueprint for your infrastructure. You tell it the resources you need and then Cloud Formation takes care of the provisioning and configurations.
- This json file defines a minimal CloudFormation template used to create a stack without provisioning any AWS resources. It contains metadata, a placeholder resource (AWS requires at least one), and an outputs section that displays a simple message indicating the region where the stack was deployed.
```
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "Hello World CloudFormation Stack",
  "Resources": {
    "DummyTopic": {
      "Type": "AWS::SNS::Topic",
      "Properties": {}
    }
  },
  "Outputs": {
    "Message": {
      "Description": "A simple message",
      "Value": {
        "Fn::Sub": "Hello from CloudFormation in the ${AWS::Region} region!"
      }
    }
  }
}
```

### 2. Pick two regions and deploy the json
- This lab is meant to emulate the deployment of the same resource in two AWS regions. So we will do something very similar and deploy the same stack in two AWS regions on opposite sides of the U.S. Therefore, I went with N. Virginia (us-east-1) and N. California (us-west-1) for this lab.
- So I first went to the us-east-1 region and opened CloudFormation to create a stack.

![image](https://github.com/user-attachments/assets/9d63ea68-eeda-483a-b41b-7ef9364ed9f4)

- Then I uploaded the .json file as the template.

![image](https://github.com/user-attachments/assets/4572025a-16d6-418d-8e55-024f0946f79e)

- I then switched to the us-west-1 template and repeated the previous steps to create a stack over there as well using the same json file.

### 3. View the message in both regions
- First I checked the stack output in the N.Virginia region and saw the following.

![image](https://github.com/user-attachments/assets/cc397ef8-bde7-4396-8f9d-97940c59d93c)


- Then I checked the stack output in N.California region and saw the following.

![image](https://github.com/user-attachments/assets/970c969f-8688-4692-93ba-34b3429b3d2d)

## Conclusion
This project offered hands-on experience with CloudFormation and helped visualize how AWS organizes its infrastructure across regions. By deploying identical stacks in multiple AWS regions, I deepened my understanding of how regions and availability zones work, while also gaining foundational experience with Infrastructure as Code using AWS’s native tooling. It’s a useful first step toward managing real-world cloud resources with repeatable, version-controlled templates.
