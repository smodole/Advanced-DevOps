**<u>PROJECT ONE</u>**

**<u>CONFIGURE ANSIBLE ON MASTER SERVER TO INSTALL NGINX ON A TARGET WEB
SERVER (SERVER1) AND APACHE ON DATABASE SERVER (SERVER2)</u>**

**Organization Context:**

1.  **Company Name:** EliteCorperations

2.  **Scenario:** EliteCorperations is a mid-sized tech company that
    needs to automate the deployment and management of its web servers
    and database servers, You were consulted by EliteCoperations to
    manage their web and database server configurations and
    installations

**Project Tasks:**

1.  **Install Nginx Server on Eilte’s corperations Web servers:**

- Use Ansible to automate the setup of web servers with Apache/Nginx.

- On the web servers install APACHE server

- On both servers get their total free disk space (hint: use-\> df)

- On both servers get their available disk space (hint use -\> free)

- Ensure the playbooks install necessary packages,

2.  **Install Apache server on Elite’s Corporations Database server**

- On the Database servers install Nginx servers

- Install the Nginx server by writing a playbook

- On both servers get their total free disk space (hint: use-\> df)

- On both server get their available disk space (hint use -\> free)

**Deliverables:**

- Ansible playbooks and roles for the above tasks.

- Documentation explaining the setup and usage of the playbooks.

- Documentation on the differences between ansible playbook and
  adhoc-commands

**Links to Ansible Documentation:**

- <https://docs.ansible.com/ansible/latest/getting_started/get_started_playbook.html>

- <https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html#playbook-execution>

This exercise is to help create a practical project that animate
real-world DevOps problems. If you have questions, feel free to ask,
answers will be provided in the slack channel.

**<u>SOLUTION</u>**

**ANSIBLE MACHINE (AnsibleTest):**

**Instance<span class="mark">:</span>**
<span class="mark">i-0be0e053fa8b4c1b3</span>

**Public IP Address:** <span class="mark">34.229.16.103</span>

**Private IP Address:** <span class="mark">172.31.24.93</span>

**Connect:** ssh -i "<span class="mark">Downloads/AnsibleKey.pem</span>"
ubuntu@ec2-34-229-16-103.compute-1.amazonaws.com

**Public Key:** id_ed25519.pub (/home/ubuntu/.ssh)

**SERVER1 (WEB SERVER):**

**Instance:** <span class="mark">i-0bc4f98c05e820b9a</span>

**Public IP Address:** <span class="mark">3.86.45.122</span>

**Private IP Address:** <span class="mark">172.31.94.227</span>

**Connect:** ssh -i "<span class="mark">Downloads/server1.pem</span>"
ubuntu@ec2-3-86-45-122.compute-1.amazonaws.com

**SERVER2 (DATABASE SERVER):**

**Instance:** <span class="mark">i-0ef7b46d50f8853dd</span>

**Public IP Address:** <span class="mark">34.238.41.148</span>

**Private IP Address:** <span class="mark">172.31.95.234</span>

**Connect:** ssh -i "<span class="mark">Downloads/server2.pem</span>"
ubuntu@ec2-34-238-41-148.compute-1.amazonaws.com

Log into the Ansible controlled machine and run the “**sudo apt
update”** command

<img src="./media/image1.jpeg"
style="width:3.83333in;height:3.28165in" />

Install Ansible using the following command “**sudo apt install
ansible**”

<img src="./media/image2.jpeg"
style="width:6.26806in;height:0.75139in" />

Create public and private keys using the command “**ssh-keygen**”

<img src="./media/image3.jpeg" style="width:6.26806in;height:1.46667in"
alt="A screenshot of a computer AI-generated content may be incorrect." />

Create a bash file called **setup_ssh.sh** to copy the public key from
ansible controlled server to our target web and database servers.

<img src="./media/image4.jpeg" style="width:6.26806in;height:1.08958in"
alt="A screenshot of a computer AI-generated content may be incorrect." />

Now, run the setup_ssh.sh file to copy the public key to the other two
target servers

<img src="./media/image5.jpeg"
style="width:5.70886in;height:2.7254in" />

Create an inventory file

<img src="./media/image6.jpeg"
style="width:5.59494in;height:1.58377in" />

Enter the IP Addresses of the web and application server into the
inventory file as shown below

<img src="./media/image7.jpeg" style="width:5.59444in;height:1.02455in"
alt="A black screen with white text AI-generated content may be incorrect." />

Create a yml file

<img src="./media/image8.jpeg"
style="width:5.44304in;height:0.99682in" />

Place the following content into the created yml file

<img src="./media/image9.jpeg"
style="width:6.26806in;height:3.43542in" />

Run the following command: **ansible-playbook -i inventory
install_services.yml**

<img src="./media/image10.jpeg" style="width:5.49728in;height:3.69815in"
alt="A screenshot of a computer AI-generated content may be incorrect." />

To check if ngix has been truly installed on server1, use the following
command: **sudo systemctl status nginx**

<img src="./media/image11.jpeg"
style="width:5.19444in;height:4.08143in" />

To check if Apache has been truly installed on server2, use the
following command: **sudo systemctl status apache2**

<img src="./media/image12.jpeg" style="width:5.00926in;height:3.93593in"
alt="A screenshot of a computer AI-generated content may be incorrect." />

Using the following command, df -k, obtain the available and free disk
space.

<img src="./media/image13.jpeg"
style="width:5.2963in;height:4.12508in" />

<img src="./media/image14.jpeg"
style="width:6.26806in;height:5.08264in" />
