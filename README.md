openwrt-sqm
===========

configure sqm (Smart Queue Management) aspects of your openwrt system.
compare: [https://wiki.openwrt.org/doc/uci/sqm]

Role Variables
--------------

| variable name     | type             | description/structure                       | default |
|-------------------|------------------|---------------------------------------------|---------|
| queues            | map of objects   | key: interface, value: see attributes below | <empty> |

Role Variable elements
----------------------

interfaces attributes:

| attribute name               | property type       | Mandatory? | valid values / examples          |
|------------------------------|---------------------|------------|----------------------------------|
| enabled                      | boolean             | yes        | True / False                     |
| upload                       | number              | yes        | in kBit/s                        |
| download                     | number              | yes        | in kBit/s                        |
| qdisc                        | text                | ?          | see documentation on openwrt.org |
| qdisc_advanced               | boolean             | no         | True / False, see documentation on openwrt.org |
| qdisc_really_really_advanced | boolean             | no         | True / False, see documentation on openwrt.org |
| script                       | text                | ?          | see documentation on openwrt.org |
| linklayer                    | text                | ?          | see documentation on openwrt.org |
| linklayer                    | text                | ?          | see documentation on openwrt.org |
| debug_log                    | boolean             | ?          | see documentation on openwrt.org |
| verbosity                    | number              | ?          | see documentation on openwrt.org |

Dependencies
------------

* openwrt-uci

Example Playbook
----------------

```  
  - role: openwrt-sqm
    luci_support: True
    queues:
      eth0:
        enabled: True
        upload: 975
        download: 18000
        qdisc: fq_codel
        qdisc_advanced: False
        qdisc_really_really_advanced: True
        script: simple.qos
        linklayer: none
        debug_logging: True
        verbosity: 2
```

[https://wiki.openwrt.org/doc/uci/sqm]: https://wiki.openwrt.org/doc/uci/sqm
