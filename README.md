# Amazon S3 Life Cycle Management

Valtara Fintech company uses AWS S3 for storing transaction logs. They implement a lifecycle policy where logs are stored in S3 Standard for immediate access for 30 days, then transitioned to S3 Glacier for cost-effective, long-term archival. After some years, the logs are automatically deleted to comply with data retention policies and minimize storage costs.

# S3 LifeCyle

<img width="768" alt="Screenshot 2025-01-11 at 17 30 03" src="https://github.com/user-attachments/assets/5bdd97a2-2bc0-43d2-8100-2d44e17ad4d8" />

# Lifecyle Architecture

<img width="586" alt="Screenshot 2025-01-11 at 17 50 13" src="https://github.com/user-attachments/assets/1cabc20c-f9c3-419d-bf7c-5fc45faca5db" />




# Activity Guide: S3 Lifecycle Management

1. Introduction to S3 Lifecycle Management
What is Lifecycle Management?
A mechanism to automate transitions and expiration of objects in S3 buckets.
- Actions include:
Transition actions: Move objects to different storage classes (e.g., Glacier, Deep Archive) after a set number of days.
Expiration actions: Permanently delete objects after a specified period.
- Use Case:
Store transaction logs in S3 Standard for 30 days, transition them to Glacier for long-term storage, and delete them after two years to save costs and comply with data retention policies.

2. Prerequisites
- AWS Account: Ensure you have an active AWS account.
- S3 Bucket: Create an S3 bucket if not already available.

3. Add Sample Data to S3 Bucket
- Log in to the AWS Management Console and navigate to the S3 service.
- Select your bucket or create a new one.
- Click on Upload, add files (e.g., PNGs from the sample data), and complete the upload process.

4. Create a Lifecycle Rule
- Navigate to the Management tab in the S3 Console for the selected bucket.
- Click on Create Lifecycle Rule and provide a rule name (e.g., K21Rule).
- Define rule scope:
Apply the rule to all objects or specify a prefix.
- Configure lifecycle actions:
- Transition Actions:
Transition to Standard-IA after 30 days.
Transition to Glacier after 365 days.
Transition to Deep Archive after 700 days.
- Expiration Actions:
Expire objects after 2 years.
- Review and save the rule.

5. Verify Lifecycle Rule
Check the lifecycle configuration under the Management tab to confirm actions are set as defined.

6. Clean Up Resources
- Delete Lifecycle Rule:
Navigate to the bucket’s Management tab, select the lifecycle rule, and delete it.
- Delete Bucket:
Empty the Bucket: Suspend versioning, delete objects, and permanently remove all versions.
Delete the bucket from the S3 Console.

7. Troubleshooting
- Common Issues:
Lifecycle Rule Not Working: Ensure versioning is enabled and proper transitions are configured.
- Deletion Errors: Verify that all objects, including versions, are deleted before attempting to delete the bucket.

8. Summary
Successfully implemented S3 lifecycle management to automate object transitions and expiration.
Reduced manual intervention for managing storage classes and costs.
