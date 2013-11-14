# Homegrown Ansible playbooks

Tested on Ubuntu 12.04 using Vagrant with the LXC provider plugin. Laptop provisioning tested on ElementaryOS 0.2 "Luna".

## Provision an ElementaryOS development laptop

    # 1. add "localhost" to /etc/ansible/hosts
    # 2. install "ssh" package
    # 3. $ ansible-playbook -vv --ask-pass --ask-sudo-pass developer.yml
    ---
    - hosts: localhost
      tasks:
        - include: ~/ansible-playbooks/tasks/build.yml    
        - include: ~/ansible-playbooks/tasks/desktop.yml
        - include: ~/ansible-playbooks/tasks/dotfiles.yml
        - include: ~/ansible-playbooks/tasks/ruby.yml
        - include: ~/ansible-playbooks/tasks/elementaryos.yml    

        - name: ensure console packages installed
          apt: pkg={{ item }} state=latest
          with_items:
            - mc
            - ranger
            - tmux
            - xclip

### Warning

Some packages require user interaction to confirm EULAs. So, must be installed manually:

- oracle-java7-installer
- ttf-mscorefonts-installer

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

Copyright (c)2013 [Cristian R. Arroyo](mailto:cristian.arroyo@vivaserver.com)
