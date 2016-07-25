# [DEPRECATED] Basic RancherOS Cluster

** RancherOS does not support Vagrantfile any longer. **

```
vagrant up --provider virtualbox
```

```
┌─────────────────────────────────────────────────────┐
│                        10.10.10                     │
└────────┬──────────────────┬──────────────────┬──────┘
         │                  │                  │   
         │.101              │.102              │.103   
 ┌────┐ ┌┴─────┐    ┌────┐ ┌┴─────┐    ┌────┐ ┌┴─────┐
 │eth0│ │ eth1 │    │eth0│ │ eth1 │    │eth0│ │ eth1 │
┌┴────┴─┴──────┴┐  ┌┴────┴─┴──────┴┐  ┌┴────┴─┴──────┴┐
│               │  │               │  │               │
│   RancherOS   │  │   RancherOS   │  │   RancherOS   │
│               │  │               │  │               │
│    node-01    │  │    node-02    │  │    node-03    │
│               │  │               │  │               │
└───────────────┘  └───────────────┘  └───────────────┘
```

### Configuration (Head of Vagrantfile)

```
members = {
  #  Name       #, 1ST_IP
  'node'   => [ 3,    101 ],
}
PREFIX          = "10.10.10"
```
