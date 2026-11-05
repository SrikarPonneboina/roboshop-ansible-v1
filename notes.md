
# To check the variables that we defined in the project folder 
`ansible localhost -m ansible.builtin.debug -a "var=mongodb_host"`

# Ansible Quick Notes & Reference

- create Ansible control node using awscli or manually
- install ansible package == `sudo dnf install ansible -y`
- Aws configure == configure with AWS Access KeyID; AWS Secret Access Key; region
- install botcore and boto3 == `pip3.9 install botocore boto3`
- run playbook in background with absolute path and combined stdout/stderr:
  `nohup ansible-playbook 05-catalogue.yaml &> /home/ec2-user/roboshop-logs/catalogue.log &`
- run playbook in background with relative path and explicit error redirection:
  `nohup ansible-playbook mongodb.yaml > ansible.log 2>&1 &`
- both commands capture standard output and standard error (both behave the same way in capturing outputs and errors)
- check if process is running using: `ps aux | grep ansible-playbook`
- check with PID: `ps -ef | grep <PID>` (e.g. `ps -ef | grep 2435`) — note: `ps aux` and `ps -ef` both display process information
- view live output using: `tail -f /home/ec2-user/roboshop-logs/catalogue.log`

- log path under defaults in ansible cfg should be with log_path not logs_path if you give logs path it will load logs to default directory

# Step 1: Verify SSH Connectivity and Port Status
- Run a network test using nc (netcat) or telnet from your control node:
- `nc -zv <managed_node_ip> 22`
- Verification: If successful, you will see a message like Connection to <ip> 22 port [tcp/ssh] succeeded!. If it says "Connection refused", the SSH service on the remote node is down or blocked.



