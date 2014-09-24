# Using Vagrant With Parallels Desktop #

A simple skeleton of Django application provisioned with Vagrant + Parallels Desktop. This example is for beginners that need some starting ground to experiment with.

Contents:

* A ```Vagrantfile``` containing virtual machine settings
* ```install_packages.sh``` is called after creating the VM to install additional software
* ```requirements.txt``` specifies which Python packages to install


## Getting Started ##

First, [install Vagrant](http://www.vagrantup.com/downloads.html). Then use the built in plugin manager to install Parallels Desktop compatibility module:

```bash
vagrant plugin install vagrant-parallels
```

Then get the sample code: 

```bash
git clone https://github.com/Parallels/vagrant-django-example.git
cd vagrant-django-example
```

Now, to produce the virtual machine:

```bash
vagrant up --provider=parallels
```

The only thing left is to create a Django project and start a HTTP server.

```bash
vagrant ssh

#(then, within the SSH session:)
django-admin.py startproject vagrant_django .
nohup python manage.py runserver [::]:8000 >&/dev/null &
exit
```

Now if you point your browser to [http://localhost:8000](http://localhost:8000), you'll see a fresh Django installation.