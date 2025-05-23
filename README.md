# Configuring a Static Website using Amazon Route-53 (Project for Beginners)
This repository is a small personal project and a stepping stone for my cloud journey. Here I will share how I created a simple static website and host it online using cloud tools like Amazon S3, Route 53, CloudFront, Amazon Certificate Manager etc. along with sharing all the possible difficulties and errors one might encounter while performing this project. Separate markup files have been created for each AWS service used in this project, which contain basic information about the AWS service, how to configure it for this Project, and what all things could go wrong while configuring them.
Screenshots have also been included to guide the reader through each step. Feel free to contribute to this repository, suggest corrections or format change, new content, or mail me at nathja@rknec.edu for requesting new project content.  

## Contents
1. [Registering a Domain using Route 53.](Route-53.md#register-a-custom-domain-using-route-53).
2. [Create two S3 buckets for hosting the main domain and subdomain.](Amazon-S3.md#create-two-S3-buckets-for-hosting-the-main-domain-and-subdomain)
3. [Configure the root domain bucket for web hosting](Amazon-S3.md#3.-configure-the-root-domain-bucket-for-web-hosting).
4. Configure the subdomain bucket for web hosting.
5. Configure logging for website traffic
6. Upload index and website content
7. Upload an error document
8. Edit S3 Block Public Access settings
9. Attach a bucket policy
10. Test your domain endpoint
11. Add alias records for your domain and subdomain
12. Test the website

### Speeding up your website with Amazon CloudFront

### Cleaning up your example resources


## IMPORTANT
This project may incur costs for the use of certain AWS services such as registering a domain using Route53, which depends upon which type of TLD reader is trying to register. I will attach the price list of some of the TLD(Top Level Domains) to make sure that our readers can go through this project by spending minimum money.

Official tutorial Docs:
https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html#root-domain-walkthrough-before-you-begin
