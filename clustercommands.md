Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\Users\abhin> docker exec -it rabbitmq-slave rabbitmqctl stop_app 
Stopping rabbit application on node rabbit@rabbitmq-slave ...

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug rabbitmq-slave
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\abhin> docker exec -it rabbitmq-slave2 rabbitmqctl stop_app
Stopping rabbit application on node rabbit@rabbitmq-slave2 ...

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug rabbitmq-slave2
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\abhin>docker exec -it rabbitmq-slave rabbitmqctl join_cluster rabbit@rabbitmq-master
Clustering node rabbit@rabbitmq-slave with rabbit@rabbitmq-master

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug rabbitmq-slave
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\abhin>docker exec -it rabbitmq-slave2 rabbitmqctl join_cluster rabbit@rabbitmq-master
Clustering node rabbit@rabbitmq-slave2 with rabbit@rabbitmq-master

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug rabbitmq-slave2
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\abhin>docker exec -it rabbitmq-slave rabbitmqctl start_app       
Starting node rabbit@rabbitmq-slave ...

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug rabbitmq-slave
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\abhin>docker exec -it rabbitmq-slave2 rabbitmqctl start_app
Starting node rabbit@rabbitmq-slave2 ...

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug rabbitmq-slave2
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\abhin> docker exec rabbitmq-master rabbitmqctl cluster_status 
Cluster status of node rabbit@rabbitmq-master ...
Basics

Cluster name: rabbit@rabbitmq-master
Total CPU cores available cluster-wide: 48

Cluster Tags

(none)

Disk Nodes

rabbit@rabbitmq-master
rabbit@rabbitmq-slave
rabbit@rabbitmq-slave2

Running Nodes

rabbit@rabbitmq-master
rabbit@rabbitmq-slave
rabbit@rabbitmq-slave2

Versions

rabbit@rabbitmq-master: RabbitMQ 4.0.7 on Erlang 27.3
rabbit@rabbitmq-slave: RabbitMQ 4.0.7 on Erlang 27.3
rabbit@rabbitmq-slave2: RabbitMQ 4.0.7 on Erlang 27.3

CPU Cores

Node: rabbit@rabbitmq-master, available CPU cores: 16
Node: rabbit@rabbitmq-slave, available CPU cores: 16
Node: rabbit@rabbitmq-slave2, available CPU cores: 16

Maintenance status

Node: rabbit@rabbitmq-master, status: not under maintenance
Node: rabbit@rabbitmq-slave, status: not under maintenance
Node: rabbit@rabbitmq-slave2, status: not under maintenance

Alarms

(none)

Network Partitions

(none)

Listeners

Node: rabbit@rabbitmq-master, interface: [::], port: 15672, protocol: http, purpose: HTTP API
Node: rabbit@rabbitmq-master, interface: [::], port: 15692, protocol: http/prometheus, purpose: Prometheus exporter API over HTTP
Node: rabbit@rabbitmq-master, interface: [::], port: 25672, protocol: clustering, purpose: inter-node and CLI tool communication
Node: rabbit@rabbitmq-master, interface: [::], port: 5672, protocol: amqp, purpose: AMQP 0-9-1 and AMQP 1.0
Node: rabbit@rabbitmq-slave, interface: [::], port: 15672, protocol: http, purpose: HTTP API
Node: rabbit@rabbitmq-slave, interface: [::], port: 15692, protocol: http/prometheus, purpose: Prometheus exporter API over HTTP
Node: rabbit@rabbitmq-slave, interface: [::], port: 25672, protocol: clustering, purpose: inter-node and CLI tool communication
Node: rabbit@rabbitmq-slave, interface: [::], port: 5672, protocol: amqp, purpose: AMQP 0-9-1 and AMQP 1.0
Node: rabbit@rabbitmq-slave2, interface: [::], port: 15672, protocol: http, purpose: HTTP API
Node: rabbit@rabbitmq-slave2, interface: [::], port: 15692, protocol: http/prometheus, purpose: Prometheus exporter API over HTTP
Node: rabbit@rabbitmq-slave2, interface: [::], port: 25672, protocol: clustering, purpose: inter-node and CLI tool communication
Node: rabbit@rabbitmq-slave2, interface: [::], port: 5672, protocol: amqp, purpose: AMQP 0-9-1 and AMQP 1.0

Feature flags

