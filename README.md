# **Cloud Load Balancing and High Availability Documentation**

## **Project Overview**
This project implements a **high availability** and **load balancing** solution using **AWS EC2**, **Application Load Balancer (ALB)**, and **Ansible automation**. The solution ensures the availability of web applications by distributing traffic across multiple servers and providing backup using two web servers. In case one web server stops, the other one takes over the traffic distribution.

---

## **1. AWS Setup**

### **AWS EC2 Instances (Web Server 1 & Web Server 2)**
- **Description**: Two EC2 instances (Web Server 1 and Web Server 2) are launched in AWS. Web Server 1 acts as the primary server, and Web Server 2 serves as the backup.
- **Web Server Setup**:
  - Both servers are set up to serve the same application, ensuring no downtime in case one server fails.
  - Installed and configured **Apache** or **Nginx** on both servers.

#### **Steps to Launch EC2 Instances**:
1. Log into AWS Console.
2. Navigate to the EC2 dashboard.
3. Launch two EC2 instances (choose appropriate AMI, instance type, etc.).
4. Set up security groups to allow HTTP and SSH access.
5. Install and configure the required web application (Apache/Nginx).

### **Application Load Balancer (ALB) Setup**
- **Description**: The ALB is configured to distribute traffic across both Web Server 1 and Web Server 2 to ensure high availability. If one server fails, the other server continues to handle the traffic.
  
**Steps to Set Up ALB**:
1. Create an ALB in AWS.
2. Configure the ALB to distribute traffic between Web Server 1 and Web Server 2.
3. Set up health checks to ensure that only healthy instances receive traffic.
4. Test failover by stopping Web Server 1 and ensuring that traffic is redirected to Web Server 2.

---

## **2. Ansible Automation**

### **Automation Overview**
- A single Ansible playbook (`playbook.yml`) is used to automate the entire process, including:
  - The creation of EC2 instances.
  - Configuring the web servers.
  - Setting up the ALB.
  - Applying necessary security configurations.

The playbook automates the setup of **AWS EC2 instances**, **Application Load Balancer (ALB)**, and **web server configurations (Apache/Nginx)**. Additionally, it configures **security groups** and ensures that only healthy instances are receiving traffic through ALB.

---

## **3. Failover Testing**

- **Description**: To test high availability, one web server (Web Server 1) is stopped, and the traffic is routed to the other web server (Web Server 2) without any downtime.
  
**Steps**:
1. Stop Web Server 1.
2. Verify that traffic continues to flow to Web Server 2 via the ALB.
3. Ensure that the web application is still accessible and running from the remaining server.

---

## **4. Future Enhancements**

### **Cloudflare DNS Failover Integration**
- **Description**: In the future, Cloudflare DNS will be used to further enhance the high availability by providing a DNS failover solution. This will ensure that traffic is routed to healthy instances even if the AWS ALB fails.

- **Steps (Future Enhancement)**:
  1. Set up a Cloudflare DNS to point to the AWS ALB.
  2. Configure failover rules to switch traffic to healthy servers automatically.

---

## **Project Status**
- **Current Setup**:
  - The setup of **AWS EC2 instances**, **Application Load Balancer (ALB)**, and **web servers** has been completed and tested.
  - **Ansible playbooks** have been created to automate the setup.
  - The **failover testing** is successful, and traffic is being redirected from one server to another without downtime.
- **Future Enhancements**:
  - Integration of **Cloudflare DNS Failover** to further improve high availability.

---

## **Installation and Configuration**

### **Steps to Run the Project**:
1. **Clone the repository**:
   ```bash
   git clone https://github.com/Chimmuuu/cloud-load-balancing-project.git
   cd cloud-load-balancing-project
