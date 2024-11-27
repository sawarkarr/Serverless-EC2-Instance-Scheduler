# Serverless-EC2-Instance-Scheduler

## Scenario :
Some companies don’t require their EC2 instances to run continuously and need them only during working hours, such as 8:00 AM to 5:00 PM. To address this, I’ve created a serverless solution that automates the starting and stopping of EC2 instances. The process is handled by two Lambda functions—one starts the instances in the morning, and the other stops them in the evening. These functions are scheduled to run automatically using CloudWatch Events, ensuring efficiency and reducing unnecessary costs without manual intervention. This solution is fully serverless.


![img0](https://github.com/user-attachments/assets/eedd289b-2061-44b2-a4e6-1a1c5f29ba4c)

## Steps :

### Step 1 :
### Creating the Instance :
1. Navigate to the EC2 Console.
2. Follow the Outlined steps below.

![img1](https://github.com/user-attachments/assets/749c7c75-06b2-4e21-8258-eab91fdb413c)

![img2](https://github.com/user-attachments/assets/c51a4005-f0a1-4cf6-930c-d9a0656c4a7a)

![img3](https://github.com/user-attachments/assets/47dd0531-11db-4ff1-978b-a009df6b79bd)

![img4](https://github.com/user-attachments/assets/28e7e84a-d1b2-4956-a2ac-5d0fef08f069)


### Step 2 :
### Creating the Policy :


1. Navigate to the IAM Console.
2. Click on "Policies" and then Click on "Create policy"

![img5](https://github.com/user-attachments/assets/b685daa1-8829-4a34-a24b-12c4d182422c)

![img6](https://github.com/user-attachments/assets/af576492-4dd2-45ed-8f82-8306a3a72aec)

![img7](https://github.com/user-attachments/assets/6dc18561-0f35-4e93-9bce-206e1986b5d8)

![img8](https://github.com/user-attachments/assets/08c4b7ba-ed30-4349-8205-f9f641c10631)

![img9](https://github.com/user-attachments/assets/00b2b125-725a-4bcf-8661-123e3bf00a3a)

![img11 2](https://github.com/user-attachments/assets/1d9e7f1f-4c12-46da-99f6-2268c6a3ba80)


