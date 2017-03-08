# wwsh
Warewulf Shell help output

```sh
wwsh bootstrap => manage bootstrap images (import, export, delete, list, rebuild, build)
wwsh file      => view and manipulate files (import, export, edit, new, set, show, list, print, sync, delete)
wwsh ipmi      => ipmi attributes (set, list, print, poweron, poweroff, powercycle, ident, noident, etc.)
wwsh node      => view and manipulate nodes (new, set, list, print, delete, clone)
wwsh object    => generic attributes (modify, print, delete, dump, canoncialize)
wwsh provision => node provisioning attributes (set, list, print)
wwsh vnfs      => mange vnfs images (import, export, delete, list, set)

wwsh bootstrap [ import | export | delete | list | rebuild | build ]

wwsh bootstrap import /path/to/name.wwbs --name=bootstrap
wwsh bootstrap export bootstrap1 bootstrap2 /tmp/exported_bootstrap/
wwsh bootstrap list

wwsh file [ import | export ] 
wwsh file [ edit | new | delete ]
wwsh file [ set | show | list | print | sync | delete ]

wwsh file import /path/to/file/to/import --name=hosts-file
wwsh file import /path/to/file/to/import/with/given-name
wwsh file edit given-name
wwsh file set given-name --origin=UNDEF --mode=0700
wwsh file set hosts-file --path=/etc/hosts --mode=0644 --uid=0
wwsh file list
wwsh file delete name123 given-name

wwsh node [ new | set | list | print | delete | clone ]

wwsh node new n0000 --netdev=eth0 --hwaddr=xx:xx:xx:xx:xx:xx
wwsh node set n0000 -D eth0 -I 10.0.0.10 -G 10.0.0.1
wwsh node set n0000 --netdev=eth0 --netmask=255.255.255.0
wwsh node set --groupadd=mygroup,hello,bye --cluster=mycluster n0000
wwsh node set --groupdel=bye --set=vnfs=sl6.vnfs
wwsh node list xx:xx:xx:xx:xx:xx --lookup=hwaddr
wwsh node print --lookup=groups mygroup hello group123
wwsh node clone n0000 new0000
wwsh node set --enabled=false n0000

wwsh object [ modify | print | delete | dump | canonicalize ]

wwsh object print -p :all
Wwsh object print -p _id,name,_type

wwsh provision [ set | list | print ]

wwsh provision set n000[0-4] --bootstrap=2.6.30-12.x86_64
wwsh provision set n00[00-99] --fileadd=ifcfg-eth0
wwsh provision set -l=cluster mycluster --vnfs=rhel-6.0
wwsh provision set -l=group mygroup hello group123
wwsh provision set n00[0-4] --console=ttyS1,57600 --kargs="noacpi"
wwsh provision list n00[00-99]

```
