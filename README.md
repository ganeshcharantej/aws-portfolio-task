# portfolio-task
# AWS Serverless Portfolio Hosting 

An enterprise-grade, highly scalable, and secure serverless architecture built on Amazon Web Services (AWS) to host a professional responsive portfolio website. This deployment fully leverages AWS edge infrastructure to ensure global low-latency content delivery and enforced traffic encryption.

## 🚀 Live Production URL
* **Secure Hosted Endpoint:** [https://d1ytox1b6eg4qz.cloudfront.net](https://d1ytox1b6eg4qz.cloudfront.net)

## 🏗️ Cloud Architecture Overview
The application architecture is entirely serverless, ensuring high availability, zero server management overhead, and cost-optimized asset delivery:

1. **Amazon S3 (Origin Storage):** Configured as a static web asset hosting repository with isolated public-read access controls.
2. **Amazon CloudFront (CDN):** Serves as the global edge caching layer, provisioning SSL/TLS encryption certificates, and acting as the public proxy.## 🛠️ Infrastructure & Tech Stack
* **Cloud Services:** Amazon S3, Amazon CloudFront (CDN), AWS IAM (Bucket Policies)
* **Frontend Web Technologies:** HTML5, CSS3, FontAwesome Icons, Google Fonts Workspace
* **DevOps & Source Control:** Git, GitHub Version Control Pipeline

## 📝 Comprehensive Deployment Steps

### Phase 1: Object Storage Setup (Amazon S3)
* **Bucket Provisioning:** Created a globally unique, lowercase S3 bucket specifically designated for asset ingestion.
* **Access Control Unblocking:** Disabled standard AWS *Block All Public Access* parameters to clear pathing for custom downstream web accessibility.
* **Static Web Hosting Layer:** Activated the native S3 Static Website Hosting capability, defining `index.html` as the standard index document object root.

### Phase 2: Asset Level Permissions (IAM Bucket Policy)
Constructed an explicit JSON Identity and Access Management (IAM) bucket policy to safely permit public read operations (`s3:GetObject`) exclusively across the bucket's object namespace.

json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
        ]
        }
}

###    Phase 3: Global Content Delivery Network Provisioning (Amazon CloudFront)
Origin Boundary Selection: Bound the S3 static website web domain endpoint as the primary origin for the delivery network.

Transport Encryption Enforcement: Configured the Viewer Protocol Policy to enforce Redirect HTTP to HTTPS, applying managed TLS handshake protection.

WAF Layer Management: Maintained cost efficiency by disabling heavy Web Application Firewall configurations for an optimized student developer tier.

Default Root Mapping: Set the delivery pipeline's default root object directly to index.html to allow direct-to-domain asset routing.

### Phase 4: Lifecycle Edge Invalidation
Applied programmatic edge invalidation targets (/*) to force-purge stale caches across global points of presence (PoPs), seamlessly pushing updated viewport elements and graphic files instantly to web traffic.
    ]
}
}
