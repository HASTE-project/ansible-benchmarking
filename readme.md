Ansible Playbooks for Automated Deployment of the HASTE Pipeline

Tested with Ubuntu LTS 16.04

Ensure that SSH configration and IP addresses are configured (in `~/.ssh/config` and `/etc/hosts`) first. See 'hostnames.yml' for more details.

To deploy entire pipeline (dry run):

```
ansible-playbook site.yml --check
```


To restart the Spark master and slaves:
(factored out to allow easy restarting for benchmarking tests)

```
ansible-playbook playbooks-util/restart-spark-cluster.yml
```



Contributors: Ben Blamey
