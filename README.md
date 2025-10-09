# vcf9-adv-deploy-lab-setup

Open a Terminal on the Linux console and copy/paste the following commands. Enter the lab password when prompted (it will ask for the password multiple times).

sudo sed -i '0,/multiverse/s/multiverse/multiverse\ main\ restricted\ universe/' /etc/apt/sources.list.d/ubuntu.sources && \
sudo apt update -y && \
sudo apt install git -y && \
cd ~/Downloads && \
git clone https://github.com/bstein-vmware/vcf9-adv-deploy-lab-setup.git && \
cd vcf9-adv-deploy-lab-setup && \
chmod +x setup.sh && \
./setup.sh

\
\
\
Note: After you deploy a VKS cluster in a vSphere Namespace, Pod Security will likely block pods from deploying if the pod tries to run as root or run with priviledged access. To relax the Pod Security, as an example, on the default namespace (don't do this in production!): \
vcf context use vks-cluster-qxml:kubernetes-cluster-qxml \
kubectl label --overwrite namespace default pod-security.kubernetes.io/enforce=privileged
