---
layout: layout.pug
navigationTitle:  Configuration Reference
title: Configuration Reference
menuWeight: 600
excerpt: List of all configuration parameters for Enterprise installations

enterprise: true
---



This topic provides configuration parameters available for [DC/OS Enterprise](https://mesosphere.com/product/). For configuration parameters available for [DC/OS](https://dcos.io/) please refer to [Configuration Reference for DC/OS](/1.10/installing/oss/custom/configuration/configuration-parameters/).

# Cluster Setup

| Parameter                              | Description                                                                                                                                               |
|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [agent_list](#agent-list)                                              | A YAML nested list (`-`) of IPv4 addresses to your [private agent](/1.10/overview/concepts/#private-agent-node) host names. |
| aws_template_storage_access_key_id         | The [access key ID](http://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) of the account owning the AWS S3 bucket. |
| aws_template_storage_bucket                | The name of an S3 bucket to contain [customized advanced AWS templates](/1.10/installing/ent/cloud/aws/advanced/#create-your-templates). |
| aws_template_storage_bucket_path           | The path to a location within the S3 bucket to store template artifacts.
| aws_template_storage_region_name           | The region containing the S3 bucket.  |
| aws_template_storage_secret_access_key     | The [secret access key](http://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) of the account owning the AWS S3 bucket. |
| aws_template_upload                        | Whether to upload the customized advanced AWS templates to an S3 bucket. |
| [bootstrap_url](#bootstrap-url)                                       | (Required) The URI path for the DC/OS installer to store the customized DC/OS build files. |
| [cluster_docker_credentials](#cluster-docker-credentials)             | The dictionary of Docker credentials to pass. |
| [cluster_docker_credentials_enabled](#cluster-docker-credentials-enabled)   |  Whether to pass the Mesos `--docker_config` option to Mesos. |
| [cluster_docker_registry_url](#cluster-docker-registry-url)           | The custom URL that Mesos uses to pull Docker images from. |
| [cluster_name](#cluster-name)                                         | The name of your cluster. |
| [cosmos_config](#cosmos-config)                                       | The dictionary of packaging configuration to pass to the [DC/OS Package Manager (Cosmos)](https://github.com/dcos/cosmos). |
| [custom_checks](#custom-checks)                                       | Custom installation checks that are added to the default check configuration process. |
| [exhibitor_storage_backend](#exhibitor-storage-backend)               | The type of storage backend to use for Exhibitor. |
| [enable_gpu_isolation](#enable-gpu-isolation)                         | Indicates whether to enable GPU support in DC/OS.  |
| [gpus_are_scarce](#gpus-are-scarce)                                   | Indicates whether to treat GPUs as a scarce resource in the cluster. |
| [ip_detect_public_filename](#ip-detect-public-filename)               | The IP detect file to use in your cluster.  |
| [master_discovery](#master-discovery)                                 | (Required) The Mesos master discovery method.         |
| [master_external_loadbalancer](#master-external-loadbalancer)         | The DNS name or IP address for the load balancer.         |
| [mesos_container_log_sink](#mesos-container-log-sink)                 | The log manager for containers (tasks). |
| [platform](#platform)                                                 | The infrastructure platform. |
| [public_agent_list](#public-agent-list)                               | A YAML nested list (`-`) of IPv4 addresses to your [public agent](/1.10/overview/concepts/#public-agent-node) host names.  |
| [rexray_config](#rexray-config)                                       | The [REX-Ray](https://rexray.readthedocs.io/en/v0.9.0/user-guide/config/) configuration method for enabling external persistent volumes in Marathon. You cannot specify both `rexray_config` and `rexray_config_preset`.|
| [rexray_config_preset](#rexray-config-preset) | If you run DC/OS on AWS setting this parameter to `aws`, sets the `rexray_config` parameter to a sensible default REX-Ray configuration that is bundled with DC/OS itself. You cannot specify both `rexray_config` and `rexray_config_preset`. |

# Networking

| Parameter                    | Description                                                                                                                                                       |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [dcos_overlay_enable](#dcos-overlay-enable)           | Block of parameters that specifies whether to enable DC/OS virtual networks. |
| [dns_bind_ip_blacklist](#dns-bind-ip-blacklist)       | A list of IP addresses that DC/OS DNS resolvers cannot bind to.|
| [dns_forward_zones](#dns-forward-zones)               | A nested list of DNS zones, IP addresses, and ports that configure custom forwarding behavior of DNS queries.  |
| [dns_search](#dns-search)                             | A space-separated list of domains that are tried when an unqualified domain is entered.  |
| [master_dns_bindall](#master-dns-bindall)             | Indicates whether the master DNS port is open.  |
| [mesos_dns_set_truncate_bit](#mesos-dns-set-truncate-bit)   |  Indicates whether to set the truncate bit if the response is too large to fit in a single packet. |
| [resolvers](#resolvers)                               | A YAML nested list (`-`) of DNS resolvers for your DC/OS cluster nodes.|
| [use_proxy](#use-proxy)                               | Indicates whether to enable the DC/OS proxy. |

# Performance and Tuning

| Parameter                    | Description                                                                                                                                                       |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [docker_remove_delay](#docker-remove-delay) | The amount of time to wait before removing stale Docker images stored on the agent nodes and the Docker image generated by the installer. |
| [dcos_audit_logging](#dcos-audit-logging-enterprise)  | [enterprise type="inline" size="small" /] Indicates whether security decisions (authentication, authorization) are logged for Mesos, Marathon, and Jobs. |
| [enable_docker_gc](#enable-docker-gc)     | Indicates whether to run the [docker-gc](https://github.com/spotify/docker-gc#excluding-images-from-garbage-collection) script, a simple Docker container and image garbage collection script, once every hour to clean up stray Docker containers. |
| [gc_delay](#gc-delay)                     | The maximum amount of time to wait before cleaning up the executor directories. |
| [log_directory](#log-directory)           | The path to the installer host logs from the SSH processes. |
| [mesos_max_completed_tasks_per_framework](#mesos-max-completed-tasks-per-framework)  | The number of completed tasks for each framework that the Mesos master will retain in memory. |
| [process_timeout](#process-timeout)       | The allowable amount of time, in seconds, for an action to begin after the process forks. |

# Security and Authentication

| Parameter                          | Description                                                                                                                                                |
|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [adminrouter_auth_cache_enabled](#adminrouter-auth-cache-enabled-enterprise)    | [enterprise type="inline" size="small" /] Controls whether the Admin Router authorization cache is enabled. |
| [auth_cookie_secure_flag](#auth-cookie-secure-flag-enterprise)    | [enterprise type="inline" size="small" /] Indicates whether to allow web browsers to send the DC/OS authentication cookie through a non-HTTPS connection. |
| [bouncer_expiration_auth_token_days](#bouncer-expiration-auth-token-days-enterprise) | [enterprise type="inline" size="small" /] Sets the auth token time-to-live (TTL) for Identity and Access Management. |
| [customer_key](#customer-key-enterprise)                       | [enterprise type="inline" size="small" /] (Required) The DC/OS Enterprise customer key. |
| ca_certificate_path                   | [enterprise type="inline" size="small" /] Use this to set up a custom CA certificate. See [this page](/1.10/security/ent/tls-ssl/ca-custom#configuration-parameter-reference) for a detailed configuration parameter reference. |
| ca_certificate_key_path           | [enterprise type="inline" size="small" /] Use this to set up a custom CA certificate. See [this page](/1.10/security/ent/tls-ssl/ca-custom#configuration-parameter-reference) for a detailed configuration parameter reference. |
| ca_certificate_chain_path       | [enterprise type="inline" size="small" /] Use this to set up a custom CA certificate. See [this page](/1.10/security/ent/tls-ssl/ca-custom#configuration-parameter-reference) for a detailed configuration parameter reference. |
| [security](#security-enterprise)                               | [enterprise type="inline" size="small" /] The security mode: disabled, permissive, or strict.  |
| [ssh_key_path](#ssh-key-path)                            | The path to the installer uses to log into the target nodes. |
| [ssh_port](#ssh-port)                                    | The port to SSH to, for example 22. |
| [ssh_user](#ssh-user)                                    | The SSH username, for example `centos`. |
| [superuser_password_hash](#superuser-password-hash-enterprise) | [enterprise type="inline" size="small" /] (Required) The hashed superuser password. |
| [superuser_username](#superuser-username-enterprise)           | [enterprise type="inline" size="small" /] (Required) The user name of the superuser.|
| [telemetry_enabled](#telemetry-enabled)                  | Indicates whether to enable sharing of anonymous data for your cluster.  |
| [zk_super_credentials](#zk-superuser)            | [enterprise type="inline" size="small" /] The ZooKeeper superuser credentials.  |
| [zk_master_credentials](#zk-master)          | [enterprise type="inline" size="small" /] The ZooKeeper master credentials.  |
| [zk_agent_credentials](#zk-agent)           | [enterprise type="inline" size="small" /] The ZooKeeper agent credentials.  |

[enterprise]
### adminrouter_auth_cache_enabled
[/enterprise]

_This option was added in DC/OS 1.10.6._

Controls whether the Admin Router authorization cache is enabled.

*   `adminrouter_auth_cache_enabled: false` (default) Every authorization check Admin Router performs will load the user's permissions from the IAM.
*   `adminrouter_auth_cache_enabled: true` Admin Router will cache the user's permissions for 5 seconds after performing an authorization check.

### agent_list
A YAML nested list (`-`) of IPv4 addresses to your [private agent](/1.10/overview/concepts/#private-agent-node) host names.

[enterprise]
### auth_cookie_secure_flag
[/enterprise]

Indicates whether to allow web browsers to send the DC/OS authentication cookie through a non-HTTPS connection. Because the DC/OS authentication cookie allows access to the DC/OS cluster, it should be sent over an encrypted connection.

*   `auth_cookie_secure_flag: false` (default) Browsers will send the DC/OS authentication cookie through either an unencrypted HTTP connection or an encrypted HTTPS connection.
*   `auth_cookie_secure_flag: true` The authentication cookie set by DC/OS will contain the [`Secure` flag](https://www.owasp.org/index.php/SecureFlag), which instructs the browser to not send the cookie over unencrypted HTTP connections. This could cause authentication to fail under the following circumstances.

    - If the security mode is `disabled`.
    - If the security mode is `permissive`, the URL specifies HTTP, and the URL includes a target different from the root path (e.g., `http://<cluster-url>/<path>/`).
    - There are proxies in between the browser and DC/OS that terminate TLS.

### bootstrap_url
(Required) The URI path for the DC/OS installer to store the customized DC/OS build files. If you are using the automated DC/OS installer, you should specify `bootstrap_url: file:///opt/dcos_install_tmp` unless you have moved the installer assets. By default the automated DC/OS installer places the build files in `file:///opt/dcos_install_tmp`.

[enterprise]
### bouncer_expiration_auth_token_days
[/enterprise]

This parameter sets the auth token time-to-live (TTL) for Identity and Access Management. You must specify the value in Python float syntax wrapped in a YAML string. By default the token expires after 5 days. For example, to set the token lifetime to half a day:

```json
bouncer_expiration_auth_token_days: '0.5'
```

For more information, see the [security documentation](/1.10/security/ent/).

### cluster_docker_credentials
The dictionary of Docker credentials to pass.

- If unset, a default empty credentials file is created at `/etc/mesosphere/docker_credentials` during DC/OS install. A sysadmin can change credentials as needed. A `systemctl restart dcos-mesos-slave` or `systemctl restart dcos-mesos-slave-public` is required for changes to take effect.
- You can also specify by using the `--docker_config` JSON [format](http://mesos.apache.org/documentation/latest/configuration/). You can write as YAML in the `config.yaml` file and it will automatically be mapped to the JSON format for you. This stores the Docker credentials in the same location as the DC/OS internal configuration (`/opt/mesosphere`). If you need to update or change the configuration, you will have to create a new DC/OS internal configuration.

**Note:**
- `cluster_docker_credentials` takes effect only when [`cluster_docker_credentials_enabled`](#cluster-docker-credentials-enabled) is set to `'true'`
- `cluster_docker_credentials` takes effect during an upgrade only when `cluster_docker_credentials_dcos_owned` is set to `'true'`.

You can use the following options to further configure the Docker credentials:

*  `cluster_docker_credentials_dcos_owned` Indicates whether to store the credentials file in `/opt/mesosphere` or `/etc/mesosphere/docker_credentials`. A sysadmin cannot edit `/opt/mesosphere` directly.
    *  `cluster_docker_credentials_dcos_owned: 'true'` The credentials file is stored in `/opt/mesosphere`.
        *  `cluster_docker_credentials_write_to_etc` Whether to write a cluster credentials file.
            *  `cluster_docker_credentials_write_to_etc: 'true'` Write a credentials file. This can be useful if overwriting your credentials file will cause problems (e.g., if it is part of a machine image or AMI). This is the default value.
            *  `cluster_docker_credentials_write_to_etc: 'false'` Do not write a credentials file.
    *  `cluster_docker_credentials_dcos_owned: 'false'` The credentials file is stored in `/etc/mesosphere/docker_credentials`.

For more information, see the [examples](/1.10/installing/ent/custom/configuration/examples/#docker-credentials).

### cluster_docker_credentials_enabled
Whether to pass the Mesos `--docker_config` option containing [`cluster_docker_credentials`](#cluster-docker-credentials) to Mesos.

*  `cluster_docker_credentials_enabled: 'true'` Pass the Mesos `--docker_config` option to Mesos. It will point to a file that contains the provided `cluster_docker_credentials` data.
*  `cluster_docker_credentials_enabled: 'false'` Do not pass the Mesos `--docker_config` option to Mesos.


### cluster_docker_registry_url
The custom URL that Mesos uses to pull Docker images from. If set, it will configure the Mesos' `--docker_registry` flag to the specified URL. This changes the default URL Mesos uses for pulling Docker images. By default `https://registry-1.docker.io` is used.

### cluster_name
The name of your cluster.

### cosmos_config
The dictionary of packaging configuration to pass to the [DC/OS package manager](https://github.com/dcos/cosmos). If set, the following options must also be specified.

* `package_storage_uri`
  Where to permanently store DC/OS packages. The value must be a file URL, for example, `file:///var/lib/dcos/cosmos/packages`.
* `staged_package_storage_uri`
   Where to temporarily store DC/OS packages while they are being added. The value must be a file URL, for example, `file:///var/lib/dcos/cosmos/staged-packages`.

[enterprise]
### customer_key
[/enterprise]
(Required) The DC/OS Enterprise customer key. Customer keys are delivered via email to the Authorized Support Contact.

This key is a 128-bit hyphen-delimited hexadecimal identifier used to distinguish an individual cluster. The customer key serves as the Universally Unique Identifier (UUID) for a given installation.

Customer keys look like this:

```
ab1c23de-45f6-7g8h-9012-i345j6k7lm8n
```

For more information, see the [security documentation](/1.10/security/ent/).

### custom_checks
Custom installation checks that are added to the default check configuration process. The configuration is used by the [DC/OS Diagnostics component](/1.10/overview/architecture/components/#dcos-diagnostics) to perform installation and upgrade checks. These custom checks are run alongside the default pre and post-flight checks during installation and upgrade.

- `cluster_checks` - This group of parameters specifies the health checks across the DC/OS cluster.

    - `<check-name>` - The custom name of your health check.
    - `description` - Specify a description of the check.
    - `cmd` - Specify an array of health check command strings.
    - `timeout` - Specify how long to wait, in seconds, before assuming the check failed. A check that times out is assumed to have a status of `3 (UNKNOWN)`.

- `node_checks` - This group of parameters specifies node health checks.

    - `<check-name>` - The custom name of your health check.
    - `description` - Specify a description of the check.
    - `cmd` - Specify an array of health check command strings.
    - `timeout` - Specify how long to wait, in seconds, before assuming the check failed. A check that times out is assumed to have a status of `3 (UNKNOWN)`.

For more information on how these custom checks are used, see the [examples](/1.10/installing/ent/custom/configuration/examples/#custom-checks) and [Node and Cluster Health Check](/1.10/installing/ent/custom/node-cluster-health-check/) documentation.

[enterprise]
### dcos_audit_logging
[/enterprise]

Indicates whether security decisions (authentication, authorization) are logged for Mesos, Marathon, and Jobs.

* `'dcos_audit_logging': 'true'` Mesos, Marathon, and Jobs are logged. This is the default value.
* `'dcos_audit_logging': 'false'` Mesos, Marathon, and Jobs are not logged.

For more information, see the [security documentation](/1.10/security/ent/).

### dcos_overlay_enable

Indicates whether to enable DC/OS virtual networks.

**Important:** Virtual networks require Docker version 1.11 or later. If you are using Docker 1.10 or earlier, you must specify `dcos_overlay_enable: 'false'`. For more information, see the [system requirements](/1.10/installing/ent/custom/system-requirements/).

*  `dcos_overlay_enable: 'false'` Do not enable the DC/OS virtual network.
*  `dcos_overlay_enable: 'true'` Enable the DC/OS virtual network. This is the default value. After the virtual network is enabled, you can also specify the following parameters:

    *  `dcos_overlay_config_attempts` Specifies how many failed configuration attempts are allowed before the overlay configuration modules stop trying to configure a virtual network.

        **Tip:** The failures might be related to a malfunctioning Docker daemon.

    *  `dcos_overlay_mtu` The maximum transmission unit (MTU) of the Virtual Ethernet (vEth) on the containers that are launched on the overlay.

    *  `dcos_overlay_network` This group of parameters defines a virtual network for DC/OS.  The default configuration of DC/OS provides a virtual network named `dcos` with this YAML configuration:

        ```
        dcos_overlay_network:
            vtep_subnet: 44.128.0.0/20
            vtep_mac_oui: 70:B3:D5:00:00:00
            overlays:
              - name: dcos
                subnet: 9.0.0.0/8
                prefix: 26
        ```

        *  `vtep_subnet` A dedicated address space that is used for the VxLAN backend for the virtual network. This address space should not be routeable from outside the agents or master.
        *  `vtep_mac_oui` The MAC address of the interface connecting to the virtual network in the public node. **Important:** The last 3 bytes must be `00`.
        *  `overlays`
            *  `name` The canonical name (see [limitations](/1.10/networking/virtual-networks/) for constraints on naming virtual networks).
            *  `subnet` The subnet that is allocated to the virtual network.
            *  `prefix` The size of the subnet that is allocated to each agent and thus defines the number of agents on which the overlay can run. The size of the subnet is carved from the overlay subnet.

 For more information, see the [example](/1.10/installing/ent/custom/configuration/examples/#overlay) and [documentation](/1.10/networking/virtual-networks/).


### dns_bind_ip_blacklist
A list of IP addresses that DC/OS DNS resolvers cannot bind to.

### dns_forward_zones
A list of DNS zones, IP addresses, and ports that configure custom forwarding behavior of DNS queries. A DNS zone is mapped to a set of DNS resolvers.

A sample definition is as follows:

```yaml
dns_forward_zones:
a.contoso.com:
- "1.1.1.1:53"
- "2.2.2.2:53"
b.contoso.com:
- "3.3.3.3:53"
- "4.4.4.4:53"
```

In the above example, a DNS query to `myapp.a.contoso.com` will be forwarded to `1.1.1.1:53` or `2.2.2.2:53`. Likewise, a DNS query to `myapp.b.contoso.com` will be forwarded to `3.3.3.3:53` or `4.4.4.4:53`.

### dns_search
A space-separated list of domains that are tried when an unqualified domain is entered (e.g., domain searches that do not contain &#8216;.&#8217;). The Linux implementation of `/etc/resolv.conf` restricts the maximum number of domains to 6 and the maximum number of characters the setting can have to 256. For more information, see [man /etc/resolv.conf](http://man7.org/linux/man-pages/man5/resolv.conf.5.html).

A `search` line with the specified contents is added to the `/etc/resolv.conf` file of every cluster host. `search` can do the same things as `domain` and is more extensible because multiple domains can be specified.

In this example, `example.com` has public website `www.example.com` and all of the hosts in the datacenter have fully qualified domain names that end with `dc1.example.com`. One of the hosts in your datacenter has the hostname `foo.dc1.example.com`. If `dns_search` is set to &#8216;dc1.example.com example.com&#8217;, then every DC/OS host which does a name lookup of `foo` will get the A record for `foo.dc1.example.com`. If a machine looks up `www`, first `www.dc1.example.com` would be checked, but it does not exist, so the search would try the next domain, lookup `www.example.com`, find an A record, and then return it.

```yaml
dns_search: dc1.example.com dc1.example.com example.com dc1.example.com dc2.example.com example.com
```

### docker_remove_delay
The amount of time to wait before removing stale Docker images stored on the agent nodes and the Docker image generated by the installer. It is recommended that you accept the default value 1 hour.

### enable_docker_gc
Indicates whether to run the [docker-gc](https://github.com/spotify/docker-gc#excluding-images-from-garbage-collection) script, a simple Docker container and image garbage collection script, once every hour to clean up stray Docker containers. You can configure the runtime behavior by using the `/etc/` config. For more information, see the [documentation](https://github.com/spotify/docker-gc#excluding-images-from-garbage-collection)

*  `enable_docker_gc: 'true'` Run the docker-gc scripts once every hour. This is the default value for [cloud](/1.10/installing/ent/cloud/) template installations.
*  `enable_docker_gc: 'false'` Do not run the docker-gc scripts once every hour. This is the default value for [custom](/1.10/installing/ent/custom/) installations.

### exhibitor_storage_backend
The type of storage backend to use for Exhibitor. You can use internal DC/OS storage (`static`) or specify an external storage system (`zookeeper`, `aws_s3`, and `azure`) for configuring and orchestrating ZooKeeper with Exhibitor on the master nodes. Exhibitor automatically configures your ZooKeeper installation on the master nodes during your DC/OS installation.

*   `exhibitor_storage_backend: static`
    The Exhibitor storage backend is managed internally within your cluster.

    **Important:** If [master_discovery](#master-discovery) is set to `master_http_loadbalancer`, then exhibitor_storage_backend cannot be set to `static`.

*   `exhibitor_storage_backend: zookeeper`
    The ZooKeeper instance for shared storage. If you use a ZooKeeper instance to bootstrap Exhibitor, this ZooKeeper instance must be separate from your DC/OS cluster. You must have at least 3 ZooKeeper instances running at all times for high availability. If you specify `zookeeper`, you must also specify these parameters.
    *   `exhibitor_zk_hosts`
        A comma-separated list (`<ZK_IP>:<ZK_PORT>, <ZK_IP>:<ZK_PORT>, <ZK_IP:ZK_PORT>`) of one or more ZooKeeper node IP and port addresses to use for configuring the internal Exhibitor instances. Exhibitor uses this ZooKeeper cluster to orchestrate it's configuration. Multiple ZooKeeper instances are recommended for failover in production environments.
    *   `exhibitor_zk_path`
        The filepath that Exhibitor uses to store data.
*   `exhibitor_storage_backend: aws_s3`
    The Amazon Simple Storage Service (S3) bucket for shared storage. If you specify `aws_s3`, you must also specify these parameters:
    *  `aws_access_key_id`
       The AWS key ID.
    *  `aws_region`
       The AWS region for your S3 bucket.
    *  `aws_secret_access_key`
       The AWS secret access key.
    *  `exhibitor_explicit_keys`
       Indicates whether you are using AWS API keys to grant Exhibitor access to S3.
        *  `exhibitor_explicit_keys: 'true'`
           If you're  using AWS API keys to manually grant Exhibitor access.
        *  `exhibitor_explicit_keys: 'false'`
           If you're using AWS Identity and Access Management (IAM) to grant Exhibitor access to s3.
    *  `s3_bucket`
       The name of your S3 bucket.
    *  `s3_prefix`
       The S3 prefix to be used within your S3 bucket to be used by Exhibitor.

       **Tip:** AWS EC2 Classic is not supported.
*   `exhibitor_storage_backend: azure`
    An Azure Storage Account for shared storage. The data will be stored under the container named `dcos-exhibitor`. If you specify `azure`, you must also specify these parameters:
    *  `exhibitor_azure_account_name`
       The Azure Storage Account Name.
    *  `exhibitor_azure_account_key`
       The secret key to access the Azure Storage Account.
    *  `exhibitor_azure_prefix`
       The blob prefix to be used within your Storage Account to be used by Exhibitor.

### enable_gpu_isolation
Indicates whether to enable GPU support in DC/OS.

*  `enable_gpu_isolation: 'true'` Any GPUs that are installed in DC/OS will be automatically discovered and available as consumable resources for DC/OS tasks. This is the default value.
*  `enable_gpu_isolation: 'false'` GPUs are not available for use in the cluster.

For more information, see the [GPU documentation](/1.10/deploying-services/gpu/).

### gc_delay
The maximum amount of time to wait before cleaning up the executor directories. It is recommended that you accept the default value of 2 days.

### gpus_are_scarce
Indicates whether to treat [GPUs](/1.10/deploying-services/gpu/) as a scarce resource in the cluster.

*  `gpus_are_scarce: 'true'` Treat GPUs as a scarce resource. This reserves the GPUs exclusively for services that opt-in to consume GPUs via the [Mesos `GPU_RESOURCES` framework capability](http://mesos.apache.org/documentation/latest/gpu-support/). This is the default value.
*  `gpus_are_scarce: 'false'` Treat GPUs like any other resource. GPUs will be offered indiscriminately to all frameworks, regardless of whether they use the [Mesos `GPU_RESOURCES` framework capability](http://mesos.apache.org/documentation/latest/gpu-support/) or not.

### ip_detect_public_filename
The path to a file (`/genconf/ip-detect-public`) on your bootstrap node that contains a shell script to map internal IPs to a public IP. For example:

```bash
#!/bin/sh
set -o nounset -o errexit

curl -fsSL https://ipinfo.io/ip
```

### log_directory
The path to the installer host logs from the SSH processes. By default this is set to `/genconf/logs`. In most cases this should not be changed because `/genconf` is local to the container that is running the installer, and is a mounted volume.

### master_discovery
(Required) The Mesos master discovery method. The available options are `static` or `master_http_loadbalancer`.

*  `master_discovery: static`
   Specifies that Mesos agents are used to discover the masters by giving each agent a static list of master IPs. The masters must not change IP addresses, and if a master is replaced, the new master must take the old master's IP address. If you specify `static`, you must also specify this parameter:

    *  `master_list`
       A YAML nested list (`-`) of static master IP addresses.

*   `master_discovery: master_http_loadbalancer` The set of masters has an HTTP load balancer in front of them. The agent nodes will know the address of the load balancer. They use the load balancer to access Exhibitor on the masters to get the full list of master IPs. If you specify `master_http_load_balancer`, you must also specify these parameters:

    *  `exhibitor_address`
       (Required) The address (preferably an IP address) of the load balancer in front of the masters. If you need to replace your masters, this address becomes the static address that agents can use to find the new master. For DC/OS Enterprise, this address is included in [DC/OS certificates](/1.10/security/ent/tls-ssl/).

       The load balancer must accept traffic on ports 80, 443, 2181, 5050, 8080, 8181. The traffic must also be forwarded to the same ports on the master. For example, Mesos port 5050 on the load balancer should forward to port 5050 on the master. The master should forward any new connections via round robin, and should avoid machines that do not respond to requests on Mesos port 5050 to ensure the master is up.
    *  `num_masters`
       (Required) The number of Mesos masters in your DC/OS cluster. It cannot be changed later. The number of masters behind the load balancer must never be greater than this number, though it can be fewer during failures.

**Important:**

* If master_discovery is set to `master_http_loadbalancer`, then [exhibitor_storage_backend](#exhibitor-storage-backend) cannot be set to `static`.
* On platforms like AWS where internal IPs are allocated dynamically, you should not use a static master list. If a master instance were to terminate for any reason, it could lead to cluster instability.

### master_dns_bindall
Indicates whether the master DNS port is open. An open master DNS port listens publicly on the masters. If you are upgrading, set this parameter to `true`.

*  `master_dns_bindall: 'true'` The master DNS port is open. This is the default value.
*  `master_dns_bindall: 'false'` The master DNS port is closed.

### master_external_loadbalancer
The DNS name or IP address for the load balancer. If specified, this is included as subject alternative name in the [DC/OS certificate](/1.10/security/ent/tls-ssl/) of the Admin Router on the master nodes.

### mesos_container_log_sink

The log manager for containers (tasks). The options are:

* `'journald'` - send task logs only to journald.
* `'logrotate'` - send task logs only to the file system (i.e. a stdout/err file).
* `'journald+logrotate'` - Send logs to both journald and the file system.

The default is `logrotate`. Due to performance issues, `journald` is not recommended. For details, see [Logging API](/1.10/monitoring/logging/logging-api/#compatibility).

### mesos_dns_set_truncate_bit

Indicates whether Mesos-DNS sets the truncate bit if the response is too large to fit in a single packet.

*  `mesos_dns_set_truncate_bit: 'true'`  Mesos-DNS sets the truncate bit if the response is too large to fit in a single packet and is truncated. This is the default behavior and is in compliance with RFC7766.
*  `mesos_dns_set_truncate_bit: 'false'`  Mesos-DNS does not set the truncate bit if the response is too large to fit in a single packet. If you know your applications crash when resolving truncated DNS responses over TCP, or for performance reasons you want to avoid receiving the complete set of DNS records in response to your DNS requests, you should set this option to `false` and note that the DNS responses you receive from Mesos-DNS may be missing entries that were silently discarded. This means that truncated DNS responses will appear complete even though they aren't and therefore won't trigger a retry over TCP. This behavior does not conform to RFC7766.

For more information regarding truncated DNS responses and retrying over TCP see [RFC7766 - DNS Transport over TCP - Implementation Requirements](https://tools.ietf.org/html/rfc7766).

### mesos_max_completed_tasks_per_framework
The number of completed tasks for each framework that the Mesos master will retain in memory. In clusters with a large number of long-running frameworks, retaining too many completed tasks can cause memory issues on the master. If this parameter is not specified, the default Mesos value of 1000 is used.

### platform
The infrastructure platform. The value is optional, free-form with no content validation, and used for telemetry only. Supply an appropriate value to help inform DC/OS platform prioritization decisions. Example values: `aws`, `azure`, `oneview`, `openstack`, `vsphere`, `vagrant-virtualbox`, `onprem` (default).

### process_timeout
The allowable amount of time, in seconds, for an action to begin after the process forks. This parameter is not the complete process time. The default value is 120 seconds.

**Tip:** For a slower network, consider changing to `process_timeout: 600`.

### public_agent_list
A YAML nested list (`-`) of IPv4 addresses to your [public agent](/1.10/overview/concepts/#public-agent-node) host names.

### resolvers
A YAML nested list (`-`) of DNS resolvers for your DC/OS cluster nodes. You can specify a maximum of 3 resolvers. Set this parameter to the most authoritative nameservers that you have.

-  If you want to resolve internal hostnames, set it to a nameserver that can resolve them.
-  If you do not have internal hostnames to resolve, you can set this to a public nameserver like Google or AWS. For example, you can specify the [Google Public DNS IP addresses (IPv4)](https://developers.google.com/speed/public-dns/docs/using):

    ```bash
    resolvers:
    - 8.8.4.4
    - 8.8.8.8
    ```
-  If you do not have a DNS infrastructure and do not have access to internet DNS servers, you can specify `resolvers: []`. By specifying this setting, all requests to non-`.mesos` will return an error. For more information, see the Mesos-DNS [documentation](/1.10/networking/mesos-dns/).

**Caution:** If you set the `resolvers` parameter incorrectly, you will permanently damage your configuration and have to reinstall DC/OS.

### rexray_config
The <a href="https://rexray.readthedocs.io/en/v0.9.0/user-guide/config/" target="_blank">REX-Ray</a> configuration for enabling external persistent volumes in Marathon. REX-Ray is a storage orchestration engine. The following is an example configuration.

    rexray_config:
        rexray:
          loglevel: info
          service: ebs
        libstorage:
          integration:
            volume:
              operations:
                unmount:
                  ignoreusedcount: true
          server:
            tasks:
              logTimeout: 5m

See the external persistent volumes [documentation](/1.10/storage/external-storage/) for information on how to create your configuration.

If the `rexray_config` parameter is provided, its contents are used verbatim for REX-Ray's configuration. This lets you define completely custom REX-Ray configurations which integrate with various [external storage providers]( https://rexray.readthedocs.io/en/v0.9.0/user-guide/storage-providers/). However, if you upgrade your cluster to a version that includes an updated version of REX-Ray, you must ensure that your `rexray_config` parameter is compatible with the newer version of REX-Ray.


### rexray_config_preset

If you are running your cluster on AWS, and want DC/OS to integrate with the Elastic Block Storage (EBS) without caring about the specific REX-Ray configuration, set the `rexray_config_preset` parameter to `aws`. This sets the `rexray_config` parameter to the default REX-Ray configuration bundled with DC/OS. This option also has the benefit of automatically upgrading your cluster's REX-Ray configuration when you upgrade to a newer version of DC/OS that contains an updated REX-Ray version.

[enterprise]
### security
[/enterprise]

Specify a security mode other than `security: permissive` (the default). The possible values follow.

- `security: disabled`
- `security: permissive`
- `security: strict`

Refer to the [security modes](/1.10/security/ent/#security-modes) section for a detailed discussion of each parameter.

### ssh_key_path
The path that the installer uses to log into the target nodes. By default this is set to `/genconf/ssh_key`. This parameter should not be changed because `/genconf` is local to the container that is running the installer, and is a mounted volume.

### ssh_port
The port to SSH to, for example `22`.

### ssh_user
The SSH username, for example `centos`.

[enterprise]
### superuser_password_hash
[/enterprise]

(Required) The hashed superuser password. The `superuser_password_hash` is generated by using the installer `--hash-password` flag. This first super user account is used to provide a method of logging into DC/OS, at which point additional administrative accounts can be added. For more information, see the [security documentation](/1.10/security/ent/).

[enterprise]
### superuser_username
[/enterprise]

(Required) The user name of the superuser. This account uses the `superuser_password_hash`.  For more information, see the [security documentation](/1.10/security/ent/).

### telemetry_enabled
Indicates whether to enable sharing of anonymous data for your cluster. <!-- DC/OS auth -->

- `telemetry_enabled: 'true'` Enable anonymous data sharing. This is the default value.
- `telemetry_enabled: 'false'` Disable anonymous data sharing.

If you’ve already installed your cluster and would like to disable this in-place, you can go through an [upgrade][3] with the same parameter set.

### use_proxy

Indicates whether to enable the DC/OS proxy.

*  `use_proxy: 'false'` Do not configure DC/OS [components](/1.10/overview/architecture/components/) to use a custom proxy. This is the default value.
*  `use_proxy: 'true'` Configure DC/OS [components](/1.10/overview/architecture/components/) to use a custom proxy. If you specify `use_proxy: 'true'`, you can also specify these parameters:
    **Important:** The specified proxies must be resolvable from the provided list of [resolvers](#resolvers).
    *  `http_proxy: http://<user>:<pass>@<proxy_host>:<http_proxy_port>` The HTTP proxy.
    *  `https_proxy: https://<user>:<pass>@<proxy_host>:<https_proxy_port>` The HTTPS proxy.
    *  `no_proxy`: A YAML nested list (`-`) of subdomains to exclude from forwarding to the `https_proxy`. If the address matches one of these strings, or the host is within the domain of one of these strings, http(s) requests to that node are not proxied. For example, the `no_proxy` list can be a list of internal IP addresses.

        **Important:** Wildcard characters (`*`) are not supported.

For more information, see the [examples](/1.10/installing/ent/custom/configuration/examples/#http-proxy).

**Important:** You should also configure an HTTP proxy for [Docker](https://docs.docker.com/engine/admin/systemd/#/http-proxy).

<a id="zk-superuser"></a>
[enterprise]
### zk_super_credentials
[/enterprise]

On DC/OS `strict` and `permissive` mode clusters the information stored in ZooKeeper is protected using access control lists (ACLs) so that a malicious user cannot connect to the ZooKeeper Quorum and directly modify service metadata. ACLs specify sets of resource IDs (RIDs) and actions that are associated with those IDs. ZooKeeper supports pluggable authentication schemes and has a few built in schemes: `world`, `auth`, `digest`, `host`, and `ip`.

DC/OS ZooKeeper credentials `zk_super_credentials`, `zk_master_credentials`, and `zk_agent_credentials` use `digest` authentication, which requires a `<uid>:<password>` string which is then used as an ID while checking if a client can access a particular resource.

`zk_super_credentials` enables access to ZooKeeper's equivalent of the `root` or `superuser` account, which has access to all resources regardless of existing ACLs. This credential allows an operator to access all the metadata stored in the ZooKeeper Quorum and is used by the DC/OS bootstrap script while initializing the cluster. Default: `'super:secret'`.

To harden clusters, Mesosphere recommends that you change the defaults of all credentials to long, complex values. Once set, you can verify the settings using `/opt/mesosphere/active/exhibitor/usr/zookeeper/bin/zkCli.sh` available on DC/OS master nodes. By default, `zkCli` does not authenticate, so the nodes in the `/dcos` tree will not be accessible. After invoking `addauth digest <zk_super_credentials>` in `zkCli`, all the nodes in ZooKeeper will be accessible, with `zk_master_credentials` and `zk_agent_credentials` providing access to a subset of them. For example:

```
[zk: localhost:2181(CONNECTED) 0] addauth digest super:secret
[zk: localhost:2181(CONNECTED) 1] ls /dcos
[backup, agent, RootCA, secrets, vault, CAChainInclRoot, CAChain, CACertKeyType, ca, master]
[zk: localhost:2181(CONNECTED) 2] ls /dcos/secrets
[core, init, system, bootstrap_user, keys]
```
<a id="zk-master"></a>
[enterprise]
### zk_master_credentials
[/enterprise]

Credentials used by the bootstrapping processes to access the credentials of the services that will be running on the DC/OS master nodes.

<a id="zk-agent"></a>
[enterprise]
### zk_agent_credentials
[/enterprise]

Credentials used by the bootstrapping processes to access the credentials of the services that will be running on the DC/OS agent nodes.
