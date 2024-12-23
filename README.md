# AWS-S3-Buckets-Project
![Amazon cloud project workflow](https://github.com/user-attachments/assets/63041ff6-ee92-4449-af55-02fbcb6faea1)

The above image displays the workflow of this project. 

Scenario 1: When the user hits “www.xyz.com/bucket1.jpg”, the Cloudfront redirects the request to “S3 bucket 1” & loads the image bucket1.jpg.

Scenario 2: When the user hits “www.xyz.com/b2/bucket2.jpg”, the Cloudfront redirects the request to “S3 bucket 2” & loads the bucket2.jpg image. 
## Objectives

  -Learn how to serve content from multiple S3 buckets using AWS CloudFront. <br>
  -Understand the role of Amazon CloudFront as a fast and secure content delivery network (CDN). <br>
  -Explore Amazon S3 as a scalable and secure object storage service. <br>
  -Configure multiple S3 buckets and distribute content via CloudFront. <br>
  -Set up error pages and implement global distribution restrictions using the AWS Management Console. <br>

### Skills Learned

  -Configure multiple S3 buckets for content storage. <br>
  -Set up a CloudFront distribution to deliver content globally. <br>
  -Optimize origins and behaviors for efficient content delivery. <br>
  -Implement custom error pages for improved user experience. <br>
  -Manage URL invalidations to ensure updated content delivery. <br>
  -Enforce restrictions for secure and compliant access. <br>
 
### Tools Used

- **Amazon S3**: For scalable and secure object storage.
- **Amazon CloudFront**: For global content delivery with low latency and high speed.
- **AWS Management Console**: For configuring and managing services.

## Steps
**1. Create S3 buckets** 
  -To create an S3 bucket you first have to create an Amazon cloud management account. From there, navigate to the top search bar and type in "S3" and click on the application. Then go to Buckets, and click on Create Bucket.<br>
  ![Create S3 bucket](https://github.com/user-attachments/assets/a68a11b9-2af4-4f43-a779-5f046280e815)<br>

  -For this project I created 2 buckets. They are named Taylormade and Callaway. No changes to the bucket settings are necessary for this project. From here, we can upload images to each of the buckets and this is what will appear when the domain name from the  CloudFront Distribution is typed into a browsers search bar. I will demonstrate this in step 3.<br>
  ![image](https://github.com/user-attachments/assets/5ddf8551-dc70-488d-9e8d-860d257f27ea)<br>


**2. Create a CloudFront distribution** 
  -The next step is creating a CloudFront distribution. To do this, go back to the home console. Then in the search bar type in "CloudFront". Click on that application, and then from there click on "Create Distribution". <br>
  ![CloudFront](https://github.com/user-attachments/assets/85075471-bf8b-475e-b1dc-cabe378d4383)<br>

  -On origin domain, you can find the buckets you made previously. The domain I selected was the Taylormade bucket. For this project I used the legacy access identity, and clicked on the option "Yes update the bucket policy". <br>
  ![cloud distribution](https://github.com/user-attachments/assets/acc29bbd-e22d-411b-9cea-b2ba99f8e172) <br>
  -I repeated the last step and added an origin domain for the Callaway bucket.<br>
  ![connecting callaway to taylormade](https://github.com/user-attachments/assets/f13f5946-249d-4fa5-87fa-649090a3b4e8)<br>

  -The bucket policy in Amazon S3 is a JSON-based access control mechanism that defines permissions for accessing the objects in a bucket. When integrating with Amazon CloudFront using a legacy Origin Access Identity (OAI), the bucket policy is updated to ensure that only CloudFront can access the bucket. Here's how it works and what it accomplishes:<br>

  -What the Bucket Policy Does:<br>
    -Restricts Direct Access: It prevents public or unauthorized access to your S3 bucket objects. Only requests coming through the specified CloudFront distribution are allowed.<br>
    -Grants CloudFront Access: The policy grants permissions to the OAI, which acts as CloudFront's identity. This ensures that CloudFront can retrieve content from the bucket to serve it to end-users.<br>
    -Secures Content: By enforcing access through CloudFront, you gain the benefits of CloudFront's caching, security features, and access control mechanisms, while keeping the S3 bucket itself private.<br>

**3. Update origins and behaviors**<br>
  -The first thing we will test is if the domain name works from the CloudFront Distribution. So, head back to CloudFront, and then click on the distribution that was made in the previous step. Under the details tab, we can copy the distribution domain name into the browsers search bar. We will also add the name of the JPG file to the domain. Please see the pictures below for how the domain was typed in.<br>
  -S3 bucket 1:
  ![taylormade initial bucket](https://github.com/user-attachments/assets/b4bbce16-5bf2-41c5-a45f-e6a7c277d2f1)<br>

  -Now S3 bucket 1 has been connected, and we will add S3 bucket 2 (Callaway bucket). To do this, we navigate to CloudFront, and then click on Origin, and create Origin.<br>
  ![Origin](https://github.com/user-attachments/assets/e94777b1-e67d-4bcf-9471-f738011a67ba)<br>

  -Here are the settings for the Origin.<br>
  ![image](https://github.com/user-attachments/assets/afae79bd-8d88-4bbe-b64c-fb4f44963484)<br>

  -Next we will update the behaviors. CloudFront allows you to specify behaviors like caching rules, query string forwarding, and origin failover to ensure efficient and reliable content delivery.<br>
  ![callaway behavior](https://github.com/user-attachments/assets/7719639c-e92e-4d7d-9dbd-b5af28516077)<br>
  
  -As you can see, we are adding a new path pattern (b2 or bucket 2) that will show the Callaway image. So now if we type in the domain name into a browser, and add /b2/<image.jpg>, then the Callaway image will appear.<br>
  ![Smoke connected bucket](https://github.com/user-attachments/assets/42d53843-88d8-43b9-99af-3aa15b850da6)


**4. Setup error page** 

**5. Setup URL invalidations** 

**6. Setup restrictions & Terminate** 

In the final step I set the environmental variable SSLKEYLOGFILE to the path where I wanted the web browsers to capture the private keys used in SSL encryption. In Wireshark, I set the Protocol TLS Pre-master secret log file to decrypt the encrypted traffic capture.<br>

This project involved using Kali Linux and TCPDump to capture, analyze, and log network traffic while developing critical cybersecurity and scripting skills. After setting up the Kali Linux VM and Visual Studio Code, familiarity with essential TCPDump commands was developed, such as limiting packet captures, applying advanced filters, and recording timestamps. The project progressed to building an automated logging tool in Bash, which facilitated organized and efficient packet capture.

Captured packets were saved in .pcap dump files for analysis using tools like Wireshark, enabling detailed inspection of both encrypted and unencrypted traffic. Advanced functionalities, like creating sequenced dump files based on time intervals or file sizes, enhanced the scope for passive monitoring. Finally, the integration of environment variables such as SSLKEYLOGFILE allowed TLS session keys to be logged, making it possible to decrypt HTTPS traffic for in-depth analysis of web interactions.
