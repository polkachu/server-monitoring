# Prometheus, Grafana and Alert Manager Setup

This repo is to set up Prometheus, Grafana and Alert Manager for a group of networked servers.

## Setp 1: Set up your own inventory file

Copy inventory file, and make your edits.

```bash
cp samples/inventory.sample inventory
```

## Setp 2: Customize several key files

Copy two configuration files, and make edits to reflect how your network is setup and what prometheus jobs you want to run.

```bash
cp samples/config_hosts.yml.sample roles/prometheus/tasks/config_hosts.yml
cp samples/prometheus.yml.sample roles/prometheus/files/prometheus.yml
```

The config_hosts.yml file is how we set up internal DNS lookup by editing /etc/hosts file. This will make the Grafana dashboard easier to read as each server has its human-readable name rather than an IP address like "10.0.0.1"

# Step 3: Run main playbook to set up a fresh monitor

The main monitor ansible file is main.yml, which sets up a new fresh monitor from scratch. It will set up firewall, install Prometheus, Grafana and Alert Manager.

```bash
ansible-playbook -i inventory main.yml
```

# Step 4: Run separate playbooks

You might want to run separate playbook as needed:

| Playbook               | Description                           |
| ---------------------- | ------------------------------------- |
| main.yml               | Full Setup                            |
| main_prepare.yml       | Some prep work; mostly firewall stuff |
| main_prometheus.yml    | Update Prometheus                     |
| main_grafana.yml       | Update Grafana                        |
| main_alert_manager.yml | Update Alert Manager                  |
| main_loki.yml          | Update Loki                           |
| main_node_exporter.yml | Update Node Exporter                  |

That's it!
