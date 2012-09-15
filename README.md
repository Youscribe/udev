Description
===========
Manages changing settings for udev configuration. Currently only only supports configuring network device ordering at boot.

Recipes
=======

net
---
Populates the `/etc/udev/rules.d/70-persistent-net.rules` with the `['udev']['net']` hash, with keys of ethernet devices (ie. 'eth0') and values of mac addresses.


Usage
=====
Set the `['udev']['net']` hash with the eth devices in the order desired with their mac addresses. Upon reboot, the ordering will take effect. Works well with the `pxe_dust` cookbook to set the order while provisioning the operating system.

Here is an example role:

```ruby
name "udev"
description "Configure udev"
run_list(
  "recipe[udev::net]"
  )
default_attributes(
  "udev" => {
    "net" => {
      "eth0" => "00:0c:29:49:84:33",
      "eth1" => "00:0c:29:49:84:29"
    }
  })
```

License and Author
==================

Author:: Matt Ray (<matt@opscode.com>)

Copyright 2012 Opscode, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

