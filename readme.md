## Install Dependuncies 
`pip install -r requirements-azure.txt`

## Setup Auth file
 - create cred file `~/.azure/credentials` 

```
[defaults]
subscription_id=""
client_id=""
secret=""
secretId=""
tenant = ""

```
## Run Ansible playbooks

- Run Windows Playbook

```
ansible-playbook rehlVM.yml
ansible-playbook winVM.yml
```
## Delete all Resources created by both playbooks

```
ansible-playbook removeAll.yml
```
## Vars files 
1. both playbooks have vars file `rehlvars.yml and winvars.yml`
2. update variable `user` and `pass` value
3. Virtual Machine name `vm_name`
4. For VM Size: `vm_size`
5. OS Images: `image` 

## Solving connection error for first run on windows
**Error Message**
```
UNREACHABLE! => {"changed": false, "msg": "ntlm: HTTPSConnectionPool(host='20.187.*.*', port=5986): Max retries exceeded with url: /wsman (Caused by ConnectTimeoutError(<urllib3.connection.VerifiedHTTPSConnection object at 0x7f7eee3dd520>, 'Connection to 20.187.*.* timed out. (connect timeout=30)'))", "unreachable": true}
```
**Execute PS1 Script as Admin this step is only required only once**

1. Copy Script to `C:\Users\tim\`
2. Open Poweshell as Admin
3. `C:\Users\tim\ConfiguringRemotingForAnsible.ps1`
4. Re-Run Playbook 

**NOTE: Re-Running PLaybook will not create another VM**

To Create new VM change VM name using vars file






