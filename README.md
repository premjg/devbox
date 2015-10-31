# Immutable Dev Environment #

This is a repo that I personally use to automate my dev environemnts.
The set up is powered by [Ansible](http://docs.ansible.com/ansible)
It has support for setting up stuff on my local mac, a vagrant-powered Ubuntu vitualbox (which is my primary dev environment) and also support for setting up a dev environment in the cloud.

The basic idea is that the tools and infrastructure contained in the dev environment are cleanly separated from the actual workspace (where your actual code lives).
You should be able to safely destroy the environment/ rebuild it/upgrade it without losing any of your work.
All the scripts are designed to be re-entrant and/or idempotent and should not have side-effects if run multiple times.

### I just want to automate my dev environemnt on Mac ###

* Clone this repo
* Edit the `inventory` file under the `[mac]` section if required
* Take a look at the `stack/mac.yml`
* Add/edit relevant `tasks`, `scripts`, `templates` under `stack/roles/mac/`
* Hint: This is what kicks off all the tasks: `stack/roles/mac/tasks/main.yml`
* Run

    ```sh
        ansible-playbook stack/mac.yml -i inventory
    ```

### I :heart: Ubuntu ###

* Clone this repo
* Download [Ansible Core](http://docs.ansible.com/ansible/intro_installation.html#getting-ansible)
* Download [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
* Inspect the `Vagrantfile` and see if it makes sense.
* Edit the `inventory` file under the `[dev-box]` section if required
* Take a look at the `stack/dev-box.yml`
* Add/edit relevant `tasks`, `scripts`, `templates` under `stack/roles/dev-box/`
* Hint: This is what kicks off all the tasks: `stack/roles/dev-box/tasks/main.yml`
* Run `vagrant up`
* Run

    ```sh
        ansible-playbook stack/dev-box.yml -i inventory
    ```
* Grab a cup of coffee and wait while your awesome devbox comes to life.
* `vagrant ssh` when you want to get into the box.


### I :heart: the :cloud: (Incomplete)###

* Clone this repo
* Edit the `inventory` file under the `[cloud-box]` section
* Take a look at the `stack/cloud-box.yml`
* Add/edit relevant `tasks`, `scripts`, `templates` under `stack/roles/cloud-box/`
* Hint: This is what kicks off all the tasks: `stack/roles/cloud-box/tasks/main.yml` 
* Run

    ```sh
        ansible-playbook stack/cloud-box.yml -i inventory
    ```
* Grab a cup of coffee and wait while your awesome cloud dev environment comes to life.
* `ssh` into your cloud box when ready.

* * *

## License

MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
