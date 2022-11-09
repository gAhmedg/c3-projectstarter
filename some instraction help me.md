ssh -i <key.pem> ubuntu@<host_name> 

ssh -i prometheus.pem ubuntu@ec2-44-205-245-29.compute-1.amazonaws.com

ssh -i prometheus.pem ubuntu@ec2-54-83-71-228.compute-1.amazonaws.com

ssh -i udacity.pem ubuntu@ec2-54-164-5-26.compute-1.amazonaws.com

# connect ssh    
ssh -i prometheus.pem ubuntu@ec2-44-205-245-29.compute-1.amazonaws.com
# download prometheus
wget https://github.com/prometheus/prometheus/releases/download/v2.40.0/prometheus-2.40.0.linux-amd64.tar.gz



sudo cp prometheus-2.40.0.linux-amd64/prometheus /usr/local/bin
sudo cp prometheus-2.40.0.linux-amd64/promtool /usr/local/bin/
sudo cp -r prometheus-2.40.0.linux-amd64/consoles /etc/prometheus
sudo cp -r prometheus-2.40.0.linux-amd64/console_libraries /etc/prometheus

sudo cp prometheus-2.40.0.linux-amd64/promtool /usr/local/bin/
rm -rf prometheus-2.40.0.linux-amd64.tar.gz prometheus-2.40.0.linux-amd64



/etc/prometheus/prometheus.yml

/etc/systemd/system/prometheus.service


# node-exporter
wget https://github.com/prometheus/node_exporter/releases/download/v1.0.1/node_exporter-1.0.1.linux-amd64.tar.gz

# such winrar
tar xvfz prometheus-2.40.0.linux-amd64.tar.gz

tar xvfz node_exporter-1.0.1.linux-amd64.tar.gz 



# VERSION
./prometheus --version


# server
./prometheus --config.file=./prometheus.yml

# edit file 
nano ./prometheus.yml



## ###########################

sudo useradd --no-create-home prometheus 

prometheus

sudo nano /etc/prometheus/prometheus.yml

sudo nano /etc/systemd/system/prometheus.service

---------------------------------------------------------
----------------------------------------------------------
[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
user=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries

[Install]
WantedBy=multi-user.target

------------------------------------------------------------
------------------------------------------------------------




sudo nano /etc/systemd/system/node_exporter.service



[Unit]
Description=Prometheus Node Exporter service
After=network.target

[Service]
user=node_exporter
Group=node_exporter
Type=simple
ExecStart=/user/local/bin/node_exporter

[Install]
WantedBy=multi-user.target

=======================================================


sudo chown prometheus:prometheus /etc/prometheus
sudo chown prometheus:prometheus /usr/local/bin/prometheus
sudo chown prometheus:prometheus /usr/local/bin/promtool
sudo chown -R prometheus:prometheus /etc/prometheus/consoles
sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
  


sudo systemctl daemon-reload


sudo systemctl enable node_exporter
sudo systemctl enable prometheus


sudo systemctl start prometheus
sudo systemctl start node_exporter



sudo systemctl status prometheus

[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries

[Install]
WantedBy=multi-user.target


