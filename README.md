Proposed Implementation Plan  :

In DevOps fashion, the idea is to make implementation and provisioning as automatic as possible to fully automated provisioning. I will document the whole infrastructure in the git repository (Infrastructure as code). The best practice is that infrastructure changes must be requested with pull requests and approved by senior engineers. We will utilize the ansibles module for AWS dynamic inventory to interact with AWS API dynamically as the infrastructure gets larger for this to be possible. Different ansible roles will be dedicated to specifically tagged EC2 instances so we can run tasks on them. Ansible playbook tasks will be run in this order:

•	Infrastructure will be deployed (EC2, EIP, ALB)
•	Kubernetes requirements and components will be deployed tagged EC2 instances
•	The cluster will be initialized, and nodes will be added automatically
•	Calico CNI will be deployed networking and policy requirements
•	Manifest will be copied and applied on the cluster with application and database
•	Kubernetes user will be created for testing purposes
•	ETCD client will be installed and used to make a snapshot
•	HPA will be implemented so that the application can scale if needed

