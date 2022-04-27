# gcloud-magic

Useful gcloud commands (GCP CLI)

---
### List load balancers
```
$ gcloud compute forwarding-rules list
$ gcloud compute url-maps list
```

### List instance groups
```
$ gcloud compute instance-groups managed list
```

### List instances in nice box view 
```
gcloud compute routes list --filter="name=nat-gw" --format "[box]"
```

### List instances with extracted name and external IP address
```
gcloud compute instances list --filter "name~'nat'" --format="value(name,EXTERNAL_IP)"
```

### List routing
```
$ gcloud compute routes list
```

### List subnets
```
$ gcloud compute networks subnets list
```

### List instances sorted by internal IP address
```
$ gcloud compute instances list --sort-by=INTERNAL_IP
```

### Revert your SDK to the previously installed version
```
$ gcloud components update --version 323.0.0
```

### Remove deletion protection
```
$ gcloud compute instances update <instance_name> --no-deletion-protection
```

### Create Redis instance
```
$ gcloud redis instances create <redis_name> --size=1 --tier=standard --redis-version=redis_5_0 \
--region=europe-west3 --network=projects/<project_name>/global/networks/<vpc_name> \
--connect-mode=private-service-access --labels "frontend=redis,app=redis"
```

### Instance migration using snapshot

### List snapshots and details
```
gcloud compute snapshots list
gcloud compute snapshots describe <snapshot_name>
```

#### Create
```
time gcloud compute disks snapshot <instance_name>-1 --zone=europe-west4-b s-1-17-12-2019
```

#### Stop instance
```
gcloud compute instance stop <instance_name> --zone=europe-west4-b
```

#### Detaching disk of the instance
```
gcloud compute instance detach-disk <instance_name> --disk=srv-gol-02-1
```

#### Delete disk of instance
```
gcloud compute disk delete <instance_name>-1 --zone=europe-west4-b
```

#### Create new disk from previous snapshot of instance
```
time gcloud compute disks create <instance_name>-1 --source-snapshot <instance_name>-02-1-17-12-2019
```

#### Attach new disk to existing instance
```
gcloud compute instance attack-disk <instance_name> --disk <instance_name>-1
```

#### Running instance again
```
time gcloud compute instance start <instance_name>
```


