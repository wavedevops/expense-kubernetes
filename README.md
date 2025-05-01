# expense-kubernetes

- ✅ How to Automatically Load `inputs.tfvars` in Terraform

* - If you don't want to run `terraform apply -var-file="inputs.tfvars` every time

- ✅ Terraform will automatically load `terraform.tfvars` when you run:
* - ```terraform apply```

- - - 
terraform.tfstate
terraform.tfvars
main.tf
state.tf
vars.tf

terraform init 
terraform apply 


terraform init -backend-config=env-dev/terraform.tfstate
terraform apply -var-file=env-dev/terraform.tfvars

```yml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUREekNDQWZlZ0F3SUJBZ0lVVlBHQmYvR2ZaQkZrTllJMU15aGRRK0JISmxnd0RRWUpLb1pJaHZjTkFRRUwKQlFBd0Z6RVZNQk1HQTFVRUF3d01NVEF1TVRVeUxqRTRNeTR4TUI0WERUSTBNVEV3TWpFNE1qUTFOVm9YRFRNMApNVEF6TVRFNE1qUTFOVm93RnpFVk1CTUdBMVVFQXd3TU1UQXVNVFV5TGpFNE15NHhNSUlCSWpBTkJna3Foa2lHCjl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUE3RGxraFBzSk9XQzZaZ2hpV0x2YlRsZkdMcHNyUllaZUVIWjMKMk4wb25oeTRKSU9xMytCTjFhREg3N1VaTjJnL2tibklHNndxdkgvTHhZYm9HbWhxSUltb2JHZ3NnTURqaUxkVwp3bU5pZ1VidUgyQnR0ek55YTdBV0pDZEx5cU9oeWt0NE1KV1Zrc1dNNEFtUzBBWUhOZVpnaURnUHVCa1VUeGl1CmVrb2dMUGplOU5ySEx6Uk9XTDVlQ0pKVVhoRGsrQk5nMlZiY0dWS3dkQjkvM1hCWG5kMVVTL09CTjZpNjkxekUKS3EvWFZCdFMwYk1aYzdlVmFGOU5hdWZnUVdKZ3lhdmFpaU1tdEU4aUtDSEtGMzh2allZQWgvQXBTL0FWaVkxLwpmMDYvWmZ1YVpYN3BHRlRSM1IySUVFR21GVnhqZGJBWXlpTVB2ZUJjSjgzYUh5NUdrd0lEQVFBQm8xTXdVVEFkCkJnTlZIUTRFRmdRVVFJVzBiNVhDckdtOW9NRkFxUXBLVzNpME45MHdId1lEVlIwakJCZ3dGb0FVUUlXMGI1WEMKckdtOW9NRkFxUXBLVzNpME45MHdEd1lEVlIwVEFRSC9CQVV3QXdFQi96QU5CZ2txaGtpRzl3MEJBUXNGQUFPQwpBUUVBNTJOZEtxdTF0VWQ4amVFbDdmOFBjclRNb0ZOcjdtaktIcnNnVTRtc29nYTFUcnc3bDJmbENyNHNXTFRFCjdGNHYxcUxPRzJPbzFMOUlYQmF4QzVBVVhaTXJRTEp4cENxV1ZRVjlGaERjN1ZIaS9ZUUdOTmRIakJIcjNIeTgKU2RTQldHZm01YjM5UXBMTVpOVnA5M2VFMjFjb21vbkU1SVl5QzVnTGJQNkM5RkRFcHhJMHRHa0NGSFp0cHBOVApBNFpxZnpBcW1yZkhmZm90UklBSlREN01qem80bUFGRDE2ekRaSkJxOWpuZjZxRHlCbWVHQ3oyL3RseWxyRkc3CnVTa21ZL0FIUFFuYlBRMlFTQWJEM1BLNzRnMm1SMEtDcm9ZdFI4RkwxSFBVOHFaTXIxUjN6QkxrZEFkbVdNbzkKOW9EU3JPekkraWJ3VnVFWGlwZE1idnVIU1E9PQotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tCg==
    server: https://main.durgasri.com:16443
  name: microk8s-cluster
contexts:
- context:
    cluster: microk8s-cluster
    namespace: prasad
    user: admin
  name: microk8s
current-context: microk8s
kind: Config
preferences: {}
users:
- name: admin
  user:
    token: eyJhbGciOiJSUzI1NiIsImtpZCI6ImZ1WnNibFl0VFZHZHhNcmxLcHRfZUpXYVR4R0JYSERQZUhUamc0TGhOdncifQ.eyJhdWQiOlsiaHR0cHM6Ly9rdWJlcm5ldGVzLmRlZmF1bHQuc3ZjIl0sImV4cCI6MTc0NTIxMDc1MywiaWF0IjoxNzQ1MjA3MTUzLCJpc3MiOiJodHRwczovL2t1YmVybmV0ZXMuZGVmYXVsdC5zdmMiLCJqdGkiOiJkN2JhNGRhZi01OTE0LTQ5OTYtYjc1ZC1hNGYwNmY4NTYwZjkiLCJrdWJlcm5ldGVzLmlvIjp7Im5hbWVzcGFjZSI6InByYXNhZCIsInNlcnZpY2VhY2NvdW50Ijp7Im5hbWUiOiJzYyIsInVpZCI6IjM4YjFhMDVlLTEzMTYtNDY3NC05Y2IyLTMxMGI3ZGQ2YjQyYiJ9fSwibmJmIjoxNzQ1MjA3MTUzLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6cHJhc2FkOnNjIn0.bE5tLkOMAY9dulaKhM6HkXZ7ZxQKhMU61G1ldFb0nSbeEFjy_2dNo1R2A1ChJA7GJzUuFhdRk1M57bvPMORiWY9HA1Xlt4oqK0ZC-8ALXt6Sk5W0KsHEq2DA7RrYoWEHvUitl9ZfSLAgnZzMvQgnn7MBuW3tPZGi-JgUW3qKeihluvYMKm1OI5agUSinTq6_jCvLPJF3PcP2NvCl_S4VLWDR4Q9xAkfrnRrx6raHK-4f-IWuc-iTF5lZPKi3E_8RkOvZD0DsU2H0kNMn-KHOIbsidWC8AknegzzUGc81UJtnHEmm5IxeiRGLQM-VP1ZtyuCIRVmo501VB0xjnvi4QQ

```

