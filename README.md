[![Agile611](https://www.agile611.com/wp-content/uploads/2020/09/cropped-logo-header.png)](http://www.agile611.com/)

# Agile611 ansible-awx-examples

A small collection of example Ansible playbooks, roles and an AWX demo application to demonstrate common patterns for provisioning and app deployment.

### Important

To install collections use the example `pip.yml` and add the collection to `collections/requirements.yml` in the `collections` folder.

**Repository layout**

- `play.yml`: top-level example playbook
- `ping.yml`, `collection_demo.yml`, `pip.yml`: small example playbooks
- `awx-demo-app/`: a small demo application with playbooks, roles and tests
- `collections/requirements.yml`: list of Ansible collections used by the examples

**Quick start**

1. (Optional) Create a virtualenv and activate it:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Install Python dependencies if any (some playbooks may use community modules):

```bash
pip install -r awx-demo-app/demo_app/files/demo/requirements.txt || true
```

3. Install Ansible collections listed in `collections/requirements.yml`:

```bash
ansible-galaxy collection install -r collections/requirements.yml
```

Note: This repository also includes an example `pip.yml` playbook. The intention is that you can add collection names to `collections/requirements.yml` and then use the `pip.yml` example if you prefer to install via an automation playbook.

**Run the example playbooks**

- Run the top-level demo playbook (adjust inventory as needed):

```bash
ansible-playbook -i hosts play.yml
```

- Run the AWX demo app site playbook:

```bash
ansible-playbook -i awx-demo-app/hosts awx-demo-app/site.yml
```

- Run a role's test playbook (examples available under each role `tests/` directory):

```bash
ansible-playbook -i awx-demo-app/mysql/tests/inventory awx-demo-app/mysql/tests/test.yml
```

**Folder descriptions**

- `awx-demo-app/`: contains a multi-role demo app with roles for `apache2`, `mysql`, `nginx`, and a small `demo_app` role. Each role follows common Ansible layout with `tasks/`, `handlers/`, `defaults/`, `vars/`, `meta/` and `tests/`.
- `collections/requirements.yml`: list of Ansible collections to install with `ansible-galaxy`.
- `pip.yml`: example playbook that can be used to install Python packages or drive installs from Ansible.

**Testing**

- Each role includes a `tests/` directory with a simple inventory and `test.yml` playbook. Run these locally to sanity-check roles.
- If you use Molecule, you can create Molecule scenarios per role (not included by default here).

**IMPORTANT TO GET COLLECTIONS FROM ANSIBLE GALAXY**

Add in Jobs Settings > Extra Environment Variables these values:

```bash
{
  "AWX_COLLECTIONS_ENABLED": "true",
  "AWX_ROLES_ENABLED": "true"
}
```

Additionally add in your `Organization` the parameter `Galaxy Credential` add your `Ansible Galaxy Credentials`

**Contributing**

- Add issues or pull requests with improvements or additional examples.
- Keep examples small and focused — they are intended as learning aids.

**License**

This tutorial is released into the public domain by [Agile611](http://www.agile611.com/) under Creative Commons Attribution-NonCommercial 4.0 International.

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC_BY--NC_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)


This README file was originally written by [Guillem Hernández Sola](https://www.linkedin.com/in/guillemhs/) and is likewise released into the public domain.

Please contact Agile611 for further details.

* [Agile611](http://www.agile611.com/)
* Laureà Miró 309
* 08950 Esplugues de Llobregat (Barcelona)