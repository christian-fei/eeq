ELK Epic Quotes
===============


## Requirements

- vagrant (tested with *1.8.1*)
- Ansible (tested with *1.9.3*)


## Installation

Add an entry to your hosts file that maps the domain `eeq.dev` to the IP of the virtual machine:

```
192.168.11.20    eeq.dev
```

---

Create the virtual machine with vagrant:

```
vagrant up
```

---

Install the ansible roles:

```
[sudo] ansible-galaxy install -r requirements.yml
```
