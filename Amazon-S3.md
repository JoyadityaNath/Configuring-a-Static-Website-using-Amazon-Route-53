## Introduction
Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can use Amazon S3 to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides management features so that you can optimize, organize, and configure access to your data to meet your specific business, organizational, and compliance requirements. For detailed information on features of S3, types of storage classes and pricing read the full [documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).

## 2. Create two S3 buckets for hosting the main domain and subdomain.
1. Open Amazon S3 on your console https://console.aws.amazon.com/s3/ or search it using the search bar.
2. Create your root domain bucket by navigating **Create Bucket**.
3. Set the bucket settings to the following:<br>
   i) **Bucket Type**- General Purpose<br><br>  ii) **Bucket Name**- *Bucket names must be 3 to 63 characters and unique within the global namespace. Bucket names must also begin and end with a letter or number. Valid characters are a-z, 0-9, periods (.), and hyphens (-).* (like `example.com`)<br><br>  iii) Choose the **bucket region**. You can navigate your region from the top-right corner of your management console just beside your account menu.<br>  Choose a Region that is geographically close to you to minimize latency and costs, or to address regulatory requirements. The Region that you choose determines your Amazon S3 [website endpoint]().<br> iv) By default, Amazon S3 blocks public access to your account and buckets. Uncheck the **Block all public access** option under the **Block Public Access settings for this bucket**. Unchecking the "Block all public access" option in Amazon S3 removes the default security barrier that prevents your bucket or its objects from being accessible to the public over the internet.<br><br>
