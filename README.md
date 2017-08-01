## Working with a node

### Bootstrap a node:
```
knife bootstrap ADDRESS --ssh-user USER --sudo --identity-file IDENTITY_FILE --node-name NODE_NAME --run-list 'recipe[RECIPE NAME]'
```
#### EX

```
knife bootstrap ADDRESS --ssh-user ubuntu --sudo --identity-file ~/.ssh/personal-aws-keys.pem --node-name app1 --run-list 'recipe[learn_chef_apache2]'
```

### Update a chef config on a specific node:
```
knife ssh 'name:node1-ubuntu' 'sudo chef-client' --ssh-user USER --identity-file IDENTITY_FILE --attribute ipaddress
```
#### EX
```
knife ssh 'name:node1-ubuntu' 'sudo chef-client' --ssh-user ubuntu --identity-file ~/.ssh/personal-aws-keys.pem
```

### Add runlist/role to node
```
knife node run_list set NODE "role[NAME]"
```
#### EX
```
knife node run_list set node1-ubuntu "role[web]"
```

### View nodes runlist
```
knife node show node1-ubuntu --run-list
```

## Roles

### Create a new role
```knife role from file roles/ROLENAME.json```

Ex role config json
```
{
   "name": "web",
   "description": "Web server role.",
   "json_class": "Chef::Role",
   "default_attributes": {
     "chef_client": {
       "interval": 300,
       "splay": 60
     }
   },
   "override_attributes": {
   },
   "chef_type": "role",
   "run_list": ["recipe[chef-client::default]",
                "recipe[chef-client::delete_validation]",
                "recipe[learn_chef_apache2::default]"
   ],
   "env_run_lists": {
   }
}
```
### List roles
```
knife role list
```

### Show roles
```
knife role show web
```

### Run configuration on all nodes in a role
```
knife ssh 'role:web' 'sudo chef-client' --ssh-user vagrant --identity-file ~/.ssh/private_key --attribute ipaddress
```

### Check all roles status'
```
knife status 'role:web' --run-list
```

## Other common commands

### List nodes
```knife node list```

### Get data on specific node
```knife node show NODE```

### Update a cookbook
```knife cookbook upload COOKBOOK```

### Generate a cookbook
```chef generate cookbook cookbooks/COOKBOOK```

### Download external cookbooks
```berks install```

### Upload external cookbooks
```berks upload```


## Cookbook details
### RVM Config
https://supermarket.chef.io/cookbooks/rvm#readme
