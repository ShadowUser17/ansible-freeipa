### Scenarios for testing FreeIPA stand...

#### URLs:
- [ansible-lint](https://github.com/ansible/ansible-lint/releases)
- [ansible-core](https://github.com/ansible/ansible/releases)
- [ansible-freeipa](https://galaxy.ansible.com/ui/repo/published/freeipa/ansible_freeipa/docs/)

#### Install Ansible:
```bash
python3 -m venv --upgrade-deps env && \
./env/bin/pip3 install -r requirements.txt
```
```bash
./env/bin/ansible-galaxy collection install freeipa.ansible_freeipa
```

#### Create user:
```bash
ipa user-add ansible --first='Ansible' --last='Admin' --shell='/bin/bash'
```
```bash
ipa passwd ansible
```
```bash
ipa user-mod ansible --setattr='krbPasswordExpiration='
```
```bash
ipa group-add-member admins --users='ansible'
```

#### Run Playbook:
```bash
./env/bin/ansible-playbook -i <inventory> -t <tags> -e <extra-vars> -l <hosts-limit> <playbook>
```

#### Test Playbook:
```bash
./env/bin/ansible-playbook -i <inventory> -C <playbook>
```
