Ansible Playbooks for Automated Deployment of the HASTE Pipeline

Tested with Ubuntu LTS 16.04

Ensure that SSH configuration and IP addresses are configured (in `~/.ssh/config` and `/etc/hosts`) first. See 'hostnames.yml' for more details.

For HPC2N use -i hosts_hpc2n
For UPPMAX use -i hosts_uppmax

**Note that many hosts do not have public IPs, you will need to configure SSH forwarding via one of the servers with a public IP**

```
ansible -i hosts_uppmax all -a "echo hi"
ansible -i hosts_hpc2n all -a "echo hi"
```

To deploy entire pipeline (dry run):

```
ansible-playbook -i hosts_hpc2n site.yml --check
```

To deploy for real:
```
ansible-playbook -i hosts_hpc2n site.yml
```

To restart the Spark master and slaves:
(factored out to allow easy restarting for benchmarking tests)

GOTCHA: check the Spark master host name - its hard coded!!!


```
ansible-playbook -i hosts_ben_uppmax playbooks-util/restart-spark-cluster.yml
```

Contributors: Ben Blamey
