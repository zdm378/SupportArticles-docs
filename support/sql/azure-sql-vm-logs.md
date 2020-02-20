---
title: Azure SQL VM logs
description: Lists the SQL Server on Azure Virtual Machines logs and diagnostic information that's collected during troubleshooting by Microsoft Support.
ms.date: 02/17/2020
ms.prod-support-area-path:
---
# SQL Server on Azure Virtual Machines logs

**Applies to**: SQL Server in VM - Windows

_Original KB number:_ &nbsp; 4131517

If you select **Allow access to logs** when you create a Microsoft SQL Server on Azure Virtual Machines support case, Microsoft Support will get access to logs and data that are related to your environment to use for troubleshooting. These include common log files, configuration files, diagnostic information, system-generated event logs, and debug logs. The following tables list what information is collected and available to Support.

## Information collected by Transact-SQL (T-SQL) queries

|**Query**|**Columns**|**Frequency–once every...**|**Reference**|
|---|---|---|---|
|**sys.databases**|All columns are displayed in reference.|Day|[sys.databases](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)|
|**sys.dm_os_sys_info**|All columns are displayed in reference.|15 minutes|[sys.dm_os_sys_info](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql)|
|**sys.master_files**|All columns are displayed in reference.|15 minutes|[sys.master_files](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)|
|**sys.dm_os_nodes**|All columns are displayed in reference.|Day|[sys.dm_os_nodes](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql)|
|**sys.dm_os_schedulers**|All columns are displayed in reference.|Day|[sys.dm_os_schedulers](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql)|
|**Cluster Member State**|member_name, member_type_desc, member_state_desc, number_of_quorum_votes, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4|5 minutes|[sys.dm_hadr_cluster_members](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)   [sys.dm_hadr_cluster_networks](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)|
|**AlwaysOn Availability Group State**|availability_group, primary_replica, primary_recovery_health_desc, synchronization_health_desc, group_id, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference_desc|5 minutes|[sys.availability_groups](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)   [sys.dm_hadr_availability_group_states](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)|
|**AlwaysOn Availability Replica State**|group_name, replica_server_name, node_name, is_local, role_desc, availability_mode, availability_mode_Desc, failover_mode_desc, join_state_desc, operational_state_desc, connected_state_desc, recovery_health_desc, synhcronization_health_desc, last_connect_error_number, last_connect_error_description, last_connect_error_timestamp, endpoint_url, session_timeout, primary_role_allow_connections_desc, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url, replica_id, group_id|5 minutes|[sys.dm_hadr_availability_replica_cluster_nodes](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  [sys.dm_hadr_availability_replica_cluster_states](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  [sys.dm_hadr_availability_replica_states](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  [sys.availability_replicas](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  [sys.availability_groups](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|
|**AlwaysOn Availability Database Identification**|name, database_id, group_id, replica_id, is_local, is_failover_ready, is_pending_secondary_suspend, is_database_joined, is_suspended, is_commit_participant, suspend_reason_desc, synchronization_state_desc, synchronization_health_desc, database_state_desc, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, drs.redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn,last_commit_lsn, last_commit_time, low_water_mark_for_ghosts, recovery_lsn, truncation_lsn, file_id, error_type, page_id, page_status, modification_time|5 minutes|[sys.dm_hadr_database_replica_cluster_states](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)   [sys.dm_hadr_database_replica_states](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)   [sys.dm_hadr_auto_page_repair](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql) |
|**Database Mirroring Endpoint**|endpoint_name, endpoint_id, principal_id, protocol_desc, type_desc, state_desc, is_admin_endpoint, role_desc, is_encryption_enabled, connection_auth_desc, encryption_algorithm_desc|15 minutes|[sys.database_mirroring_endpoints](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)|
|**Availability Group Listeners**|listener_id, state_desc, dns_name, port, is_conformant, ip_configuration_string_from_cluster, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, network_subnet_prefix_length|15 minutes|[sys.availability_group_listeners](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  [sys.availability_group_listener_ip_addresses](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)|
|**AlwaysOn Windows Cluster**|cluster_name, quorum_type, quorum_state_desc|15 minutes|[sys.dm_hadr_cluster](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)|

## Information collected via PowerShell

|**Powershell command**|**Frequency–once every...**|
|---|---|
|**Get-ClusterLog**|Hour|
|**get-clusterresource** | **get-clusterparameter**|Hour|
|**get-cluster** | **fl**|Hour|

## Information collected by WMI queries

|**Wmi query**|**Columns**|**Frequency–once every...**|**Link**|
|---|---|---|---|
|**MSFT_Volume**|DriveType, DriveLetter, Size, SizeRemaining, FileSystemLabel, HealthStatus, FileSystem|Day|[MSFT_Volume](https://msdn.microsoft.com/library/windows/desktop/hh830604%28v=vs.85%29.aspx)|
|**MSFT_VirtualDisk**|FriendlyName, ResiliencySettingName, NumberOfColumns, Interleave, NumberOfAvailableCopies, OperationalStatus, UniqueIdFormat, HealthStatus, IsManualAttach, Size|Day|[MSFT_VirtualDisk](https://msdn.microsoft.com/library/windows/desktop/hh830584%28v=vs.85%29.aspx)|
|**MSFT_PhysicalDisk**|FriendlyName, CanPool, OperationalStatus, HealthStatus, Usage, Size|Day|[MSFT_PhysicalDisk](https://msdn.microsoft.com/library/windows/desktop/hh830532%28v=vs.85%29.aspx)|
|**MSFT_Disk**|Number, NumberOfPartitions, SerialNumber|Day|[MSFT_Disk](https://msdn.microsoft.com/library/windows/desktop/hh830493%28v=vs.85%29.aspx)|
|**MSFT_Partition**|DiskNumber, PartitionNumber, DriveLetter, GptType, IsBoot, IsSystem, Size|Day|[MSFT_Partition](https://msdn.microsoft.com/library/windows/desktop/hh830524%28v=vs.85%29.aspx)|

## More information

If you create a SQL Server AlwaysOn Availability Groups cluster, the AlwaysOn_health.xel files will be collected. For more information about the collected files, see[Always On Availability Groups extended events](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-extended-events).