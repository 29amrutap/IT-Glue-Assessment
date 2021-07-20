# IT-Glue-Assessment

This repo has basic ansible code to update windows VM. It contains the ansible playbook called windows_update.yml with ansible module to install windows updates and reboot the vm in the update process whenever required. The hosts file represents the inventory file that has the windows inventory defined in it along with the group_vars specific to windows servers. The Jenkinsfile has the steps to invoke the ansible playbook and install windows updates on target vm's mentioned in the inventory file. The jenkins job is parameterized with vm login credentials and vm login ip. 

Steps to run:

1. Before running the job, spin up a windows server on AWS or use existing one. As an extra step, a user called 'Ansible' along with the password is created in the server to connect and run the playbook. This is not mandatory, you can use the admin user and password. Grab the ip address of the server, user and password you want to use to connect and run the playbook. 
2. Create a pipeline job in jenkins and configure it with this github url and the branch to refer the source files from. In the pipeline section select the option to fetch the pipeline script from SCM and provide the script path as 'Jenkinsfile'. 


<img width="1136" alt="Screen Shot 2021-07-20 at 12 21 47 AM" src="https://user-images.githubusercontent.com/38916016/126282393-ea69a73a-7874-4d0d-a225-f7358f7a5479.png">


3. The jenkins job is parameterized. To run the job, click 'build with parameters' and enter the inputs like ip of the server that needs to be updated along with the user and password to connect and run the playbook. Before running, make sure that the windows ip is updated in the 'hosts' file in the github under the windows inventory


<img width="927" alt="Screen Shot 2021-07-20 at 12 16 49 AM" src="https://user-images.githubusercontent.com/38916016/126283182-1e67a4f4-436e-4c83-a23f-d8cf155fa719.png">


4. The job invokes the ansible playbook to install the windows updates on the server you provided. Below is the sample input.

<img width="1138" alt="Screen Shot 2021-07-20 at 12 19 25 AM" src="https://user-images.githubusercontent.com/38916016/126283876-06aea8a8-cc6a-4daf-86ff-023af120fa76.png">


Note: Since this is a public repo, the SCM credentials are not configured in the job.

Improvements Needed: This is a simple playbook to install the windows updates. For advanced configuration, this can be written as ansible role with proper variables. Also, we can make use of proper block and rescue sections to debug and catch the exceptions during the installation. 
