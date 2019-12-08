# terraform-aws-cloudfront-s3-website-lambda-edge
Terraform 0.12.x compatible module for creating a s3 static website with cloudfront distribution, and Lambda@Edge function

The following resources will be created
  
  - S3 Bucket
  - Cloudfront distribution
  - Route53 record
  - Lambda@Edge nodejs10.x function to redirect fqdn.com/folder/index.html request to fqdn.com/folder

  
Prerequisites:

  - Route 53 hosted zone for example.com
  - ACM certificate for *.example.com in us-east-1 region
  
### Example 1

    provider "aws" {
      region = "us-east-1"
    }
     
    module "cloudfront_s3_website" {
        source           = "twstewart42/cloudfront-s3-website/aws"
        version          = "1.1.0"
        hosted_zone      = "example.com"
        domain_name      = "test.example.com"
        aws_region       = "us-east-1"
    }

### Variables    
| variable | Default | Description |
| -------- | ------- | ----------- |
| aws_region | us-east-1| AWS Region to host S3 site | 
| domain_name | None | FQDN of cloudfront alias for the website - blog.site.com|
| hosted_zone | None | Root domain of website - site.com |
| tags | None | Map of the tags for all resources |

### Credits
The original core module was developed by [chgangaraju/terraform-aws-cloudfront-s3-website](https://github.com/chgangaraju/terraform-aws-cloudfront-s3-website)
