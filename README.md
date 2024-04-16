# user-domain
User Domain Initializer


## Pre-condition

This command is runnable in spacectl POD.
Login to spacectl POD and run the following command.

```bash
export SPACECTL_POD=$(kubectl get pod -n cloudforet | grep spacectl | awk '{print $1}')
kubectl exec -it -n cloudforet $SPACECTL_POD -- /bin/bash
```

## Get User domain script

```bash
git clone https://github.com/cloudforet-io/user-domain.git
cd user-doamin
```

## Edit your domain information

demo.yaml is a sample for new user domain

```yaml
import:
  - /root/user-domain/user_domain.yaml
  - /root/user-domain/create_role.yaml
  - /root/user-domain/add_statistics_schedule.yaml
var:
  domain:
    user: demo                              # domain name. for example, demo.console.example.com
  default_language: en                      # default language
  default_timezone: America/Los_Angeles     # default timezone
  domain_owner:
    id: admin
    password: Admin123!@#                   # domain owner password
  user:
    id: system_api_key
```

## Run the script

```bash
spacectl apply demo.yaml
```
