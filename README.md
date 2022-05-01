# configure-stf

Hello, this project let's you configure and deploy Service Telemetry Framework [STF] with the help of ansible playbooks.

Here's how to get started.

1. Clone the repository to your local system/jump/UPI node.
   # git clone <repository-path-here>

2. If you're running the tasks from a host where oc binary is already available you can skip this point and move on to the next step.
   Otherwise,
     Untar the binary and copy it to a path that has already been setup on your Linux host by the "PATH" environment variable.
     Here's a quick reference: https://docs.openshift.com/container-platform/4.7/cli_reference/openshift_cli/getting-started-cli.html

3. Login to the OCP Cluster by either using user/pass combination or a login token provided by the cluster.
   # oc login -u kubeadmin <api-url>
  
4. Run the deploy-prepare.yaml playbook to create the "service-telemetry" namespace, operatorgroups and different operators, object required for setting up STF.
   # ansible-playbook -vv deploy-prepare.yaml
  
5. The deploy-prepare playbook makes use of Ansible tags to grant more granular control to the user while configuring the cluster. A few tasks are labelled with tag "always"
   which suggests that the tasks included in that playbook would run irrespective of the tags provided by the user as those resources are needed clusterwide to proceed
   further with STF.
  
6. Once the required resources are created, the STF deployment can then be triggered.
   # ansible-playbook -vv deploy-stf.yaml
  
Thanks!!
   
