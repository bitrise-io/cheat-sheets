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
