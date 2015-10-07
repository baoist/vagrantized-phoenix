## General Stack

- [Elixir]
- [Phoenix]

[Elixir]: http://elixir-lang.org/
[Phoenix]: http://www.phoenixframework.org/

## Getting Started

You will need to initialize your phoenix app at the base of `./src/`.

Replace the variables `APP_NAME` in [Vagrantfile](./vagrant/Vagrantfile)
and the various variables in [application.yml](./vagrant/ansible/vars/application.yml).
Then continue.

You'll need to install [VirtualBox][], [Vagrant][], and [Ansible][]
first. VirtualBox and Vagrant both have Mac OS X installer packages, and
Ansible can be installed either with Homebrew or with pip, the Python
package manager.

[VirtualBox]: https://www.virtualbox.org/wiki/Downloads
[Vagrant]: http://www.vagrantup.com/downloads.html
[Ansible]: http://docs.ansible.com/intro_installation.html

Once you've got those installed, you can bootstrap the project with:

    $ cd vagrant && vagrant up

This will create the box, install the gems, create the database (if it
doesn't already exist), and start the app inside the box. To access it,
add an entry in your /etc/hosts file like the following (or do the
equivalent in dnsmasq.conf):

    192.168.100.23 ampifiu.local

You can then visit <http://ampifiu.local/>.

The app will be started inside a detached [`screen(1)`][screen] session
inside the Vagrant box. To access it, run `vagrant ssh` and answer 'y'
when prompted to resume the `screen(1)` session.

[screen]: http://www.gnu.org/software/screen/

To re-run the provisioning scripts, which are idempotent, you can simply do:

    $ vagrant provision

This should bring the box back into its correct configuration if
anything has gotten messed up.
