# Ansible Collection - iac.lab4
Коллекция с ролью ovenvpn и тестированием через molecule(как в [официальном мануале molecule](https://ansible.readthedocs.io/projects/molecule/getting-started/)).

Установка openvpn с помощью скрипта [openvpn-install](https://github.com/Nyr/openvpn-install)

## Тестирование роли openvpn через molecule
```
[~/dev/itmo/infra/iac/lab4/extensions]$ molecule test
WARNING  Driver vagrant does not provide a schema.
INFO     default scenario test matrix: dependency, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun with role_name_check=0...
INFO     Running default > dependency
WARNING  Skipping, missing the requirements file.
WARNING  Skipping, missing the requirements file.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy

PLAY [Destroy] *****************************************************************

TASK [Populate instance config] ************************************************
ok: [localhost]

TASK [Dump instance config] ****************************************************
skipping: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Running default > syntax

playbook: /home/svt/dev/itmo/infra/iac/lab4/extensions/molecule/default/converge.yml
INFO     Running default > create

PLAY [Create] ******************************************************************

TASK [Populate instance config dict] *******************************************
skipping: [localhost]

TASK [Convert instance config dict to a list] **********************************
skipping: [localhost]

TASK [Dump instance config] ****************************************************
skipping: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=0    changed=0    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0

INFO     Running default > prepare

PLAY [Prepare] *****************************************************************

TASK [Gather system info] ******************************************************
ok: [srv1]

TASK [Bootstrap python for Ansible] ********************************************
ok: [srv1]

PLAY RECAP *********************************************************************
srv1                       : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running default > converge

PLAY [Converge] ****************************************************************

TASK [Include openvpn role] ****************************************************
included: openvpn for srv1

TASK [openvpn : Download sources] **********************************************
ok: [srv1]

TASK [openvpn : Check if openvpn installed already] ****************************
ok: [srv1]

TASK [openvpn : Install openvpn] ***********************************************
skipping: [srv1]

TASK [openvpn : Start openvpn] *************************************************
ok: [srv1]

TASK [openvpn : Copy ovpn file to playbook directory] **************************
ok: [srv1]

PLAY RECAP *********************************************************************
srv1                       : ok=5    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Running default > idempotence

PLAY [Converge] ****************************************************************

TASK [Include openvpn role] ****************************************************
included: openvpn for srv1

TASK [openvpn : Download sources] **********************************************
ok: [srv1]

TASK [openvpn : Check if openvpn installed already] ****************************
ok: [srv1]

TASK [openvpn : Install openvpn] ***********************************************
skipping: [srv1]

TASK [openvpn : Start openvpn] *************************************************
ok: [srv1]

TASK [openvpn : Copy ovpn file to playbook directory] **************************
ok: [srv1]

PLAY RECAP *********************************************************************
srv1                       : ok=5    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Idempotence completed successfully.
INFO     Running default > side_effect
WARNING  Skipping, side effect playbook not configured.
INFO     Running default > verify
INFO     Running Ansible Verifier
WARNING  Skipping, verify action has no playbook.
INFO     Verifier completed successfully.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy

PLAY [Destroy] *****************************************************************

TASK [Populate instance config] ************************************************
ok: [localhost]

TASK [Dump instance config] ****************************************************
skipping: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Pruning extra files from scenario ephemeral directory
```
