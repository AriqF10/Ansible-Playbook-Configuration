Ansible Security Hardening Playbooks
This repository provides a collection of Ansible playbooks designed to enhance the security posture of Linux servers by automating the implementation of security best practices.
📖 Table of Contents
* Prerequisites
* 🚀 Getting Started
   * Installation
   * Inventory Setup
* ▶️ Usage
   * Running a Playbook
   * Available Playbooks
* 🛡️ Auditing with CIS-CAT
   * Downloading CIS-CAT
   * Running a Scan
* 🤝 Contributing
* 📄 License
✅ Prerequisites
Before you begin, ensure you have the following:
* Ansible: Installed on your control machine.
* SSH Access: Key-based SSH access to the target servers.
* Permissions: sudo or root privileges on the target servers.
🚀 Getting Started
Installation
First, install Ansible on your control machine. The installation method varies depending on your operating system.
Ubuntu/Debian:
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install -y ansible

CentOS/RHEL:
sudo yum install -y epel-release
sudo yum install -y ansible

For other operating systems or more detailed instructions, please refer to the official Ansible installation guide.
Inventory Setup
The inventory file (inventory.ini) is where you define the hosts that Ansible will manage. Create or modify the inventory.ini file to match your environment.
Example inventory.ini:
[prod_servers]
# Format: <alias> ansible_host=<ip_address> ansible_user=<ssh_user> ansible_private_key_file=<path_to_ssh_key>
server1 ansible_host=192.168.1.10 ansible_user=admin ansible_private_key_file=~/.ssh/prod_key

[my_machine]
localhost ansible_connection=local ansible_become=true

* [prod_servers]: A group of remote servers.
* [my_machine]: The local machine where Ansible is running.
* Replace the placeholder values with your actual server details.
▶️ Usage
Running a Playbook
To execute a playbook, use the ansible-playbook command from the root of this repository.
Command Syntax:
ansible-playbook -i <inventory_file> <playbook_file>

Example:
To apply the SSH hardening playbook to the servers defined in your inventory.ini:
ansible-playbook -i inventory.ini 01_ssh_hardening.yml

Available Playbooks
Here is a list of the playbooks included in this repository:
* 01_ssh_hardening.yml: Applies fundamental security hardening to the SSH service.
* file_system.yml: Implements security measures for the filesystem.
* firewall_hardening.yml: Configures and hardens the UFW (Uncomplicated Firewall).
* network_parameter.yml: Hardens kernel network parameters.
* service_hardening.yml: Disables and removes insecure services.
* ssh.yml: Contains additional, more specific SSH hardening configurations.
🛡️ Auditing with CIS-CAT
To verify the effectiveness of these playbooks and assess your system's compliance with security benchmarks, you can use the CIS-CAT (Configuration Assessment Tool).
Downloading CIS-CAT
1. Navigate to the CIS-CAT Lite download page.
2. Complete the registration form to get access to the download link.
3. Download the tool for your specific operating system.
Running a Scan
1. Extract the downloaded archive.
2. Change into the extracted directory.
3. Execute the appropriate script to start a scan.
Example for Linux:
This command runs an assessment against the CIS Benchmark for Ubuntu 20.04 and saves the report in the reports directory.
# The benchmark file name may vary based on the version you download.
./CIS-CAT.sh -b benchmarks/CIS_Ubuntu_Linux_20.04_LTS_Benchmark_v1.1.0-xccdf.xml -r ./reports -a

For detailed instructions, consult the documentation provided with the CIS-CAT tool. You can also watch this video for a demonstration: CAT Application Usage Instructions.
🤝 Contributing
Contributions are welcome! If you have suggestions for improvements or new features, please open an issue or submit a pull request.
📄 License
This project is open-source and available under the MIT License.