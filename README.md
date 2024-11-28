# Serverless-EC2-Instance-Scheduler

## Scenario :
Some companies don’t require their EC2 instances to run continuously and need them only during working hours, such as 8:00 AM to 5:00 PM. To address this, I’ve created a serverless solution that automates the starting and stopping of EC2 instances. The process is handled by two Lambda functions—one starts the instances in the morning, and the other stops them in the evening. These functions are scheduled to run automatically using CloudWatch Events, ensuring efficiency and reducing unnecessary costs without manual intervention. This solution is fully serverless.


![img0](https://github.com/user-attachments/assets/7255f12f-3774-4bf2-bec0-a2b7d0e41b5e)

## Steps :

### Step 1 :
### Creating the Instance :
1. Navigate to the EC2 Console.
2. Follow the Outlined steps below.

![img1](https://github.com/user-attachments/assets/0c5af324-6dc1-4a55-a92f-09134ffcc29f)

![img2](https://github.com/user-attachments/assets/bc1ff576-ab56-4a36-9234-646755a487c1)

![img3](https://github.com/user-attachments/assets/22122bce-31e6-40a7-9e26-df92ec0308ae)

![img4](https://github.com/user-attachments/assets/2cdbcfcc-ab00-4d1f-a9b0-8231b84de3c7)




### Step 2 :
### Creating the Policy :


1. Navigate to the IAM Console.
2. Click on "Policies" and then Click on "Create policy"

![img5](https://github.com/user-attachments/assets/63b2f05f-8fbc-462e-9bc7-ff4753b04e1e)

![img6](https://github.com/user-attachments/assets/918b41b7-7154-41c6-a551-677ea1e9c707)


3. Select services as EC2.
4. And Actions are DescribeInstances , StartInstances.


![img7](https://github.com/user-attachments/assets/478a5780-eb9d-4699-8a40-fe9552e386a0)

![img8](https://github.com/user-attachments/assets/6edd77fa-ac84-4f65-a80e-6461402c00ff)

![img9](https://github.com/user-attachments/assets/16907576-f4ea-4c27-b56c-60518db4896f)

![img11 2](https://github.com/user-attachments/assets/e749c107-58ec-450c-a8de-803153ba30c4)


5. After creating the policy for starting instances, we also need to create a policy for stopping the instances. This is because we will create two Lambda functions: one for starting and one for stopping the instances. Each Lambda function will have its own role, and we will attach the corresponding policies to their roles.

6. Now, let's repeat the same steps to create the stopping policy.

7. The process is similar, but the actions will be different since this policy will handle stopping instances.

8. For the stopping policy, the actions should be DescribeInstances and StopInstances.

9. Name your policy "stop-ec2-instance" for clarity.


## Step 3 :
## Creating the Lambda functions :

1. Navigate to the lambda Console.
2. Follow the Outlined steps below.


![img11 3](https://github.com/user-attachments/assets/fc1bf614-9e57-4463-b8dc-3f7014083bbe)

![img11 4](https://github.com/user-attachments/assets/a9242247-21f7-463c-98a9-dc6363d5f929)

![img11](https://github.com/user-attachments/assets/ce295d88-7a31-456d-9c9b-418d3443d296)

![img12](https://github.com/user-attachments/assets/d2177d28-9dae-41e0-8b2a-ddc0856e3864)

![img13](https://github.com/user-attachments/assets/288f62db-7fbf-4614-9246-7cb9e27012a2)

Now, test the code and then create event
![img14](https://github.com/user-attachments/assets/7966ab44-4136-4eda-924c-06a99aa1313e)

![img15](https://github.com/user-attachments/assets/b502ffd4-4b92-4e8b-9fd5-d51620ef3383)

![img16](https://github.com/user-attachments/assets/40634ced-9622-453b-895b-d9975c7f00e7)

![img17 1](https://github.com/user-attachments/assets/2da03db4-049f-4533-a6fc-82779635e296)
3. Now again , go to the Lambda console and then test the code.

![img17](https://github.com/user-attachments/assets/5cecb075-8dd2-4d4d-b6e4-7549a0e60de1)
                As, now you can see our instance is ready in running state, if we want to test our function, we can stop instance and come again it will start our instance

4. We have now created a Lambda function for starting the instance.

5. To create a Lambda function for stopping the instance, repeat the same steps. Name this Lambda function "Stop-EC2-demo."

6. The only changes required are:

   - Replace the default code with the stop-ec2-instance.py code.
   - Attach the policy we created for stopping instances to the role of this Lambda function.

![img18](https://github.com/user-attachments/assets/5dc786e8-83d2-4bb4-beca-909b59fc8b0e)
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



