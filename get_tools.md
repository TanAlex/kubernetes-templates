brew update && brew install kubernetes-cli kops kubectx aws-iam-authenticator kubernetes-helm


Install Kubernetes Tools

https://www.eksworkshop.com/020_prerequisites/k8stools/

sudo curl --silent --location -o /usr/local/bin/kubectl \
  https://amazon-eks.s3.us-west-2.amazonaws.com/1.17.7/2020-07-08/bin/linux/amd64/kubectl

sudo chmod +x /usr/local/bin/kubectl


# Install/update awscli

sudo pip install --upgrade awscli && hash -r


# install jq and envsubst
sudo yum -y install jq gettext bash-completion moreutils

# check installation
for command in kubectl jq envsubst aws
  do
    which $command &>/dev/null && echo "$command in path" || echo "$command NOT FOUND"
  done


# enable bash completion
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion


# install aws-iam-authenticator

curl -o aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.11.5/2018-12-06/bin/linux/amd64/aws-iam-authenticator
chmod +x ./aws-iam-authenticator
