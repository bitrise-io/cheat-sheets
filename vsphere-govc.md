# govc

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
