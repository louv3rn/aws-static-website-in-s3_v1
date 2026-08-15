# Hosting a Static Website in Amazon S3  

Learn how to host and deploy a static website using Amazon S3.  

---

## Overview  
Exploring how to create an S3 bucket, configure access settings, upload static files (HTML, CSS, JS), and enable static website hosting. I also practiced using ACLs, bucket policies, and versioning to understand how permissions and updates work in S3.

---

## Steps I Followed  

### Bucket Creation  
![Bucket Creation](./assets/create_bucket.png)

I started by creating an S3 bucket named `aws-hostweb-project`. Bucket names must be unique across all AWS accounts, so no two buckets can have the same name. I chose the region `us-east-1` because picking the closest region helps reduce delay (latency) and cost.

![Bucket Name](./assets/bucket_name.png)

### Object Ownership  
I enabled **ACLs** (Access Control Lists) to see how permissions work, even though AWS recommends turning them off. ACLs are rules that decide who can access files inside the bucket.
![Enable ACL](./assets/enable_acl.png)

Under Object Ownership, I kept the default setting “Bucket owner preferred” which means the bucket owner is the one who owns uploaded files.  

![Object owner](./assets/object_ownership.png)

### Disabling the “Block All Public Access”  
Next, I turned off the “Block all public access” option so the website could be viewed by anyone. This setting normally protects the bucket from unwanted access, but for hosting a public site, it needs to be disabled. 

![Enable Public Access](./assets/disbale_block_all_public_access.png)

I also enabled bucket versioning to keep track of file changes and left the default encryption on so files are protected. 
![Bucket Versioning](./assets/bucket_versioning.png)

AWS automatically encrypts the objects inside the bucket so whenever someone tries an unauthorize access, they cannot actually view the objects.
![Default Encryption](./assets/default_encryption.png)

After these settings, the bucket was created successfully and can be seen on the Buckets list.
![Success Bucket Creation](./assets/created_bucket_success.png)
![Bucket List](./assets/buckets_list.png)
### Uploading Files / Folders  
Once the bucket was ready, I uploaded my website files: `portfolio_website.html` and the assets folder containing CSS, JS, and images. The HTML file gives the structure of the site, while the assets add style and interactivity. After uploading, I made the files public using ACLs to avoid 403 Forbidden errors.  

To make the website available online, I enabled **static website hosting** in the bucket’s properties. I set `portfolio_website.html` as the index document, saved the changes, and confirmed that the site was accessible through the bucket’s endpoint URL.  

---

## 🔧 Additional Activities  
While testing, I noticed the “My Projects” section was missing. I found that the JavaScript file path was wrong, so I updated the HTML to:  

```html
<script src="./assets/portfolio_js.js"></script>
