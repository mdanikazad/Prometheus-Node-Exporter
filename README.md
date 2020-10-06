# Prometheus-Node-Exporter

[root@localhost ~]# wget https://github.com/prometheus/node_exporter/releases/download/v0.16.0-rc.1/node_exporter-0.16.0-rc.1.linux-amd64.tar.gz

[root@localhost ~]# tar -xzvf node_exporter-0.16.0-rc.1.linux-amd64.tar.gz

[root@localhost ~]# mv node_exporter-0.16.0-rc.1.linux-amd64 node_exporter

[root@localhost ~]# cd /etc/systemd/system/

[root@localhost system]# vi node_exporter.service

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=root
ExecStart=/root/node_exporter/node_exporter

[Install]
WantedBy=default.target

[root@localhost ~]# systemctl daemon-reload

[root@localhost ~]# systemctl start node_exporter

[root@localhost ~]# systemctl enable node_exporter

Check node exporter is exposing metrics by following command:

[root@localhost ~]# curl http://node-ip:9100/metrics

[root@localhost ~]# curl http://localhost:9100/metrics
