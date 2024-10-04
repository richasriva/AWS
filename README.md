# AWS

Set up an AWS S3 Bucket:

Go to the AWS Management Console and create an S3 bucket where files will be uploaded.
Ensure the bucket has appropriate permissions to allow uploads.

Python Script to Upload Files:

Install the Boto3 library using pip install boto3.
Create a Python script that connects to your S3 bucket and uploads files.
python
Copy code
import boto3
from botocore.exceptions import NoCredentialsError

def upload_to_aws(local_file, bucket, s3_file):
    s3 = boto3.client('s3')
    try:
        s3.upload_file(local_file, bucket, s3_file)
        print(f"Upload Successful: {s3_file}")
        return True
    except FileNotFoundError:
        print("The file was not found")
        return False
    except NoCredentialsError:
        print("Credentials not available")
        return False

if __name__ == "__main__":
    local_file = 'test.txt' 
    bucket = 'your-bucket-name'  
    s3_file = 'uploaded_test.txt' 
    
    uploaded = upload_to_aws(local_file, bucket, s3_file)
Add AWS Credentials:

Set up your AWS credentials by configuring ~/.aws/credentials or directly in the environment using aws configure in your terminal.
Testing:

Run the Python script and ensure it uploads the file to the S3 bucket.