`
# Inventory
# Inventory

- **List of Servers**:
  - Include the IP addresses or hostnames of all your servers.

- **Group by Environment**:
  - Organize servers into groups such as `dev`, `staging`, or `prod`.

- **Group by Role**:
  - Categorize servers based on their roles, like `database` or `web server`.

- **Dynamic Inventory**:
  - Use scripts for dynamic environments where server configurations change frequently.
---



## Ansible


- Describe each of the following components in Ansible, including the relationship between them:

  * Task
  * Module
  * Play
  * Playbook
  * Role


Task – a call to a specific Ansible module
Module – the actual unit of code executed by Ansible on your own host or a remote host. Modules are indexed by category (database, file, network, …) and also referred to as task plugins.

Play – One or more tasks executed on a given host(s)

Playbook – One or more plays. Each play can be executed on the same or different hosts

Role – Ansible roles allows you to group resources based on certain functionality/service such that they can be easily reused. In a role, you have directories for variables, defaults, files, templates, handlers, tasks, and metadata. You can then use the role by simply specifying it in your playbook.



- How Ansible is different from other Automation tools?

Ansible is:

* Agentless
* Minimal run requirements (Python & SSH) and simple to use
* Default mode is "push" (it supports also pull)
* Focus on simpleness and ease-of-use



- True or False? Ansible follows the mutable infrastructure paradigm

True.



- True or False? Ansible uses declarative style to describe the expected end state
False. It uses a procedural style.



- What kind of automation you wouldn't do with Ansible and why?

While it's possible to provision resources with Ansible, some prefer to use tools that follow immutable infrastructure paradigm.
Ansible doesn't saves state by default. So a task that creates 5 instances for example, when executed again will create additional 5 instances (unless
additional check is implemented) while other tools will check if 5 instances exist. If only 4 exist, additional instance will be created.



- What is an inventory file and how do you define one?

An inventory file defines hosts and/or groups of hosts on which Ansible tasks executed upon.

An example of inventory file:

```
192.168.1.2
192.168.1.3
192.168.1.4

