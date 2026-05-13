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
| `radixnode_use_proxy_protocol` | `false` | Use proxy protocol for P2P |

### Optional Variables

The following variables are **optional**. They are only included in the node config when explicitly defined.

| Variable | Description |
|----------|-------------|
| `radixnode_genesis_data` | Genesis data string |
| `radixnode_genesis_data_file` | Path to genesis data file |
| `radixnode_node_key_create_if_missing` | Create node key if missing (boolean, default: `true`) |
| `radixnode_state_hash_tree_gc_interval_sec` | State hash tree GC interval in seconds |
| `radixnode_state_hash_tree_state_version_history_length` | State hash tree version history length |
| `radixnode_db_local_transaction_execution_index_enable` | Enable local transaction execution index (boolean) |
| `radixnode_db_account_change_index_enable` | Enable account change index (boolean) |
| `radixnode_db_entity_listing_indices_enable` | Enable entity listing indices (boolean) |
| `radixnode_db_historical_substate_values_enable` | Enable historical substate values (boolean) |
| `radixnode_db_checkpoints_path` | Path to DB checkpoints |
| `radixnode_mempool_max_transaction_count` | Max transactions in mempool |
| `radixnode_mempool_max_memory` | Max mempool memory |
| `radixnode_mempool_relayer_interval_ms` | Mempool relayer interval (ms) |
| `radixnode_mempool_relayer_max_peers` | Max relayer peers |
| `radixnode_mempool_relayer_max_relayed_size` | Max relayed size |
| `radixnode_mempool_relayer_max_message_transaction_count` | Max message transaction count |
| `radixnode_mempool_relayer_max_message_payload_size` | Max message payload size |
| `radixnode_mempool_reevaluation_interval_ms` | Mempool reevaluation interval (ms) |
| `radixnode_mempool_reevaluation_max_count` | Max reevaluation count |
| `radixnode_protocol_vertex_max_transaction_count` | Max transactions per vertex |
| `radixnode_protocol_vertex_max_total_transactions_size` | Max total transactions size per vertex |
| `radixnode_protocol_vertex_max_total_execution_cost_units_consumed` | Max execution cost units per vertex |
| `radixnode_protocol_vertex_max_total_finalization_cost_units_consumed` | Max finalization cost units per vertex |
| `radixnode_protocol_custom_config` | Custom protocol configuration |
| `radixnode_core_api_bind_address` | Core API bind address (default: `0.0.0.0`) |
| `radixnode_core_api_flags_enable_unbounded_endpoints` | Enable unbounded core API endpoints (boolean) |
| `radixnode_engine_state_api_port` | Engine state API port |
| `radixnode_engine_state_api_bind_address` | Engine state API bind address |
| `radixnode_mesh_api_enabled` | Enable mesh API (boolean) |
| `radixnode_mesh_api_port` | Mesh API port |
| `radixnode_mesh_api_bind_address` | Mesh API bind address |
| `radixnode_system_api_bind_address` | System API bind address (default: `0.0.0.0`) |
| `radixnode_system_api_enable_db_checkpoint` | Enable DB checkpoint via system API (boolean) |
| `radixnode_prometheus_api_port` | Prometheus API port |
| `radixnode_prometheus_api_bind_address` | Prometheus API bind address |
| `radixnode_testing_forks_enable` | Enable testing forks (boolean) |
| `radixnode_testing_fork_config_name` | Testing fork config name |
| `radixnode_consensus_use_genesis_for_validator_address` | Use genesis for validator address (boolean) |
| `radixnode_consensus_validator_address` | Consensus validator address |
| `radixnode_bft_vertex_store_max_serialized_size_bytes` | Max BFT vertex store serialized size in bytes |

> **Note:** All boolean variables render as lowercase `true`/`false` in the generated config.

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
