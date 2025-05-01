## <pre>                             Terraform      </pre>

<summary>Explain what Terraform is and how does it works</summary><br><b>

Read [here](https://www.terraform.io/intro/index.html#what-is-terraform-)



<summary>What benefits infrastructure-as-code has?</summary><br><b>

- fully automated process of provisioning, modifying and deleting your infrastructure
- version control for your infrastructure which allows you to quickly rollback to previous versions
- validate infrastructure quality and stability with automated tests and code reviews
- makes infrastructure tasks less repetitive



<summary>Why Terraform and not other technologies? (e.g. Ansible, Puppet, CloufFormation)</summary><br><b>

A common *wrong* answer is to say that Ansible and Puppet are configuration management tools
and Terraform is a provisioning tool. While technically true, it doesn't mean Ansible and Puppet can't
be used for provisioning infrastructure. Also, it doesn't explain why Terraform should be used over
CloudFormation if at all.

The benefits of Terraform over the other tools:

  * It follows the immutable infrastructure approach which has benefits like avoiding a configuration drift over time
  * Ansible and Puppet are more procedural (you mention what to execute in each step) and Terraform is declarative since you describe the overall desired state and not per resource or task. You can give the example of going from 1 to 2 servers in each tool. In Terraform you specify 2, in Ansible and puppet you have to only provision 1 additional server so you need to explicitly make sure you provision only another one server.



<summary>True or False? Terraform follows the mutable infrastructure paradigm</summary><br><b>

False. Terraform follows immutable infrastructure paradigm.



<summary>True or False? Terraform uses declarative style to describe the expected end state</summary><br><b>
True



<summary>Explain what is "Terraform configuration"</summary><br><b>
A configuration is a root module along with a tree of child modules that are called as dependencies from the root module.



<summary>What is HCL?</summary><br><b>
HCL stands for Hashicorp Configuration Language. It is the language Hashicorp made to use as the configuration language for a number of its tools, including terraform.



<summary>Explain each of the following:

  * Provider
  * Resource
  * Provisioner
</summary><br><b>
  * Provider is any cloud based technology - github, aws, postgresql etc - which one can make an API call to with its unique terraform provider binary to provision available services and components.<br>
  * Resources are the services and components you provision on these platforms.<br>
  * Provisioner in terraform's lingo specifically refers to configuration tools like ansible or salt-stack which are used in combination with terraform to orchestrate a system.



<summary>What <code>terraform.tfstate</code> file is used for?</summary><br><b>

It keeps track of the IDs of created resources so that Terraform knows what it is managing.



<summary>How do you rename an existing resource?</summary><br><b>

terraform state mv



<summary>Explain what the following commands do:

  * <code>terraform init</code>
  * <code>terraform plan</code>
  * <code>terraform validate</code>
  * <code>terraform apply</code>
</summary><br><b>

<code>terraform init</code> scans your code to figure which providers are you using and download them.
<code>terraform plan</code> will let you see what terraform is about to do before actually doing it.
<code>terraform validate</code> checks if configuration is syntactically valid and internally consistent within a directory.
<code>terraform apply</code> will provision the resources specified in the .tf files.



<summary>How to write down a variable which changes by an external source or during <code>terraform apply</code>?</summary><br><b>

You use it this way: <code>variable “my_var” {}</code>



<summary>Give an example of several Terraform best practices</summary><br><b>



<summary>Explain how implicit and explicit dependencies work in Terraform</summary><br><b>



<summary>What is <code>local-exec</code> and <code>remote-exec</code> in the context of provisioners?</summary><br><b>



<summary>What is a "tainted resource"?</summary><br><b>

It's a resource which was successfully created but failed during provisioning. Terraform will fail and mark this resource as "tainted".



<summary>What <code>terraform taint</code> does?</summary><br><b>
<code>terraform taint resource.id</code> manually marks the resource as tainted in the state file. So when you run <code>terraform apply</code> the next time, the resource will be destroyed and recreated.



<summary>What types of variables are supported in Terraform?</summary><br><b>

string
number
bool
list(<TYPE>)
set(<TYPE>)
map(<TYPE>)
object({<ATTR_NAME> = <TYPE>, ... })
tuple([<TYPE>, ...])



<summary>What is a data source? In what scenarios for example would need to use it?</summary><br><b>
Data sources lookup or compute values that can be used elsewhere in terraform configuration.

There are quite a few cases you might need to use them:
* you want to reference resources not managed through terraform
* you want to reference resources managed by a different terraform module
* you want to cleanly compute a value with typechecking, such as with <code>aws_iam_policy_document</code>



<summary>What are output variables and what <code>terraform output</code> does?</summary><br><b>
Output variables are named values that are sourced from the attributes of a module. They are stored in terraform state, and can be used by other modules through <code>remote_state</code>



<summary>Explain Modules</summary>



<summary>What is the Terraform Registry?</summary><br><b>



<summary>Explain <code>remote-exec</code> and <code>local-exec</code></summary><br><b>




<summary>Explain "Remote State". When would you use it and how?</summary><br><b>
  Terraform generates a `terraform.tfstate` json file that describes components/service provisioned on the specified provider. Remote
  State stores this file in a remote storage media to enable collaboration amongst team.



<summary>Explain "State Locking"</summary><br><b>
  State locking is a mechanism that blocks an operations against a specific state file from multiple callers so as to avoid conflicting operations from different team members. Once the first caller's operation's lock is released the other team member may go ahead to
  carryout his own operation. Nevertheless Terraform will first check the state file to see if the desired resource already exist and
  if not it goes ahead to create it.



<summary>What is the "Random" provider? What is it used for</summary><br><b>
 The random provider aids in generating numeric or alphabetic characters to use as a prefix or suffix for a desired named identifier.



<summary>How do you test a terraform module?</summary><br><b>
  Many examples are acceptable, but the most common answer would likely to be using the tool <code>terratest</code>, and to test that a module can be initialized, can create resources, and can destroy those resources cleanly.



<summary>Aside from <code>.tfvars</code> files or CLI arguments, how can you inject dependencies from other modules?</summary><br><b>
  The built-in terraform way would be to use <code>remote-state</code> to lookup the outputs from other modules.
  It is also common in the community to use a tool called <code>terragrunt</code> to explicitly inject variables between modules.


## <pre>                              Ansible      </pre>
Ansible is an open-source automation tool that simplifies IT tasks such as configuration management, application deployment, and orchestration. It is agentless, uses SSH for communication, and is designed for simplicity and ease of use.
---

<summary>Describe each of the following components in Ansible, including the relationship between them:

  * Task
  * Module
  * Play
  * Playbook
  * Role
</summary><br><b>

`Task` – a call to a specific Ansible module
Module – the actual unit of code executed by Ansible on your own host or a remote host. Modules are indexed by category (database, file, network, …) and also referred to as task plugins.

`Play` – One or more tasks executed on a given host(s)

`Playbook` – One or more plays. Each play can be executed on the same or different hosts

`Role` – Ansible roles allows you to group resources based on certain functionality/service such that they can be easily reused. In a role, you have directories for variables, defaults, files, templates, handlers, tasks, and metadata. You can then use the role by simply specifying it in your playbook.



<summary>How Ansible is different from other Automation tools?</summary><br><b>

Ansible is:

* Agentless
* Minimal run requirements (Python & SSH) and simple to use
* Default mode is "push" (it supports also pull)
* Focus on simpleness and ease-of-use



<summary>True or False? Ansible follows the mutable infrastructure paradigm</summary><br><b>

True.



<summary>True or False? Ansible uses declarative style to describe the expected end state</summary><br><b>
False. It uses a procedural style.



<summary>What kind of automation you wouldn't do with Ansible and why?</summary><br><b>

While it's possible to provision resources with Ansible, some prefer to use tools that follow immutable infrastructure paradigm.
Ansible doesn't saves state by default. So a task that creates 5 instances for example, when executed again will create additional 5 instances (unless
additional check is implemented) while other tools will check if 5 instances exist. If only 4 exist, additional instance will be created.



