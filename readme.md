Ansible Playbooks for Automated Deployment of servers for benchmarking study

see: 
_Apache Spark Streaming and HarmonicIO: A Performance and Architecture Comparison_ [https://arxiv.org/abs/1807.07724]

Also used for Uppsala University LDSA Course 2019, 2020 --  [https://studentportalen.uu.se/portal/portal/uusp/student/student-courses?courseCode=1TD268]


GOTCHAS (2021 branch): 
- check the Spark master host name - its hard coded!!!
    see: spark-worker/tasks/main.yml
- HDFS data nodes don't start with ansible? seems to work manually..?!
- maybe HDFS master node also
- The HDFS filesystem needs to be formatted before it will start from the master.
- some issue with the JDK environment variable missing? need a fresh shell session? (just run it more than once)
- TODO: add cron lines to restart hdfs/spark on reboot.


Ensure that SSH configuration and IP addresses are configured (in `~/.ssh/config` and `/etc/hosts`) first. See 'hostnames.yml' for more details.

For 2019 work,
For HPC2N use -i hosts_hpc2n
For UPPMAX use -i hosts_uppmax

**Note that many hosts do not have public IPs, you will need to configure SSH forwarding via one of the servers with a public IP**

To test ssh connection:
```
ansible -i hosts_uppmax_ldsa all -a "echo hi"
ansible -i hosts_hpc2n all -a "echo hi"
ansible -i hosts_snic_east1 all -a "echo hi"
ansible -i hosts_snic_east1_2021 all -a "echo hi"
```

To deploy entire pipeline (dry run):

```
ansible-playbook -i hosts_hpc2n site.yml --check
ansible-playbook -i hosts_uppmax site.yml --check
ansible-playbook -i hosts_snic_east1_2021 site.yml --check
```

To deploy for real:
```
ansible-playbook -i hosts_hpc2n site.yml
ansible-playbook -i hosts_uppmax_ldsa site.yml
ansible-playbook -i hosts_snic_east1 site.yml
ansible-playbook -i hosts_snic_east1_2021 site.yml
```

To restart the Spark master and slaves:
(factored out to allow easy restarting for benchmarking tests)




ansible -i hosts_uppmax_ldsa all -a "echo hi"
ansible -i hosts_uppmax_ldsa all -a "python3 --version"
ansible -i hosts_uppmax_ldsa all -a "sudo apt update"


```
ansible-playbook -i hosts_ben_uppmax playbooks-util/restart-spark-cluster.yml
```

Contributors: Ben Blamey