# aws-static-website-picture-enhancer
A guide on how to set up secure static web hosting in AWS to host a picture enhancing application. 
This project covers:  S3 Buckets, Route 53, Permissions and access control, Lambda functions, CloudFront

------------------------------------------------------------------------------------------------------------
Step 1: Create an AWS S3 bucket 
- Name: lowercase, must be unique [global resource]
- Disable "Block Public Access" setting -> allows website to be publicly accessible
- Enable "Bucket Versioning" -> allows rollback if files get overwritten

Step 2: Enable "Static Website Hosting" under properties section for the bucket -> allows website files to be served over HTTP
- Index Document: 'index.html'
- (Optional) Error Document: 'error.html' -> good practice

Step 3: Configure Bucket Policy -> to allow users to interact with the website 
- Navigate to Permissions
- Under Bucket Policy paste the provided bucket policy -> ensures everyone can read the website files, but not write anything
<img width="743" height="597" alt="image" src="https://github.com/user-attachments/assets/06d94719-7673-4e8b-b794-1e135fe02e5e" />

Step 4: Create Uploads Bucket for User Images
- This bucket remains private; only Lambda will have read/write access. It will store user-uploaded images separately and securely
- Keep the first bucket (website bucket) public-facing to handle user traffic
- Enable bucket versioning for rollback and recovery
<img width="371" height="201" alt="image" src="https://github.com/user-attachments/assets/add66869-8869-43e6-8b82-d55e0e5720b2" />

Step 5: Create a fully functional website and link it to the static website hosting bucket 
- Upload files from the following repository into the bucket or use your own personal code 
- Verify that the website is live by visiting the S3 endpoint URL
  <img width="766" height="346" alt="image" src="https://github.com/user-attachments/assets/8ebc9b6c-62c3-4fc9-9145-0befb71762da" />

 