<summary>What is an inventory file and how do you define one?</summary><br><b>

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



<summary>What is a dynamic inventory file? When you would use one?</summary><br><br>

A dynamic inventory file tracks hosts from one or more sources like cloud providers and CMDB systems.

You should use one when using external sources and especially when the hosts in your environment are being automatically<br>
spun up and shut down, without you tracking every change in these sources.



<summary>How do you list all modules and how can you see details on a specific module?</summary><br><br>

1. Ansible online docs
2. `ansible-doc -l` for list of modules and `ansible [module_name]` for detailed information on a specific module



<summary>Write a task to create the directory ‘/tmp/new_directory’</summary><br><b>

```
- name: Create a new directory
  file:
    path: "/tmp/new_directory"
    state: directory
```



<summary>You want to run Ansible playbook only on specific minor version of your OS, how would you achieve that?</summary><br><b>



<summary>What the "become" directive used for in Ansible?</summary><br><b>



<summary>What are facts? How to see all the facts of a certain host?</summary><br><b>



<summary>What would be the result of the following play?</summary><br><b>

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



<summary>What would be the result of running the following task? How to fix it?

```
- hosts: localhost
  tasks:
      - name: Install zlib
        package:
          name: zlib
          state: present
```
</summary><br><b>



<summary>Which Ansible best practices are you familiar with?. Name at least three</summary><br><b>



