## Introduction
Amazon Route 53 is a service that helps us achieve 3 things namely:
1) Registering Domains
2) Routing internet traffic to domains([DNS](Route-53.md##Further-Readings))
3) Checking the health of our resources such as web servers or pages.
   
In this project, the first two services of Amazon Route 53 will be used. Route 53 serves other purposes as well, such as a DNS Resolver. For more information about all things Route 53 can do, check out this [link](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html).

### 1. Register a Custom Domain using Route 53
1. In the search bar, type Route 53 and click the first option that pops up. If you are using Route 53 for the first time, you will be directed to the main page, else your Route 53 dashboard will pop up.
   ![image](https://github.com/user-attachments/assets/c41ac112-53ab-494d-b17d-a13e4a4eb532)

2. For registering a domain using Route 53 navigate through web pages as follows **Get Started** --> **Register a Domain**--> **Get started**.

3. You will land on a Register Domains page. here you can give your website a name and decide which Top Level Domain([TLD](Route-53.md##Further-Readings)) to select. For project purposes, select the cheapest TLD i.e.**.click** which charges only 3 USD per year! You can explore many more TLDs. Route 53 provides a whopping 355 TLDs.

4. Also [select a unique domain name](Route-53.md##Further-Readings) and check its availability. Your domain name should be unique across the internet. In the screenshot below it shows "statico.click is not available" because I have already registered this domain for this project.
   ![image](https://github.com/user-attachments/assets/51da0187-6141-436c-b6ee-9c824a65b693)


5. Once you find a unique domain name of your choice, press **Select**-->**Proceed to checkout**. From there you will be asked how long do you want your domain to be registered and do you want it to get **Auto-Renewed**. Select the suitable duration and uncheck the auto-renew option(unless you want to renew periodically) to avoid recurring periodic charges. Select **Next**. Enter your contact details on the next page, and then Review and Submit your contact information. After the domain registration is complete, which takes time, this is how your Dashboard should look.
   ![image](https://github.com/user-attachments/assets/c6407486-b3aa-4ccd-95d1-3eb26eb4d900)

6. Note that a **[Hosted Zone](Route-53.md##Further-Readings)** is automatically created by Route 53 for your registered domain. We will learn more about hosted zones in the upcoming sections. Now we'll [create our S3 Buckets](Amazon-S3.md) for hosting our main domain as well as our subdomain.

## Further Readings

1. Route 53 official documentation by [AWS](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html).
2. What is DNS? by [CloudFare](https://www.cloudflare.com/learning/dns/what-is-dns/).
3. Top-Level Domains by [Wikipedia](https://en.wikipedia.org/wiki/Top-level_domain).
4. How to choose a domain name by [WixBlog](https://www.wix.com/blog/how-to-choose-domain-name).
5. Working with Hosted Zones by [AWS](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html).

   


    
