# Heat Orchestration Template Example

the purpose of this template is to create the following openstack components

- Internal Network
- Router (add Internal Network & External Network Interface)
- Security Group
- Key Pair
- Flavor
- Instance
- Attach Floatin ip to Instance


## How to Run?

- Clone repository

```
git clone https://github.com/prastamaha/heat-stack-example.git
cd heat-stack-example
```

- edit `os-env.yml`

This template does not create external/provider networks, image, ssh keypair. so define them manually

```
parameters:
 demo_net_name: net-internal
 demo_net_cidr: 192.168.100.0/24
 demo_net_gateway: 192.168.100.1
 demo_net_pool_start: 192.168.100.2
 demo_net_pool_end: 192.168.100.254
 demo_subnet_name: subnet-internal
 demo_ext_net_name: <external-network-name>
 demo_sg_name: heat-sg
 demo_key_name: heat-key
 demo_public_key: <your-ssh-key>
 demo_image_name: <image-name>
 demo_flavor_name: heat-flavor
 demo_server1_name: heat-instance
```

- Create stack

```
openstack stack create -e os-env.yml -t os-heat.yml mystack
```

