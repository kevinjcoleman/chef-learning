# In this directory you will need your chef server key and your `knife.rb` configuration.

### Example knife.rb
```
# See http://docs.chef.io/config_rb_knife.html for more information on knife configuration options

current_dir = File.dirname(__FILE__)
log_level                :info
log_location             STDOUT
node_name                "#{username}"
client_key               "#{current_dir}/#{username}.pem"
chef_server_url          "https://api.chef.io/organizations/#{org-name}"
cookbook_path            ["#{current_dir}/../cookbooks"]
```
