# AWS Kubernetes Cluster (EKS) Setup
Based on this video on Youtube [AWS EKS - Create Kubernetes cluster on Amazon EKS | the easy way
](https://www.youtube.com/watch?v=p6xDCz00TxU&t=668s).  
To learn more about ``eksctl`` visit the websire [eksctl.io](https://eksctl.io/) .

### Install eksctl on macOS
Following the structure on the website [eksctl](https://github.com/weaveworks/eksctl) :
```shell
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```

## eksctl needs to authenticate with AWS

### 1. Install AWS CLI
Follow the structure on the website [aws cli install](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) and install aws cli for your machine. 
### 2. Instal AWS CLI on MacOS
```shell
brew install awscli
```
### 3. Authenticate
Follow the structures on the website [aws cli basic configuration](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html).  
First you need to create access key for your IAM user. In the web page mentioned above all the steps needed to walk are placed. Then, when you provide the access keys, let's configure the aws cli like this:
```shell
$ aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-2
Default output format [None]: json
```
 

## Create Cluster
Enter this command
```shell
eksctl create cluster --name bahram-k8s --region eu-north-1 --node-type t3.small --nodes 2 --nodegroup-name linux-nodes
```
**Error:**  
Be sure that EC2 instance is available on that region. for example at this time t2.small is not available in eu-north-1 region. 

## Create kubeconfig file automatically
By default, the resulting configuration file is created at the default kubeconfig path ``(.kube/config)`` in your home directory or merged with an existing kubeconfig file at that location.
```shell
aws eks update-kubeconfig --region <region-code> --name <cluster-name>
```