<summary>Explain the directory layout of an Ansible role</summary><br><b>



<summary>What 'blocks' are used for in Ansible?</summary><br><b>



<summary>How do you handle errors in Ansible?</summary><br><b>



<summary>You would like to run a certain command if a task fails. How would you achieve that?</summary><br><b>



<summary>Write a playbook to install ‘zlib’ and ‘vim’ on all hosts if the file ‘/tmp/mario’ exists on the system.</summary><br><b>

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



<summary>Write a single task that verifies all the files in files_list variable exist on the host</summary><br><b>

```
- name: Ensure all files exist
  assert:
    that:
      - item.stat.exists
  loop: "{{ files_list }}"
```



<summary>Write a playbook to deploy the file ‘/tmp/system_info’ on all hosts except for controllers group, with the following content</summary><br><b>

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



<summary>The variable 'whoami' defined in the following places:

  * role defaults -> whoami: mario
  * extra vars (variables you pass to Ansible CLI with -e) -> whoami: toad
  * host facts -> whoami: luigi
  * inventory variables (doesn’t matter which type) -> whoami: browser

According to variable precedence, which one will be used?</summary><br><b>

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



<summary>For each of the following statements determine if it's true or false:

  * A module is a collection of tasks
  * It’s better to use shell or command instead of a specific module
  * Host facts override play variables
  * A role might include the following: vars, meta, and handlers
  * Dynamic inventory is generated by extracting information from external sources
  * It’s a best practice to use indention of 2 spaces instead of 4
  * ‘notify’ used to trigger handlers
  * This “hosts: all:!controllers” means ‘run only on controllers group hosts</summary><br><b>



<summary>Explain the Diffrence between Forks and Serial & Throttle.</summary><br><b>

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




<summary>What is ansible-pull? How is it different from how ansible-playbook works?</summary><br><b>



<summary>What is Ansible Vault?</summary><br><b>



<summary>Demonstrate each of the following with Ansible:

  * Conditionals
  * Loops
</summary><br><b>



<summary>What are filters? Do you have experience with writing filters?</summary><br><b>



<summary>Write a filter to capitalize a string</summary><br><b>

```
def cap(self, string):
    return string.capitalize()
```



<summary>You would like to run a task only if previous task changed anything. How would you achieve that?</summary><br><b>



<summary>What are callback plugins? What can you achieve by using callback plugins?</summary><br><b>



<summary>What is Ansible Collections?</summary><br><b>



<summary>File '/tmp/exercise' includes the following content

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
</summary><br><b>

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


<summary>How do you test your Ansible based projects?</summary><br><b>



<summary>What is Molecule? How does it works?</summary><br><b>



<summary>You run Ansibe tests and you get "idempotence test failed". What does it mean? Why idempotence is important?</summary><br><b>

