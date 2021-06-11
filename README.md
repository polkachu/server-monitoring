# Prometheus, Grafana and Alert Manager Setup for Polkadot

This repo is to set up Prometheus, Grafana and Alert Manager for a Polkadot node.

## Set Up Monitor

Copy inventory file.

```bash
cp inventory.sample inventory
```

The key monitor ansible file is main.yml, which will set up a new fresh monitor from scratch. It will set up firewall, install Prometheus, Grafana and Alert Manager

```bash
ansible-playbook -i inventory main.yml
```

You might want to run separate playboos as needed:

| Playbook               | Description                           |
| ---------------------- | ------------------------------------- |
| main.yml               | Full Setup                            |
| main_prepare.yml       | Some prep work; mostly firewall stuff |
| main_prometheus.yml    | Update Prometheus                     |
| main_grafana.yml       | Update Grafana                        |
| main_alert_manager.yml | Update Alert Manager                  |
