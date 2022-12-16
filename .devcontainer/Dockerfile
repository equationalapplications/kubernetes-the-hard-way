FROM mcr.microsoft.com/vscode/devcontainers/base:focal

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
  && apt-get -y install --no-install-recommends wget unzip curl apt-transport-https ca-certificates gnupg jq openssh-client software-properties-common -y \
  && wget https://releases.hashicorp.com/terraform/0.14.7/terraform_0.14.7_linux_amd64.zip \
  && unzip terraform_0.14.7_linux_amd64.zip \
  && mv terraform /usr/local/bin/ \
  && terraform -v \
  && echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main"  | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
  && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg  | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - \
  && apt-get update -y \
  && apt-get install google-cloud-cli -y \
  && wget -q --show-progress --https-only --timestamping \
  https://storage.googleapis.com/kubernetes-the-hard-way/cfssl/1.4.1/linux/cfssl \
  https://storage.googleapis.com/kubernetes-the-hard-way/cfssl/1.4.1/linux/cfssljson \
  && chmod +x cfssl cfssljson \
  && sudo mv cfssl cfssljson /usr/local/bin/ \
  && wget https://storage.googleapis.com/kubernetes-release/release/v1.21.0/bin/linux/amd64/kubectl \
  && chmod +x kubectl \
  && sudo mv kubectl /usr/local/bin/