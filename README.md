Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

---
# ansible-playbook /home/devekko/Projects/ansible-aegir3-php7/aegir3-platforms-install-playbook.yml --ask-become-pass -i ~/ansible_hosts -vvvv
# ansible-playbook aegir3-platforms-install-playbook.yml --ask-become-pass -i ~/ansible_hosts -vvvv
#

#
# https://github.com/PraxisLabs/praxis_aegirvps_ansible/blob/master/roles/auto-deploy/tasks/main.yml

- hosts: auto-deploy-goo
  remote_user: root
  become: yes
  roles:
    - { role: ansible-role-aegir3platforms, platform_name: getopenoutreach, makefiles_repo: "https://github.com/PraxisLabs/getopenoutreach_makefiles.git", makefile_name: getopenoutreach.make, release_feed: "https://github.com/PraxisLabs/getopenoutreach_makefiles/releases.atom", tags: auto-deploy }

- hosts: auto-deploy-openatrium
  remote_user: root
  become: yes
  roles:
    - { role: ansible-role-aegir3platforms, platform_name: openatrium, makefiles_repo: "http://git.drupal.org/project/openatrium.git", makefile_name: build-openatrium.make, release_feed: "https://www.drupal.org/node/681432/release/feed", tags: auto-deploy }

- hosts: auto-deploy-civicrm
  remote_user: root
  become: yes
  roles:
    - { role: ansible-role-aegir3platforms, platform_name: civicrm, makefiles_repo: "https://github.com/PraxisLabs/civicrm_makefiles.git", makefile_name: build-civicrm.make, release_feed: "https://github.com/PraxisLabs/civicrm_makefiles/tags.atom", tags: auto-deploy }

- hosts: auto-deploy-drulenium
  remote_user: root
  become: yes
  roles:
    - { role: ansible-role-aegir3platforms, platform_name: drulenium, makefiles_repo: "https://github.com/ErgonLogicEnterprises/hosting_drulenium_drupal7_makefiles.git", makefile_name: hosting_drulenium_drupal7_makefiles.make, release_feed: "https://github.com/ErgonLogicEnterprises/hosting_drulenium_drupal7_makefiles/tags.atom", tags: auto-deploy }



 broken
- hosts: auto-deploy-rune
  become: yes
  roles:
    - { role: ansible-role-aegir3platforms, platform_name: rune, makefiles_repo: "https://github.com/poetic/rune.git", makefile_name: makefiles/stubs/build.make.yml, release_feed: "https://github.com/poetic/rune/tags.atom", tags: auto-deploy }

 drush dl needs own role
- hosts: ansible-role-aegir3platforms
  become: yes
  roles:
    - { role: ansible-role-aegir3platforms}

 broken php7
- hosts: auto-deploy-d8
  roles:
    - { role: auto-deploy, platform_name: drupal8, makefiles_repo: "https://github.com/PraxisLabs/drupal8_makefiles.git", makefile_name: drupal8.make, release_feed: "https://github.com/PraxisLabs/drupal8_makefiles/tags.atom", tags: auto-deploy }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
