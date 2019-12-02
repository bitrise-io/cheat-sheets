# govc

Links:

- govc: https://github.com/vmware/govmomi/tree/master/govc
- govc Usage guide: https://github.com/vmware/govmomi/blob/master/govc/USAGE.md
- Practical intro guide: https://prefetch.net/blog/2017/12/19/managing-vsphere-from-the-linux-command-line/

## Checking vSphere tasks

```shell
# print tasks
govc tasks

# print & follow tasks:
govc tasks -f

# check (follow) filtering for just the tasks including "error"
govc tasks -f | grep -i 'error'

# check tasks related to a specific VM/Template, e.g. all the VM clones from this specified VM
# for VMs the path has to start with vm/ followed by the path of the VM (folder1/subfolder/.../vmname)
#  the same format you get in the results/output of "govc find vm ..."
govc tasks -f vm/PATH/TO/SOURCE-VM
```

## List files on a datastore

```shell
govc datastore.ls -ds=DataStoreName
```

## Delete a file from a datastore

```shell
# to delete a complete folder
govc datastore.rm -ds=DataStoreName folder-name
```

## Find a VM by pattern in its name

```shell
govc find vm -name '*case-sensitive-pattern*'

# a more complex example
govc find 'vm/path/to/folder' -type VirtualMachine -name 'prefix-*-pattern*'
```

## List all VMs

```shell
govc find 'vm/' -type VirtualMachine
```

## Print infos about an object

```shell
# info about a specific VM
govc vm.info path/of/vm

# info about all datastores
govc datastore.info
# info about a specific one
govc datastore.info DataStoreName

# info about datacenters
govc datacenter.info
# info about a specific one
govc datacenter.info DatacenterName
```

## Attach a tag to a VM or to multiple VMs

```shell
# find the VM and its full path:
govc find vm -name '*some-pattern-*'
# attach THE-TAG to the VM
govc tags.attach THE-TAG "/vm/PATH/TO/VM"

# or to attach the tag to multiple VMs:
govc find vm -name '*some-pattern-*' > /tmp/vmlist
# will find all the VMs and write the list into /tmp/vmlist
# now inspect the /tmp/vmlist file
cat /tmp/vmlist
# if the list is good (make sure it only includes the VMs you expect it to include!!)
# you can attach the tags to all of them via:
cat /tmp/vmlist | xargs -I {} govc tags.attach THE-TAG {}
```