[web_servers]
190.40.2.20
190.40.2.21
190.40.2.22
```



- What is a dynamic inventory file? When you would use one?

A dynamic inventory file tracks hosts from one or more sources like cloud providers and CMDB systems.

You should use one when using external sources and especially when the hosts in your environment are being automatically<br>
spun up and shut down, without you tracking every change in these sources.



- How do you list all modules and how can you see details on a specific module?

1. Ansible online docs
2. `ansible-doc -l` for list of modules and `ansible [module_name]` for detailed information on a specific module



- Write a task to create the directory ‘/tmp/new_directory’

```
- name: Create a new directory
  file:
    path: "/tmp/new_directory"
    state: directory
```



- You want to run Ansible playbook only on specific minor version of your OS, how would you achieve that?



- What the "become" directive used for in Ansible?



- What are facts? How to see all the facts of a certain host?



- What would be the result of the following play?

```
---
- name: Print information about my host
  hosts: localhost
  gather_facts: 'no'
  tasks:
      - name: Print hostname
        debug:
            msg: "It's me, {{ ansible_hostname }}"
```

When given a written code, always inspect it thoroughly. If your answer is “this will fail” then you are right. We are using a fact (ansible_hostname), which is a gathered piece of information from the host we are running on. But in this case, we disabled facts gathering (gather_facts: no) so the variable would be undefined which will result in failure.



- What would be the result of running the following task? How to fix it?

```
- hosts: localhost
  tasks:
      - name: Install zlib
        package:
          name: zlib
          state: present
```




- Which Ansible best practices are you familiar with?. Name at least three



- Explain the directory layout of an Ansible role



- What 'blocks' are used for in Ansible?



- How do you handle errors in Ansible?



- You would like to run a certain command if a task fails. How would you achieve that?



- Write a playbook to install ‘zlib’ and ‘vim’ on all hosts if the file ‘/tmp/mario’ exists on the system.

```
---
- hosts: all
  vars:
      mario_file: /tmp/mario
      package_list:
          - 'zlib'
          - 'vim'
  tasks:
      - name: Check for mario file
        stat:
            path: "{{ mario_file }}"
        register: mario_f

      - name: Install zlib and vim if mario file exists
        become: "yes"
        package:
            name: "{{ item }}"
            state: present
        with_items: "{{ package_list }}"
        when: mario_f.stat.exists
```



- Write a single task that verifies all the files in files_list variable exist on the host

```
- name: Ensure all files exist
  assert:
    that:
      - item.stat.exists
  loop: "{{ files_list }}"
```



- Write a playbook to deploy the file ‘/tmp/system_info’ on all hosts except for controllers group, with the following content

  ```
  I'm <HOSTNAME> and my operating system is <OS>
  ```

  Replace <HOSTNAME> and  <OS> with the actual data for the specific host you are running on

The playbook to deploy the system_info file

```
---
- name: Deploy /tmp/system_info file
  hosts: all:!controllers
  tasks:
      - name: Deploy /tmp/system_info
        template:
            src: system_info.j2
            dest: /tmp/system_info
