[![Collection Molecule Tests](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/workflows/Collection%20Molecule%20Tests/badge.svg)](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22Collection+Molecule+Tests%22)
[![BUCC Tools Role Molecule Tests](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/workflows/BUCC%20Tools%20Role%20Molecule%20Tests/badge.svg)](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22BUCC+Tools+Role+Molecule+Tests%22)
[![Hashicorp Tools Role Molecule Tests](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/workflows/Hashicorp%20Tools%20Role%20Molecule%20Tests/badge.svg)](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22Hashicorp+Tools+Role+Molecule+Tests%22)
[![Vim Role Molecule Tests](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/workflows/Vim%20Role%20Molecule%20Tests/badge.svg)](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22Vim+Role+Molecule+Tests%22)
[![Ubuntu User Role Molecule Tests](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/workflows/Ubuntu%20User%20Role%20Molecule%20Tests/badge.svg)](https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22Ubuntu+User+Role+Molecule+Tests%22)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-tools__vm-blue)](https://galaxy.ansible.com/matthewcosgrove/tools_vm)

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

1) Create a release with the next logical semantic version number using convention (see NOTE below) of prefix with letter v e.g. `v1.1.0` via https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/releases/new 
2) Check nothing went wrong https://github.com/matthewcosgrove/matthewcosgrove.tools_vm/actions?query=workflow%3A%22Ansible+Galaxy%22

NOTE: The version of `galaxy.yml` is incremented dynamically as part of the GitHub Actions release. It is not currently persisted anywhere, but the version comes from the tag name so the convention above for semantic versioning is essential. It must be a tag called vMAJOR.MINOR.PATCH e.g. `v1.1.0`. See the script used [here](.github/scripts/tag_version.sh)
