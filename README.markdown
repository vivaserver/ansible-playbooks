# Homegrown Ansible playbooks

Tested on Ubuntu 12.04 using Vagrant with the LXC provider plugin.
Laptop provisioning tested on ElementaryOS 0.2 "Luna".

## Provision an elementaryOS development laptop

Just execute the developer role against a local elementaryOS host:

    # 1. add "localhost" to /etc/ansible/hosts
    # 2. install "ssh" package
    # 3. $ ansible-playbook -vv -K --sudo developer.yml
    ---
    - hosts: localhost
      tasks:
        - name: ensure PPA repos addition supported
          apt: pkg=python-pycurl state=present
      roles:
        - developer

### Warning

Some packages require user interaction to confirm EULAs. So, must be installed manually:

- oracle-java7-installer
- ttf-mscorefonts-installer

## Extracted roles to Ansible Galaxy

- [ansible-lamp][glamp]
- [ansible-ioncube][glion]
- [ansible-plowshare][glplw]

[glamp]: https://github.com/vivaserver/ansible-lamp
[glion]: https://github.com/vivaserver/ansible-ioncube
[glplw]: https://github.com/vivaserver/ansible-plowshare

## References

* [Insanely complete Ansible playbook, showing off all the options][gst]
* [Provisioning with Ansible and Vagrant][scl]
* [Simple LAMP using Ansible][git] 

[git]: https://github.com/ansible/ansible-examples/tree/master/lamp_simple
[scl]: http://julien.ponge.org/blog/scalable-and-understandable-provisioning-with-ansible-and-vagrant/
[gst]: https://gist.github.com/marktheunissen/2979474

## License

Released under the [MIT License](http://www.opensource.org/licenses/MIT).

## Copyright

Copyright (c)2014 [Cristian R. Arroyo](mailto:cristian.arroyo@vivaserver.com)
