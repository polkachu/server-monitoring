# Prometheus, Grafana and Alert Manager Setup

This repo is to set up Prometheus, Grafana and Alert Manager for a groups on internal network nodes.

## Setp 1: Set up your own inventory file

Copy inventory file, and make your edits.

```bash
cp samples/inventory.sample inventory
```

## Setp 2: Customize a few files for Prometheus according to your network setup and jobs you want to run

Copy two configuration files, and make edits to reflect how your network is setup and what prometheus jobs you want to run

```bash
cp samples/config_hosts.yml.sample roles/prometheus/tasks/config_hosts.yml
cp samples/prometheus.yml.sample roles/prometheus/files/prometheus.yml
```

# Step 3: Run main playbook to set up a fresh monitor

The key monitor ansible file is main.yml, which will set up a new fresh monitor from scratch. It will set up firewall, install Prometheus, Grafana and Alert Manager

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

That's it!
