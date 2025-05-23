## Introduction
Amazon Route 53 is a service that helps us achieve 3 things namely:
1) Registering Domains
2) Routing internet traffic to domains([DNS](#Further-Readings))
3) Checking the health of our resources such as web servers or pages.
   
In this project, the first two services of Amazon Route 53 will be used. Route 53 serves other purposes as well, such as a DNS Resolver. For more information about all things Route 53 can do, check out this [link](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html).

### 1. Register a Custom Domain using Route 53
1. In the search bar, type Route 53 and click the first option that pops up. If you are using Route 53 for the first time, you will be directed to the main page, else your Route 53 dashboard will pop up.
   ![image](https://github.com/user-attachments/assets/c41ac112-53ab-494d-b17d-a13e4a4eb532)

2. For registering a domain using Route 53 navigate through web pages as follows **Get Started** --> **Register a Domain**--> **Get started**.

3. You will land on a Register Domains page. here you can give your website a name and decide which Top Level Domain([TLD](#Further-Readings)) to select. For project purposes, select the cheapest TLD i.e.**.click** which charges only 3 USD per year! You can explore many more TLDs. Route 53 provides a whopping 355 TLDs.

4. Also [select a unique domain name](#Further-Readings) and check its availability. Your domain name should be unique across the internet. In the screenshot below it shows "statico.click is not available" because I have already registered this domain for this project.
   ![image](https://github.com/user-attachments/assets/51da0187-6141-436c-b6ee-9c824a65b693)


5. Once you find a unique domain name of your choice, press **Select**-->**Proceed to checkout**. From there you will be asked how long do you want your domain to be registered and do you want it to get **Auto-Renewed**. Select the suitable duration and uncheck the auto-renew option(unless you want to renew periodically) to avoid recurring periodic charges. Select **Next**. Enter your contact details on the next page, and then Review and Submit your contact information. After the domain registration is complete, which takes time, this is how your Dashboard should look.
   ![image](https://github.com/user-attachments/assets/c6407486-b3aa-4ccd-95d1-3eb26eb4d900)

6. Note that a **[Hosted Zone](#Further-Readings)** is automatically created by Route 53 for your registered domain. We will learn more about hosted zones in the upcoming sections. Now we'll [create our S3 Buckets](Amazon-S3.md) for hosting our main domain as well as our subdomain.

## 8. Add alias records for your domain and subdomain
####To add an alias record for your root domain (example.com)
1. Open the Route 53 console.
2. Choose **Hosted zones** in the left navigation pane.
3. In the list of hosted zones, choose the name of the hosted zone that matches your domain name.
4. Choose **Create record**.
5. Choose **Switch to wizard**.
6. Choose **Simple routing**, and choose **Next**. 
7. Choose **Define simple record**.
8. In **Record name**, accept the default value, which is the name of your hosted zone and your domain.
9. In **Value/Route traffic to**, choose **Alias to S3 website endpoint**.
10. Choose the **Region**.
11. Choose the S3 bucket.
12. The bucket name should match the name that appears in the Name box. In the **Choose S3 bucket** list, the bucket name appears with the Amazon S3 website endpoint for the Region where the bucket was created, for example, `s3-website-us-west-1.amazonaws.com` (example.com).
13. If your bucket does not appear in the Choose S3 bucket list, enter the Amazon S3 website endpoint for the Region where the bucket was created, for example, `s3-website-us-west-2.amazonaws.com`. For a complete list of Amazon S3 website endpoints, see Amazon S3 Website endpoints.
14. In Record type, choose A ‐ Routes traffic to an IPv4 address and some AWS resources.
15. For Evaluate target health, choose No.
16. Choose Define simple record.

    
## Further Readings

1. Route 53 official documentation by [AWS](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html).
2. What is DNS? by [CloudFare](https://www.cloudflare.com/learning/dns/what-is-dns/).
3. Top-Level Domains by [Wikipedia](https://en.wikipedia.org/wiki/Top-level_domain).
4. How to choose a domain name by [WixBlog](https://www.wix.com/blog/how-to-choose-domain-name).
5. Working with Hosted Zones by [AWS](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html).

   


    
