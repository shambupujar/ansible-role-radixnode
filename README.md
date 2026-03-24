# Ansible Role: Radix Node

Deploys and configures a [Radix Babylon](https://www.radixdlt.com/) validator or fullnode as a systemd service.

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `radixnode_release` | `v1.3.0.2` | Radix node release version |
| `radixnode_user` | `radixdlt` | System user for the node |
| `radixnode_data_dir` | `/home/radixdlt/babylon-ledger` | Ledger data directory |
| `radixnode_dir` | `/etc/radixdlt/node` | Node config directory |
| `radixnode_network_id` | `1` | Network ID (1=mainnet) |
| `radixnode_host_ip` | `""` | Public IP (auto-detected if empty) |
| `radixnode_trusted_node` | `""` | Trusted node for syncing |
| `radixnode_p2p_broadcast_port` | `30000` | P2P broadcast port |
| `radixnode_p2p_listen_port` | `30001` | P2P listen port |
| `radixnode_core_api_port` | `3333` | Core API port |
| `radixnode_system_api_port` | `3334` | System API port |
| `radixnode_keystore_create` | `false` | Generate new keystore |
| `radixnode_keystore_deploy` | `false` | Deploy existing keystore |

## Example Playbook

```yaml
- hosts: radixnode
  become: true
  roles:
    - role: radixnode
      vars:
        radixnode_release: "v1.3.0.2"
        radixnode_trusted_node: "radix://node_..."
```

## License

MIT
