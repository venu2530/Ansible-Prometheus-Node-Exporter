# Ansible Playbook: Install Prometheus Node Exporter on Ubuntu VMs

This Ansible playbook automates the installation of Prometheus Node Exporter on multiple Ubuntu Virtual Machines. It allows specifying the version of Node Exporter to use and uses a username/password to connect to the virtual machines.

## Prerequisites

1. **Ansible Installed**: Make sure Ansible is installed on your local machine or the control node from where you'll run the playbook.

2. **Access to Ubuntu VMs**: Ensure you have SSH access to the Ubuntu virtual machines and have the necessary privileges to execute commands with `sudo`.

## Usage

1. **Clone Repository**: Clone or download this repository to your local machine.

2. **Modify Playbook Variables**:
   - Open the `playbook.yml` file and update the following variables:
     - `node_exporter_version`: Set the desired version of Node Exporter.
     - `username`: Specify your username for connecting to VMs.
     - `password`: Specify your password for connecting to VMs.

3. **Create Inventory File**:
   - Create an Ansible inventory file (e.g., `inventory.yml`) containing the IP addresses or hostnames of your Ubuntu VMs.

4. **Run Playbook**:
   - Execute the playbook using the following command:
     ```bash
     ansible-playbook -i inventory.yml playbook.yml --extra-vars "ansible_ssh_user=your_username ansible_ssh_pass=your_password"
     ```
     Replace `inventory.yml` with your inventory file, and `your_username` and `your_password` with your actual username and password for connecting to the VMs.

5. **Verify Installation**:
   - Once the playbook execution is complete, verify that Prometheus Node Exporter is installed and running on your Ubuntu VMs.

## Directory Structure

```
ansible-prometheus-node-exporter/
│
├── playbook.yml
├── node_exporter.service.j2
└── README.md
```

- `playbook.yml`: Ansible playbook script to install Node Exporter.
- `node_exporter.service.j2`: Jinja2 template for the systemd service file.
- `README.md`: This documentation file.

## Notes

- Ensure that SSH access is properly configured on your Ubuntu VMs and that you can connect using the provided username and password.
- It's recommended to review and test the playbook in a non-production environment before running it in a production environment.
- For security reasons, consider using SSH key-based authentication instead of password authentication for SSH connections.

---
