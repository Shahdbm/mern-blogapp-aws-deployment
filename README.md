# Week-10 Assignment – Deploying a MERN Stack App on AWS

This project demonstrates the deployment of a full-stack MERN application using several AWS services. The frontend is hosted on **S3**, the backend runs on **EC2** with **PM2**, and images are stored on a separate **S3 bucket**. IAM roles and secure environment configurations were applied for best practices.

---

## Technologies Used

- **Frontend:** React, Vite
- **Backend:** Node.js, Express
- **Database:** MongoDB Atlas
- **Infrastructure:** AWS (EC2, S3, IAM, PM2)

---

## Deployment Steps

### 1. Frontend – S3 Static Website Hosting

Steps Taken:
- Cloned the repo and configured environment variables.
- Installed dependencies using `pnpm`.
- Built the frontend with `pnpm run build`.
- Created an S3 bucket (`shahad-blogapp-frontend`) with static hosting enabled.
- Uploaded the `dist/` folder to the S3 bucket.
- Adjusted bucket permissions for public access.
- Verified frontend functionality via S3 URL.

---

### 2. Backend – EC2 Deployment with PM2

Steps Taken:
- Launched a new Ubuntu EC2 instance.
- Opened port **5000** in the security group.
- Installed Node, NPM, PM2, and cloned the backend repo.
- Created `.env` file with necessary variables:
  ```env
  PORT=5000
  AWS_ACCESS_KEY_ID=********
  AWS_SECRET_ACCESS_KEY=********
  AWS_REGION=eu-north-1
  S3_BUCKET_NAME=shahad-blogapp-media
  ```
- Installed dependencies via `npm install`.
- Started the backend with `pm2 start index.js`.
- Saved PM2 config for persistence across reboots.


---


### 3. S3 Media Bucket – Image Hosting

Steps Taken:
- Created a second bucket: `shahad-blogapp-media`.
- Updated CORS policy to allow file upload and retrieval:
  ```json
  [
    {
      "AllowedHeaders": ["*"],
      "AllowedMethods": ["GET", "PUT", "POST", "DELETE"],
      "AllowedOrigins": ["*"],
      "ExposeHeaders": []
    }
  ]
  ```
- Configured IAM user with S3 permissions (`s3:ListBucket`, `s3:PutObject`, etc.).
- Integrated the bucket with backend via `.env`.
- Successfully tested file upload and retrieval through the app.

---

### 4. Final Test – Post with Image

- Used the deployed frontend to add a new blog post with an image.
- Image successfully uploaded to the media S3 bucket.
- Image rendered correctly in the new post.

---


## Reflections & Lessons Learned

- Gained hands-on experience deploying full-stack apps on AWS.
- Learned how to configure IAM users and policies for secure S3 access.
- Practiced using EC2 for backend deployment with environment isolation.
- Understood how to troubleshoot deployment errors and logs using PM2.
This experience strengthened my cloud deployment skills and helped me understand real-world infrastructure configuration.
---

## Security Considerations

- IAM user credentials have been removed after deployment.
-IAM user was deleted after submission.
- The `.env` file is excluded from source control to prevent exposure.
- Buckets were reviewed for public access, and access was restricted post-testing.

---

## Screenshots

All required screenshots are included and clearly labeled.

---

## Author
Shahad
Clarusway - DevOps & Infrastructure Engineer Track
