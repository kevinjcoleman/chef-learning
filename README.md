Bootstrap a node:
`knife bootstrap ADDRESS --ssh-user USER --sudo --identity-file IDENTITY_FILE --node-name NODE_NAME --run-list 'recipe[RECIPE NAME]'`
ex
`knife bootstrap ADDRESS --ssh-user ubuntu --sudo --identity-file ~/.ssh/personal-aws-keys.pem --node-name app1 --run-list 'recipe[learn_chef_apache2]'`

Update a chef config on a specific node:
`knife ssh 'name:node1-ubuntu' 'sudo chef-client' --ssh-user USER --identity-file IDENTITY_FILE --attribute ipaddress`
ex
`knife ssh 'name:node1-ubuntu' 'sudo chef-client' --ssh-user ubuntu --identity-file ~/.ssh/personal-aws-keys.pem`