```

The content of the system_info.j2 template

```
# {{ ansible_managed }}
I'm {{ ansible_hostname }} and my operating system is {{ ansible_distribution }
```



- The variable 'whoami' defined in the following places:

  * role defaults -> whoami: mario
  * extra vars (variables you pass to Ansible CLI with -e) -> whoami: toad
  * host facts -> whoami: luigi
  * inventory variables (doesn’t matter which type) -> whoami: browser

According to variable precedence, which one will be used?

The right answer is ‘toad’.

Variable precedence is about how variables override each other when they set in different locations. If you didn’t experience it so far I’m sure at some point you will, which makes it a useful topic to be aware of.

In the context of our question, the order will be extra vars (always override any other variable) -> host facts -> inventory variables -> role defaults (the weakest).

Here is the order of precedence from least to greatest (the last listed variables winning prioritization):

1. command line values (eg “-u user”)
2. role defaults [[1\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id15)
3. inventory file or script group vars [[2\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id16)
4. inventory group_vars/all [[3\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id17)
5. playbook group_vars/all [[3\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id17)
6. inventory group_vars/* [[3\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id17)
7. playbook group_vars/* [[3\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id17)
8. inventory file or script host vars [[2\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id16)
9. inventory host_vars/* [[3\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id17)
10. playbook host_vars/* [[3\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id17)
11. host facts / cached set_facts [[4\]](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#id18)
12. play vars
13. play vars_prompt
14. play vars_files
15. role vars (defined in role/vars/main.yml)
16. block vars (only for tasks in block)
17. task vars (only for the task)
18. include_vars
19. set_facts / registered vars
20. role (and include_role) params
21. include params
22. extra vars (always win precedence)

A full list can be found at  [PlayBook Variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#ansible-variable-precedence) . Also, note there is a significant difference between Ansible 1.x and 2.x.



- For each of the following statements determine if it's true or false:

  * A module is a collection of tasks
  * It’s better to use shell or command instead of a specific module
  * Host facts override play variables
  * A role might include the following: vars, meta, and handlers
  * Dynamic inventory is generated by extracting information from external sources
  * It’s a best practice to use indention of 2 spaces instead of 4
  * ‘notify’ used to trigger handlers
  * This “hosts: all:!controllers” means ‘run only on controllers group hosts



- Explain the Diffrence between Forks and Serial & Throttle.

`Serial` is like running the playbook for each host in turn, waiting for completion of the complete playbook before moving on to the next host. `forks`=1 means run the first task in a play on one host before running the same task on the next host, so the first task will be run for each host before the next task is touched. Default fork is 5 in ansible.

```
[defaults]
forks = 30
```

```
- hosts: webservers
  serial: 1
  tasks:
    - name: ...
```

Ansible also supports `throttle` This keyword limits the number of workers up to the maximum set via the forks setting or serial. This can be useful in restricting tasks that may be CPU-intensive or interact with a rate-limiting API

```
tasks:
- command: /path/to/cpu_intensive_command
  throttle: 1
```




- What is ansible-pull? How is it different from how ansible-playbook works?



- What is Ansible Vault?



- Demonstrate each of the following with Ansible:

  * Conditionals
  * Loops




- What are filters? Do you have experience with writing filters?



- Write a filter to capitalize a string

```
def cap(self, string):
    return string.capitalize()
```



- You would like to run a task only if previous task changed anything. How would you achieve that?



- What are callback plugins? What can you achieve by using callback plugins?



- What is Ansible Collections?



- File '/tmp/exercise' includes the following content

```
Goku = 9001
Vegeta = 5200
Trunks = 6000
Gotenks = 32
```

With one task, switch the content to:

```
Goku = 9001
Vegeta = 250
Trunks = 40
Gotenks = 32
```


```
- name: Change saiyans levels
  lineinfile:
    dest: /tmp/exercise
    regexp: "{{ item.regexp }}"
    line: "{{ item.line }}"
  with_items:
    - { regexp: '^Vegeta', line: 'Vegeta = 250' }
    - { regexp: '^Trunks', line: 'Trunks = 40' }
    ...
```


#### Ansible Testing


- How do you test your Ansible based projects?



- What is Molecule? How does it works?



- You run Ansibe tests and you get "idempotence test failed". What does it mean? Why idempotence is important?
