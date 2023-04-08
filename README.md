# Prometheus, Grafana and Alert Manager Setup

This repo is to set up Prometheus, Grafana and Alert Manager for a group of networked servers.

## Step 1: Set up your own inventory file

Copy inventory file, and make your edits.

```bash
cp samples/inventory.sample inventory
```

## Step 2: Customize several key files

Copy two configuration files, and make edits to reflect how your network is setup and what prometheus jobs you want to run.

```bash
cp samples/hosts.sample roles/prometheus_config/files/hosts
cp samples/prometheus.yml.sample roles/prometheus_config/files/prometheus.yml
```

The config_hosts.yml file is how we set up internal DNS lookup by editing /etc/hosts file. This will make the Grafana dashboard easier to read as each server has its human-readable name rather than an IP address like "10.0.0.1"

# Step 3: Run main playbook to set up a fresh monitor

The main monitor ansible file is main.yml, which sets up a new fresh monitor from scratch. It will set up firewall, install Prometheus, Grafana and Alert Manager.

```bash
ansible-playbook -i inventory main.yml
```

That's it!
