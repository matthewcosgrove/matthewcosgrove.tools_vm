![Collection Molecule Tests](https://github.com/matthewcosgrove/ansible-collection-tools_vm/workflows/Collection%20Molecule%20Tests/badge.svg) ![BUCC Tools Role Molecule Tests](https://github.com/matthewcosgrove/ansible-collection-tools_vm/workflows/BUCC%20Tools%20Role%20Molecule%20Tests/badge.svg)

# Ansible Collection - matthewcosgrove.tools_vm

An opinionated way to set up a Tools VM. Initially for Ubuntu 18.04 only.

## Development prereqs

Clone the repo into a location as required by `ANSIBLE_COLLECTIONS_PATHS` that enables running the molecule integration tests (See the env var set [here](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/blob/5282dccc78f6609d9967371cfa0a07cd3074dd12/molecule/default/molecule.yml#L20))

```
mkdir -p ~/collections/ansible_collections/matthewcosgrove/tools_vm && cd "$_"
git clone https://github.com/matthewcosgrove/matthewcosgrove.tools_vm.git
# for convenience
ln -s ~/collections/ansible_collections/matthewcosgrove/tools_vm/ ~/matthewcosgrove.tools_vm
```

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
```

## Testing

### Integration test of all roles via collection

```
# cd into the root of this repo then
molecule --debug test
```

### Individual role

```
# cd into role dir e.g.
cd ~/collections/ansible_collections/matthewcosgrove/tools_vm
molecule --debug test
```

## Release Process via GitHub Actions

1) Update the version in [galaxy.yml](galaxy.yml) e.g. `version: 1.1.0`
2) Create a release with the same version number using convention of prefix with letter v e.g. `v1.1.0` via https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/releases/new 
3) Check nothing went wrong https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22Ansible+Galaxy%22
