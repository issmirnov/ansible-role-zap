
## Commands

```
# ubuntu
ansible-role-tester run --distribution ubuntu1804 --name zap
ansible-role-tester test --name zap --playbook tests/playbook-nginx.yml
ansible-role-tester destroy --name zap

# centos
ansible-role-tester run --distribution centos7 --name zap2
ansible-role-tester test --name zap2 --playbook tests/playbook-nginx.yml
ansible-role-tester destroy --name zap2
```
