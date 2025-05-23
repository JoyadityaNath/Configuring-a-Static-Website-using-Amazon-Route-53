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
   Note that the buckets *statico.click* and *`www.statico.click`* are my main domain and subdomain buckets respectively. The third bucket *logs.statico.click* is for logging metadata which we will discuss later. 

## 3. Configure the root domain bucket for web hosting


