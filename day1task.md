Here is your question and answer formatted in GitHub Markdown (`README.md`) so you can copy it directly into your GitHub repository.

---

## **📘 Ansible Playbook for File Creation on App Servers**

### **Question**
The Nautilus DevOps team is testing various Ansible modules on servers in Stratos DC. They're currently focusing on file creation on remote hosts using Ansible. Here are the details:

**a.** Create an inventory file `~/playbook/inventory` on the jump host and include all app servers.  

**b.** Create a playbook `~/playbook/playbook.yml` to create a blank file `/opt/nfsdata.txt` on all app servers.  

**c.** Set the permissions of the `/opt/nfsdata.txt` file to `0755`.  

**d.** Ensure the user/group owner of the `/opt/nfsdata.txt` file is `tony` on app server 1, `steve` on app server 2, and `banner` on app server 3.  

📌 **Note:** Validation will execute the playbook using the command  
```sh
ansible-playbook -i inventory playbook.yml
```
Ensure the playbook functions correctly without any additional arguments.

---

### **Inventory File (`inventory`)**
Create the `inventory` file inside `~/playbook/` with the following content:

```ini
[app_servers]
stapp01 ansible_user=tony ansible_ssh_pass=Ir0nM@n
stapp02 ansible_user=steve ansible_ssh_pass=Am3ric@
stapp03 ansible_user=banner ansible_ssh_pass=BigGr33n
```

---

### **Playbook File (`playbook.yml`)**
Create the `playbook.yml` file inside `~/playbook/` with the following content:

```yaml
- hosts: all
  become: yes
  tasks:
    - name: Create empty file
      file:
        path: /opt/nfsdata.txt
        state: touch
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"
        mode: "0755"
```

---

### **Running the Playbook**
Run the playbook using:  

```sh
ansible-playbook -i inventory playbook.yml
```

---

Now you can copy and paste this content into a `README.md` file and push it to your GitHub repository. 🚀
