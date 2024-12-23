# AWS-S3-Buckets-Project
![Amazon cloud project workflow](https://github.com/user-attachments/assets/63041ff6-ee92-4449-af55-02fbcb6faea1)

The above image displays the workflow of this project. 

Scenario 1: When the user hits "`www.xyz.com/bucket1.jpg`”, the Cloudfront redirects the request to “S3 bucket 1” & loads the image bucket1.jpg.

Scenario 2: When the user hits “`www.xyz.com/b2/bucket2.jpg`”, the Cloudfront redirects the request to “S3 bucket 2” & loads the bucket2.jpg image. 
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
**Step 1. Create S3 buckets** 
  -To create an S3 bucket you first have to create an Amazon cloud management account. From there, navigate to the top search bar and type in "S3" and click on the application. Then go to Buckets, and click on Create Bucket.<br>
  ![Create S3 bucket](https://github.com/user-attachments/assets/a68a11b9-2af4-4f43-a779-5f046280e815)<br>

  -For this project I created 2 buckets. They are named Taylormade and Callaway. No changes to the bucket settings are necessary for this project. From here, we can upload images to each of the buckets and this is what will appear when the domain name from the  CloudFront Distribution is typed into a browsers search bar. I will demonstrate this in step 3.<br>
  ![image](https://github.com/user-attachments/assets/5ddf8551-dc70-488d-9e8d-860d257f27ea)<br>


**Step 2. Create a CloudFront distribution** 
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


**Step 3. Update origins and behaviors**<br>
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


**Step 4. Setup error page** 
  -Next I setup a custom error response page. The first part is going back to S3, and then clicking on our Taylormade bucket. We will upload another JPG image and in this case I used a 403 error picture from Google.<br>
  ![error page](https://github.com/user-attachments/assets/8ce76fd6-733b-4bf1-a09d-0d8bfacd48f6)<br>

  -Then we will navigate back to CloudFront and then click on the Distribution that was made, then click on "Create error page response". The HTTP error code used will be 403, and the HTTP response code will be 403. Lastly on the response page path, we will type in the JPG image name from the Taylormade bucket that was uploaded.<br>
  ![Error response page](https://github.com/user-attachments/assets/7e957f3f-bb1c-4f85-becb-05302b0bee68)<br>
  
  -Now if we type in an incorrect response path, the 403 image that we uploaded will appear.<br>
  ![403 error page](https://github.com/user-attachments/assets/3e7b1d97-58b7-4361-a524-daaed869cc04)<br>
  

**Step 5. Setup URL invalidations** 
  -First, what are URL invalidations? By default, CloudFront serves cached content from its edge locations to reduce latency and improve performance. If you update an object in your origin (e.g., an updated image or a changed CSS file), the cached version in the edge locations remains the same until it expires based on the cache settings. Invalidations allow you to explicitly remove the outdated cached objects and force CloudFront to fetch the latest version from the origin.<br>
  -For example, in the Taylormade S3 bucket if I wanted to update the Qi10 driver image, to a different one (in this case I will use the P7CB iron image) there are a couple of things I have to do. Navigating back to S3, I will click on the Taylormade bucket, and delete the Qi10 driver image. <br>
  ![image](https://github.com/user-attachments/assets/391cc258-c5ea-43cf-bbf5-8657c8f3ecb8)<br>

  
  -Next I will upload an image of P7CB like I did in step 1, and still have the JPG named as Qi10.jpg for demonstration purposes. Now if we type in the same URL again, then the image of the Qi10 driver will still appear.<br>
  ![still same qi190 image](https://github.com/user-attachments/assets/501e18d0-0b42-4873-ad1d-5a2dfcd8c425)<br>

  -To fix this, we will now setup the URL invalidation. We will navigate back to CloudFront, then the distribution that was made, then Invalidations, then click on Create Invalidation. It will ask for an object path, so we will type in /Qi10.jpg.<br>
  ![Invalidation fix path](https://github.com/user-attachments/assets/515fac99-5691-493f-8ecf-b64b3fec6bc2)<br>

  -Now if we type in the same URL, the new image will appear and the URL invalidation has been successfully updated.<br>
  ![New image uploaded](https://github.com/user-attachments/assets/f0498790-b055-48ba-aea2-59b8437b476f)<br>


**Step 6. Setup restrictions** 
  -The final step in this project is showing how country restrictions can be setup for our S3 bucket. There are 2 ways of doing this, we can create a white list or black list. A white list allows only the countries we select to be able to access this S3 bucket, and every other country is banned. A black list on the other hand bans access to every country that is selected, and allows access from everywhere else. For this project I believe that it was easier to use a white list and only allow people in the US to have access to this bucket. We will navigate to CloudFront, then Distributions, then our distribution that was made, and then Security. Under CloudFront geographic restrictions, we will select Allow list, and then select United States.<br>
  ![country restrictions](https://github.com/user-attachments/assets/ac8b102e-af45-4bcc-ab14-2385ff0ec427)<br>


**Conclusion**
In this project, we successfully learned how to serve content from multiple S3 buckets using AWS CloudFront through the AWS Management Console. By completing each task step-by-step, we gained hands-on experience with key configurations:

  -Creating S3 buckets<br>
  -Setting up a CloudFront distribution<br>
  -Updating origins and behaviors<br>
  -Configuring error pages<br>
  -Managing URL invalidations<br>
  -Implementing access restrictions<br>

  
This comprehensive approach not only deepened our understanding of AWS CloudFront but also demonstrated how to effectively deliver secure, scalable, and low-latency content to users worldwide.
