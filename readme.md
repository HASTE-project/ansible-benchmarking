Ansible Playbooks for Automated Deployment of the HASTE Pipeline

Tested with Ubuntu LTS 16.04

Ensure that SSH configuration and IP addresses are configured (in `~/.ssh/config` and `/etc/hosts`) first. See 'hostnames.yml' for more details.

To deploy entire pipeline (dry run):

```
ansible-playbook -i hosts_ben_uppmax site.yml --check
```

ansible-playbook -i hosts_ben_uppmax site.yml


```
ansible -i hosts_ben_uppmax all -a "echo hi!"
```

To restart the Spark master and slaves:
(factored out to allow easy restarting for benchmarking tests)

GOTCHA: check the Spark master host name - its hard coded!!!



ansible-playbook -i hosts_ben_uppmax playbooks-util/restart-spark-cluster.yml


Contributors: Ben Blamey
