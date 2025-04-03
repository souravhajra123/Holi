# Make changes here to trigger CI/CD Pipeline
14.03.2025
new commit made

# HAPPY HOLI
About: A web page to wish Happy Holi.
Services & Tools Used: AWS, EC2, GitHub, Ansible, Jenkins, Docker.
Workflow: Continuously fetch code from GitHub and deploy over EC2 server by
containerizing it using Docker on Jenkins platform.
Solution:
1. Create a GitHub repository containing the the code and necessary files.
2. Launch two EC2 instances(ubuntu, t2.micro), one will work as master and other
one as slave.
3. Connect the master machine and update it.
4. Install Ansible on master machine.
5. After Ansible got installed, now do password less ssh with slave machine.
# $ ssh-keygen -t rsa
# $ cd .ssh
# $ sudo cat id_rsa.pub
Copy the content of id_rsa.pub
6. Connect the slave machine and paste the content of id_rsa.pub in authorized_keys
inside .ssh directory and save the file.
# $ cd .ssh
# $ sudo nano authorized_keys
7. Now set up Ansible cluster.
First change the directory to /etc/ansible → $ cd /etc/ansible
Now edit “hosts” file and add our slave IP in “holi” group → $ sudo nano hosts
Now save the file.
# Now ping the hosts → $ ansible -m ping holi
8. Now go to root directory and create a directory to store your files related to
configuration management.
# Create playbook.yaml to configure master and slave both → $ nano playbook.yaml
# Create master.sh to install Java and Jenkins on master → $ nano master.sh
# Create holi.sh to install Java and Docker on slave → $ nano holi.sh
# Now run the ansible playbook → $ ansible-playbook playbook.yaml
9. Java and Jenkins got installed on master machine.
10. Java and Docker got installed on slave machine.
11. Set Jenkins Dashboard.
12. Add slave machine as Jenkins node.
13. Create a job on Jenkins Dashboard name as “HOLI” and add Github Repository in
Source Code Management and restrict the job in “Holi” node, then Build the job
manually.
14. After successful build of the job, the Github repository will be copied to
/home/ubuntu/jenkins/ in slave machine.
15. Create the the Dockerfile on GitHub repository to containerize the code.
16. Connect GitHub repository with Jenkins using GitHub Webhook to auto trigger
the Jenkins job.
17. Make a new commit to GitHub repository.
18. Jenkins job is automatically got triggered.
19. Dockerfile got copied to slave server after the new automatic build.
20. Reconfigure the Jenkins job and add Build Steps to build image using Dockerfile
and run container from the image on specified port.
21. Build the job manually.
22. After successful build browse the public IP address of the slave machine on 81
port(as per port mapping) to see the output.
23. Add a new photo and update and update the code accordingly and commit the
changes.
# 24. Seamless Continuous Integration and Continuous Deployment establibshed.
Without doing anything after updating the code the changes getting reflected
automatically.
# GitHub Repository: https://github.com/souravhajra123/Holi
