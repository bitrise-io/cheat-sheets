# govc

Practical intro guide: https://prefetch.net/blog/2017/12/19/managing-vsphere-from-the-linux-command-line/

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
