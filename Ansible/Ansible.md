Ansible:

Ansible is an open-source IT configuration management, Deployment and Orchestration Tool. It aims to provide large productivity gains to a wide variety of Automation Challenges.
It automates application deployment, intra service orchestration, cloud provisioning and many other IT tools.
Ansible is completely agentless which means Ansible works by connecting your nodes through ssh(by default). 
It is Push Based Mechanism.
Uses YAML scripting language whcih works on KEY-PAIR. Used Python for backend.

- Ansible Core   : An open-source automation platform
- Ansible Tower  : A web application and REST API for ansible
- Ansible Galaxy : A website with a large catalogue of community created roles

##### Why Ansible: 
- Simplistic
- Reliable
- Powerful
- Agentless

### Ansible concepts:
** Control Node: ** A system on which Ansible installed. You run Ansible commands such as 
** Managed node: ** A remote system, or host, that Ansible controls.
** Inventory: ** A list of managed nodes that are logically organized. You create an inventory on the control node to describe host deployments to Ansible.

![https://docs.ansible.com/ansible/latest/_images/ansible_basic.svg]

### Playbook:
- Playbooks are automation blueprints, in ** YAML ** format, that Ansible uses to deploy and configure managed nodes.

** Playbook: ** A list of plays that define the order in which Ansible performs operations, from top to bottom, to achieve an overall goal.
** Play: ** An ordered list of tasks that maps to managed nodes in an inventory. 
** Task: ** A list of one or more modules that defines the operations that Ansible performs.
** Module: ** A unit of code or binary that Ansible runs on managed nodes. Ansible modules are grouped in collections with a Fully Qualified Collection Name (FQCN) for each module.

Playbooks can:
- declare configurations
- orchestrate steps of any manual ordered process, on multiple sets of machines, in a defined order
- launch tasks synchronously or asynchronously




Roles provide a framework for fully independent, or interdependent collections of variables, tasks, files, templates, and modules.