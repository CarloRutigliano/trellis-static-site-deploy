Static site deploy
=========

Deploy a static site with trellis.

Requirements
------------

This role needs to run after https://github.com/CarloRutigliano/trellis-static-site-setup.git role.

Usage
------------

git clone in trellis/roles folder
Add group_vars/{env}/static_sites.yml file with your sites conf.

```
static_sites:
  example.com:
    site_hosts:
      - canonical: example.com
        redirects:
          - www.example.com
    local_path: ../static # path targeting local site directory (relative to Ansible root)
    repo: git@bitbucket.org:itoshi/server.git # replace with your Git repo URL
    repo_subtree_path: static # relative path to your static site directory in your repo
    branch: dev
    ssl:
      enabled: false
      provider: self-signed
```
In trellis/deploy.yml playbook use trellis-static-site-deploy role instead of deploy when deploying static_sites

Heavily inspired by trellis deploy role (mostly a copy without wordpress related stuff)

License
-------

MIT

Author Information
------------------

rutiglianocarlo@gmail.com