Flag: classic_mirrored_queue_version, state: enabled
Flag: classic_queue_type_delivery_support, state: enabled
Flag: detailed_queues_endpoint, state: enabled
Flag: direct_exchange_routing_v2, state: enabled
Flag: drop_unroutable_metric, state: enabled
Flag: empty_basic_get_metric, state: enabled
Flag: feature_flags_v2, state: enabled
Flag: implicit_default_bindings, state: enabled
Flag: khepri_db, state: disabled
Flag: listener_records_in_ets, state: enabled
Flag: maintenance_mode_status, state: enabled
Flag: message_containers, state: enabled
Flag: message_containers_deaths_v2, state: enabled
Flag: quorum_queue, state: enabled
Flag: quorum_queue_non_voters, state: enabled
Flag: rabbit_exchange_type_local_random, state: enabled
Flag: rabbitmq_4.0.0, state: enabled
Flag: restart_streams, state: enabled
Flag: stream_filtering, state: enabled
Flag: stream_queue, state: enabled
Flag: stream_sac_coordinator_unblock_group, state: enabled
Flag: stream_single_active_consumer, state: enabled
Flag: stream_update_config_command, state: enabled
Flag: tracking_records_in_ets, state: enabled
Flag: user_limits, state: enabled
Flag: virtual_host_metadata, state: enabled
PS C:\Users\abhin> docker exec rabbitmq-master rabbitmqctl cluster_status
Cluster status of node rabbit@rabbitmq-master ...
Basics

Cluster name: rabbit@rabbitmq-master
Total CPU cores available cluster-wide: 32

Cluster Tags

(none)

Disk Nodes

rabbit@rabbitmq-master
rabbit@rabbitmq-slave
rabbit@rabbitmq-slave2

Running Nodes

rabbit@rabbitmq-master
rabbit@rabbitmq-slave

Versions

rabbit@rabbitmq-master: RabbitMQ 4.0.7 on Erlang 27.3
rabbit@rabbitmq-slave: RabbitMQ 4.0.7 on Erlang 27.3

CPU Cores

Node: rabbit@rabbitmq-master, available CPU cores: 16
Node: rabbit@rabbitmq-slave, available CPU cores: 16

Maintenance status

Node: rabbit@rabbitmq-master, status: not under maintenance
Node: rabbit@rabbitmq-slave, status: not under maintenance

Alarms

(none)

Network Partitions

(none)

Listeners

Node: rabbit@rabbitmq-master, interface: [::], port: 15672, protocol: http, purpose: HTTP API
Node: rabbit@rabbitmq-master, interface: [::], port: 15692, protocol: http/prometheus, purpose: Prometheus exporter API over HTTP
Node: rabbit@rabbitmq-master, interface: [::], port: 25672, protocol: clustering, purpose: inter-node and CLI tool communication
Node: rabbit@rabbitmq-master, interface: [::], port: 5672, protocol: amqp, purpose: AMQP 0-9-1 and AMQP 1.0
Node: rabbit@rabbitmq-slave, interface: [::], port: 15672, protocol: http, purpose: HTTP API
Node: rabbit@rabbitmq-slave, interface: [::], port: 15692, protocol: http/prometheus, purpose: Prometheus exporter API over HTTP
Node: rabbit@rabbitmq-slave, interface: [::], port: 25672, protocol: clustering, purpose: inter-node and CLI tool communication
Node: rabbit@rabbitmq-slave, interface: [::], port: 5672, protocol: amqp, purpose: AMQP 0-9-1 and AMQP 1.0

Feature flags

Flag: classic_mirrored_queue_version, state: enabled
Flag: classic_queue_type_delivery_support, state: enabled
Flag: detailed_queues_endpoint, state: enabled
Flag: direct_exchange_routing_v2, state: enabled
Flag: drop_unroutable_metric, state: enabled
Flag: empty_basic_get_metric, state: enabled
Flag: feature_flags_v2, state: enabled
Flag: implicit_default_bindings, state: enabled
Flag: khepri_db, state: disabled
Flag: listener_records_in_ets, state: enabled
Flag: maintenance_mode_status, state: enabled
Flag: message_containers, state: enabled
Flag: message_containers_deaths_v2, state: enabled
Flag: quorum_queue, state: enabled
Flag: quorum_queue_non_voters, state: enabled
Flag: rabbit_exchange_type_local_random, state: enabled
Flag: rabbitmq_4.0.0, state: enabled
Flag: restart_streams, state: enabled
Flag: stream_filtering, state: enabled
Flag: stream_queue, state: enabled
Flag: stream_sac_coordinator_unblock_group, state: enabled
Flag: stream_single_active_consumer, state: enabled
Flag: stream_update_config_command, state: enabled
Flag: tracking_records_in_ets, state: enabled
Flag: user_limits, state: enabled
Flag: virtual_host_metadata, state: enabled
PS C:\Users\abhin> 
