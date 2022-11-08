ssh -i <key.pem> ubuntu@<host_name> 

ssh -i prometheus.pem ubuntu@ec2-44-205-245-29.compute-1.amazonaws.com

ssh -i prometheus.pem ubuntu@ec2-54-83-71-228.compute-1.amazonaws.com



# connect ssh    
ssh -i prometheus.pem ubuntu@ec2-44-205-245-29.compute-1.amazonaws.com
# download prometheus
wget https://github.com/prometheus/prometheus/releases/download/v2.19.0/prometheus-2.19.0.linux-amd64.tar.gz

# node-exporter
wget https://github.com/prometheus/node_exporter/releases/download/v1.0.1/node_exporter-1.0.1.linux-amd64.tar.gz

# such winrar
tar xvfz prometheus-2.19.0.linux-amd64.tar.gz

tar xvfz node_exporter-1.0.1.linux-amd64.tar.gz 



# VERSION
./prometheus --version


# server
./prometheus --config.file=./prometheus.yml

# edit file 
nano ./prometheus.yml