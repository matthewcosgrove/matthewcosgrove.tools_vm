![Collection Molecule Tests](https://github.com/matthewcosgrove/ansible-collection-tools_vm/workflows/Collection%20Molecule%20Tests/badge.svg) ![BUCC Tools Role Molecule Tests](https://github.com/matthewcosgrove/ansible-collection-tools_vm/workflows/BUCC%20Tools%20Role%20Molecule%20Tests/badge.svg)

# Ansible Collection - matthewcosgrove.tools_vm

An opinionated way to set up a Tools VM. Initially for Ubuntu 18.04 only.

## Development prereqs

Initial installs (for Ubuntu, adapt for other OSs)

```
sudo apt install python3-venv
```

General Set Up

```
# cd into the root of this repo then
pip3 install pre-commit
pre-commit install
python3 -m venv .venv
source .venv/bin/activate
docker --version
pip3 install -U setuptools pip ansible ansible-lint yamllint 'molecule[docker]'
molecule --version
molecule --debug test
```
