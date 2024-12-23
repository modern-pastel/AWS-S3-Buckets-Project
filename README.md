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
   
**2. Create a Cloudfront distribution** 

**3. Update origins and behaviors**<br>

**4. Setup error page** 

**5. Setup URL invalidations** 

**6. Setup restrictions & Terminate** 

In the final step I set the environmental variable SSLKEYLOGFILE to the path where I wanted the web browsers to capture the private keys used in SSL encryption. In Wireshark, I set the Protocol TLS Pre-master secret log file to decrypt the encrypted traffic capture.<br>

This project involved using Kali Linux and TCPDump to capture, analyze, and log network traffic while developing critical cybersecurity and scripting skills. After setting up the Kali Linux VM and Visual Studio Code, familiarity with essential TCPDump commands was developed, such as limiting packet captures, applying advanced filters, and recording timestamps. The project progressed to building an automated logging tool in Bash, which facilitated organized and efficient packet capture.

Captured packets were saved in .pcap dump files for analysis using tools like Wireshark, enabling detailed inspection of both encrypted and unencrypted traffic. Advanced functionalities, like creating sequenced dump files based on time intervals or file sizes, enhanced the scope for passive monitoring. Finally, the integration of environment variables such as SSLKEYLOGFILE allowed TLS session keys to be logged, making it possible to decrypt HTTPS traffic for in-depth analysis of web interactions.
