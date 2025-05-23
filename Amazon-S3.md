## Introduction
Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can use Amazon S3 to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides management features so that you can optimize, organize, and configure access to your data to meet your specific business, organizational, and compliance requirements. For detailed information on features of S3, types of storage classes and pricing read the full [documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).

## 2. Create two S3 buckets for hosting the main domain and subdomain.
1. Open Amazon S3 on your console https://console.aws.amazon.com/s3/ or search it using the search bar.
2. Create your root domain bucket by navigating **Create Bucket**.
3. Set the bucket settings to the following:<br>
   i) **Bucket Type**- General Purpose<br><br>  ii) **Bucket Name**- *Bucket names must be 3 to 63 characters and unique within the global namespace. Bucket names must also begin and end with a letter or number. Valid characters are a-z, 0-9, periods (.), and hyphens (-).* (like `example.com`)<br><br>  iii) Choose the **bucket region**. You can navigate your region from the top-right corner of your management console just beside your account menu.<br>  Choose a Region that is geographically close to you to minimize latency and costs, or to address regulatory requirements. The Region that you choose determines your Amazon S3 [website endpoint]().<br><br>
Leave all the other settings as they are in their default values.   
![image](https://github.com/user-attachments/assets/0992efba-1102-44a2-92a3-bc7e3242ffc0)
![image](https://github.com/user-attachments/assets/0346d30c-cc56-4eae-adf5-fdb3db6a161e)
![image](https://github.com/user-attachments/assets/c1e63240-8750-4910-aecd-d80a3cdd4405)


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
The index document name is case sensitive and must exactly match the file name of the HTML index document that you plan to upload to your S3 bucket. When you configure a bucket for website hosting, you must specify an index document. Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders.<br>
7. To provide your own custom error document for 4XX class errors, in **Error document**, enter the custom error document file name.<br>
The error document name is case sensitive and must exactly match the file name of the HTML error document that you plan to upload to your S3 bucket. If you don't specify a custom error document and an error occurs, Amazon S3 returns a default HTML error document.<br>
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





