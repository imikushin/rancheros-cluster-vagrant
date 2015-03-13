# RancherOS Cluster on Vagrant

Quickly deploy a multi-VM RancherOS cluster on Vagrant/VirtualBox.


## Getting started
1.) Install dependencies

* Virtualbox (Tested with 4.3.24)
* Vagrant (Tested with 1.7.2)

2.) Clone this project

```
git clone https://github.com/rancherio/os-vagrant.git
cd os-vagrant
```

3.) Up and Running

```
vagrant up
vagrant ssh node-01
vagrant ssh node-02
...
```

Start running Docker like you usually would!

## Upgrading RancherOS Versions

To upgrade the Vagrant box, refresh this repository from master.



### Customizing and configuring


To get a feel for how things work under the hood checkout the
[RancherOS Repo](https://github.com/rancherio/os) for details.

# License
Copyright (c) 2014-2015 [Rancher Labs, Inc.](http://rancher.com)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