Leave all the other settings as they are in their default values.   
![image](https://github.com/user-attachments/assets/0992efba-1102-44a2-92a3-bc7e3242ffc0)
![image](https://github.com/user-attachments/assets/0346d30c-cc56-4eae-adf5-fdb3db6a161e)
![image](https://github.com/user-attachments/assets/5a469d5e-cb2b-4ed3-a935-fcb206323de0)



5. Similarly create another bucket for your subdomain with a different name(`www.example.com`) in the same region. After creating both the buckets, you can view them in the **General Purpose Buckets** section.
   ![image](https://github.com/user-attachments/assets/d0468586-ea4b-4b1a-aa3f-a9c4980cae7e)<br>
   Note that the buckets *`statico.click`* and *`www.statico.click`* are my main domain and subdomain buckets respectively. The third bucket *logs.statico.click* is for logging metadata which we will discuss later. 

## 3. Configure the root domain bucket for web hosting
1. Click your root domain bucket name and it will take you to the bucket settings.
2. Choose **Properties** tab and scroll down to the bottom to navigate to **Static website hosting** section.
3. Under **Static website hosting**, choose **Edit**.
4. Under **Static website hosting**, choose **Enable**.
5. Choose **Host Static Website** under **Hosting Type** to host a website.
6. In **Index document**, enter the file name of the index document, typically *`index.html`*.<br>
The index document name is case sensitive and must exactly match the file name of the HTML index document that you plan to upload to your S3 bucket. When you configure a bucket for website hosting, you must specify an index document. Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders. <br>
7. Create an `index.html` file locally and upload it to your root domain bucket. A sample index file code is given below.
```html
<html xmlns="http://www.w3.org/1999/xhtml" >
<head>
    <title>My Website Home Page</title>
</head>
<body>
  <h1>Welcome to my website</h1>
  <p>Now hosted on Amazon S3!</p>
</body>
</html>
```

8. To provide your own custom error document for 4XX class errors, in **Error document**, enter the custom error document file name.<br>
The error document name is case sensitive and must exactly match the file name of the HTML error document that you plan to upload to your S3 bucket. If you don't specify a custom error document and an error occurs, Amazon S3 returns a default HTML error document.<br>
9. Create an `error.html` file locally and upload it to your root domain bucket. A sample error file code is given below.<br>
```html
<html xmlns="http://www.w3.org/1999/xhtml" >
<head>
    <title>Error Page</title>
</head>
<body>
  <h1>404 ERROR</h1>
  <p>Sorry for the Issue</p>
</body>
</html>
```
8. Choose **Save changes**.<br>
Amazon S3 enables static website hosting for your bucket. At the bottom of the page, under Static website hosting, you see the website endpoint for your bucket.
9. Under **Static website hosting**, note the `Endpoint`.<br>
The Endpoint is the Amazon S3 website endpoint for your bucket. After you finish configuring your bucket as a static website, you can use this endpoint to test your website.<br><br>
![image](https://github.com/user-attachments/assets/5bb68432-c18f-47aa-b21d-5e76c834a57a)

## 4. Configure the Subdomain bucket for web hosting
1. Click your subdomain bucket name and it will take you to the bucket settings.
2. Choose **Properties** tab and scroll down to the bottom to navigate to **Static website hosting** section.
3. Under **Static website hosting**, choose **Edit**.
4. Under **Static website hosting**, choose **Enable**.
5. Choose **Redirect requests for an object** under **Hosting Type** to host a website. This  option is used to redirect visitors who try to access a specific object (file) to another location — either within the same bucket, another bucket, or even an external URL.
6. In the **Host Name** box, enter your root domain, for example, `example.com`. So now if you enter your subdomain name on any browser, it will redirect it to the root domain automatically. 
7. For **Protocol**, choose **http**.
8. Choose **Save changes**.<br><br>
![image](https://github.com/user-attachments/assets/4644b163-fac3-400a-9d77-33fbeb0e0149)

## 5. Configure logging for Website Traffic
If you want to track the number of visitors accessing your website, you can enable logging for your root domain bucket. Logging can also be done using CloudFront which we will do in the section [Speeding up your website using Amazon Cloudfront](CloudFront.md).<br><br>
1. Open the Amazon S3 console and in the same region where you created the bucket that is configured as a static website, create a bucket for logging, for example `logs.example.com`.
2. Create a folder for the server access logging log files (for example, logs).
3. (Optional) If you want to use CloudFront to improve your website performance, create a folder for the CloudFront log files inside `logs.example.com` (for example, cdn).<br>
![image](https://github.com/user-attachments/assets/573d3368-7694-4641-bffc-4b6bcf789b01)<br>

4. In the **Buckets** list, choose your root domain bucket.
5. Choose **Properties**.
6. Under **Server access logging**, choose **Edit**.
7. Choose **Enable**.
![image](https://github.com/user-attachments/assets/e701a78a-474a-4d52-94c2-ae10bc66ed0a)<br>

8. Under the **Target bucket**, choose the bucket and folder destination for the server access logs:
9. Browse to the folder and bucket location:<br>
    i)Choose **Browse S3**.<br>
   ii) Choose the bucket name, and then choose the logs folder.<br>
  iii) Choose **Choose destination**.<br>
   ![image](https://github.com/user-attachments/assets/3548ffbe-fba8-4134-b40f-f3982ed46917)<br>
   You can leave the remaining settings at their default values.

10. Choose **Save changes**.<br><br>

In your log bucket, you can now access your logs. Amazon S3 writes website access logs to your log bucket within a few minutes after someone visits your website.

## 6. Attach a Bucket Policy
1. Under **Buckets**, choose the name of your bucket.
2. Choose **Permissions**.
3. Under **Bucket Policy**, choose **Edit**.
4. To grant public read access for your website, copy the following bucket policy, and paste it in the Bucket policy editor.
   ```JSON
   {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
   }
   ```
5. Update the Resource to your bucket name.<br>
In the above example bucket policy, *Bucket-Name* is a placeholder for the bucket name. To use this bucket policy with your own bucket, you must update this name to match your bucket name.<br>
6. Choose **Save changes**.<br>
![image](https://github.com/user-attachments/assets/ef9d1b4e-d01e-4e62-a3d2-0e0201beb8e2)<br><br>
Attaching a bucket policy to the domain bucket will allow public read access. You replace the *Bucket-Name* in the example bucket policy with the name of your domain bucket.
After you edit S3 Block Public Access settings, you can add a bucket policy to grant public read access to your bucket. When you grant public read access, anyone on the internet can access your bucket.<br>
## 7. Test your Domain Endpoint
1. Under **Buckets**, choose the name of your bucket.
2. Choose **Properties**.
3. At the bottom of the page, under **Static website hosting**, choose your Bucket website endpoint.

4. Your index document opens in a separate browser window.







