## govc

### Checking vSphere tasks

```shell
# print tasks
govc tasks

# print & follow tasks:
govc tasks -f

# check (follow) filtering for just the tasks including "error"
govc tasks -f | grep -i 'error'
```
