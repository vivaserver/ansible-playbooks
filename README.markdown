# Homegrown Ansible playbooks for fun and profit

Tested on Ubuntu 12.04 using Vagrant with the LXC provider plugin.

## Sample usage

Have a `provisioning/project.yaml` file in your Vagrant directory with the following contents:

    ---
    - hosts: all
      handlers:
      - include: handlers/lamp.yml
      tasks:
      - include: tasks/lamp.yml
      - include: tasks/phpmyadmin.yml
      - include: tasks/dotfiles.yml

Now include it in your `Vagrantfile` as a provider:

    config.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/project.yml"
      ansible.verbose = 'vv'
    end

## References

* [Insanely complete Ansible playbook, showing off all the options][gst]
* [Provisioning with Ansible and Vagrant][scl]
* [Simple LAMP using Ansible][git] 

[git]: https://github.com/ansible/ansible-examples/tree/master/lamp_simple
[scl]: http://julien.ponge.org/blog/scalable-and-understandable-provisioning-with-ansible-and-vagrant/
[gst]: https://gist.github.com/marktheunissen/2979474
