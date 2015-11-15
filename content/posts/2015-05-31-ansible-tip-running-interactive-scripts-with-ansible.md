+++
author = "Jeremy Brown"
categories = ["Blog Posts", "Developer", "Technology"]
date = "2015-05-31"
dsq_thread_id = [3808905472]
layout = "post"
tags = ["ansible"]
title = "Ansible Tip: Running Interactive Scripts with Ansible"
url = "/2015/05/31/ansible-tip-running-interactive-scripts-with-ansible/"

+++

Some­times when you run a script with Ansi­ble it requires an inter­ac­tive prompt like y/n or some­thing similar.

I recently ran into this prob­lem and after a bit of head bash­ing I found the fol­low­ing solu­tion in a lit­tle Linux util­ity called ‘yes’ which repeat­edly out­puts a line with a spec­i­fied STRING(s), or ‘y’. In this case I just needed ‘y’ so I went with the default.

Here is my Ansi­ble Task file with the ‘yes’ com­mand in use:

```
---
# file: roles/apigee_edge_base/tasks/apigee_install.yml
#

# slight hack below we pipe the "yes" command to send a y to our installer script because it complains about the OS version not being supported!
#
- name: Apigee Install - Run the apigee-install.sh shell script to setup the environment
 shell: yes | ./apigee-install.sh -r /opt -d /opt -j /usr/java/default
 args:
 chdir: "{{ unpack_dir }}/apigee-edge-{{ edge_version }}"
 remote_user: root
 sudo: yes

```

If you know a more ele­gant way to do this then let me know (I thought about ‘echo y |’ as well but liked this one).
