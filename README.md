# Ansible 'copyv' Plugin

This version should work with Ansible v2.0.x  I've not tested it extensively so YMMV.  If the folder structure and plugin detection is the same in Ansible v2.0.x then this plugin should work fine.

The code is based on this [Ansible PR](https://github.com/ansible/ansible/pull/13849).

The plugin for version v1.9.2 is available on [this branch](https://github.com/saygoweb/ansible-plugin-copyv/tree/master).

## TLDR;

### Install
Copy the two files in the folders action_plugins and library alongside your own main playbook files.  Ansible includes the `action_plugins` folder in the plugin search path.

Your folder structure should look like this:

    SomePlay.yml
    action_plugins/copyv.py
    library/copyv.py


### Use

    - name: Copy Some Secret File
      copyv: src="secret.txt" dest="/tmp/"

See test.yml for an example.

You can use anything that the [copy module](http://docs.ansible.com/copy_module.html) supports.

## References

There's a [Stack Overflow](https://stackoverflow.com/questions/22773294/how-to-upload-encrypted-file-using-ansible-vault) question relating to this issue which then leads to several issues and pull-requests in ansible, and ansible module repositories.

## Running test.yml

If you want to run the included test.yml you can do so with something like this:

    ansible-playbook -h hosts test.yml --ask-vault

The vault password is `test`.