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


3. Select services as EC2.
4. And Actions are DescribeInstances , StartInstances.


![img7](https://github.com/user-attachments/assets/6dc18561-0f35-4e93-9bce-206e1986b5d8)

![img8](https://github.com/user-attachments/assets/08c4b7ba-ed30-4349-8205-f9f641c10631)

![img9](https://github.com/user-attachments/assets/00b2b125-725a-4bcf-8661-123e3bf00a3a)

![img11 2](https://github.com/user-attachments/assets/1d9e7f1f-4c12-46da-99f6-2268c6a3ba80)


5. After creating the policy for starting instances, we also need to create a policy for stopping the instances. This is because we will create two Lambda functions: one for starting and one for stopping the instances. Each Lambda function will have its own role, and we will attach the corresponding policies to their roles.

6. Now, let's repeat the same steps to create the stopping policy.

7. The process is similar, but the actions will be different since this policy will handle stopping instances.

8. For the stopping policy, the actions should be DescribeInstances and StopInstances.

9. Name your policy "stop-ec2-instance" for clarity.


## Step 3 :
## Creating the Lambda functions :

1. Navigate to the lambda Console.
2. Follow the Outlined steps below.


![img11 3](https://github.com/user-attachments/assets/0e8f9afa-ad78-4afa-a76e-d6c70a3156dc)

![img11 4](https://github.com/user-attachments/assets/2abf31ab-9634-415e-b33d-6d209dd46cd9)

![img11](https://github.com/user-attachments/assets/e6b84d5e-04ac-4fe6-b669-9c657ff72bd9)

![img12](https://github.com/user-attachments/assets/e42959d8-addd-4114-9c96-bb1a8feb8841)

![img13](https://github.com/user-attachments/assets/00671daa-d28b-4445-b844-5bade4f9554c)

![img14](https://github.com/user-attachments/assets/13c22705-9b2d-4058-b60e-b6865182cf87)

![img15](https://github.com/user-attachments/assets/ebbcce40-10f3-4a66-bdee-dc019b69180b)

![img16](https://github.com/user-attachments/assets/aa57a851-5bcf-437b-802f-d16fa6ce8b41)

![img17 1](https://github.com/user-attachments/assets/1276a719-7147-4345-8c31-22e77dc8a54b)
3. Now again , go to the Lambda console and then test the code.

![img17](https://github.com/user-attachments/assets/743122a8-3fa2-4e29-8d08-0d9397d8bd80)
                As, now you can see our instance is ready in running state, if we want to test our function, we can stop instance and come again it will start our instance

4. We have now created a Lambda function for starting the instance.

5. To create a Lambda function for stopping the instance, repeat the same steps. Name this Lambda function "Stop-EC2-demo."

6. The only changes required are:

   - Replace the default code with the stop-ec2-instance.py code.
   - Attach the policy we created for stopping instances to the role of this Lambda function.

![img18](https://github.com/user-attachments/assets/8c142496-9dd1-47f2-b453-89f55cd32015)
            After completion all the steps mentioned above, we can test our code. It successfully starts and stop the instance, as we can see above. Therefore we can schedule these two functions.

            
7. As shown earlier, when I tested the Python code, it ran successfully and stopped the instance as expected.

8. Now, we are ready to proceed with creating schedules for these functions.

   
### Step 5 :
### Creating the Schedules Using Cloud Watch :

1. Navigate to the Cloud Watch Console.
2. Follow the Outlined Steps below.


![img19](https://github.com/user-attachments/assets/413bdb39-72c1-40ad-979f-cb5ef1fc7720)

![img20](https://github.com/user-attachments/assets/056eea14-d59b-4dae-a87b-41c93dd19e93)

![img21](https://github.com/user-attachments/assets/3ffe40bc-cb99-4826-a5b0-7e0b587da511)

![img22](https://github.com/user-attachments/assets/73fdb12d-604e-4f0b-81bc-a4ca78ece198)

![img23](https://github.com/user-attachments/assets/b7a1f0ad-f568-44fd-a5b8-b190bdc989a7)

![img24](https://github.com/user-attachments/assets/8f728bf4-e69b-4473-a472-874cc958e43d)

![img25](https://github.com/user-attachments/assets/bd7bd64d-1a66-47b6-bd49-4a7692b81b76)

![img26](https://github.com/user-attachments/assets/a2341f94-27ed-4ff1-94e4-7b557360a451)

![img27](https://github.com/user-attachments/assets/0cddecae-72e3-48dc-840a-04f43b24cfae)

![img28](https://github.com/user-attachments/assets/c3ac992b-cd20-412c-b3f1-a18ddb96c4b6)

3. We have now created a schedule to start the instance every day at 8:00 AM.

4. Next, we need to create a schedule for stopping the instances.

5. To create the stopping schedule, follow the same steps used for starting the instance schedule, with a few changes. Name the rule "stop-ec2-rule."

6. The changes include:

       - Modifying the scheduled time to 5:00 PM (17:00 IST).
       - Selecting the Lambda function designed for stopping the instance.
       - The schedule will trigger the Lambda function at 5:00 PM IST to stop the EC2 instance.

![img-1](https://github.com/user-attachments/assets/7e7dcbc0-38d6-4bfe-a5bd-ca676cfa9aa3)

7. We have to Change the Function as Stop-EC2-instance

8. Now, we have successfully created two schedules: one to start the instance every day at 8:00 AM and the other to stop the instance every day at 5:00 PM.

![img29](https://github.com/user-attachments/assets/fb1a98ac-2f1b-4619-8a17-3c422dbcfdfb)



