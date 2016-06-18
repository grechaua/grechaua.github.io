---
layout: post
title:  "Install ansible on windows"
date:   2016-06-17 03:18:00 +0200
categories: windows
---
Install chocolatey package manager: [choco]

Install babun shell: 
`choco install babun -y`

Run following commands in babun.

Install required python packages:
`pact install python-paramiko python-crypto python-setuptools`

Install pip:
`python /usr/lib/python2.7/site-packages/easy_install.py pip`

Install ansible via pip:
`pip install ansible`

Check ansible and ansible-playbook installed:
`ansible --version && ansible-playbook --version`

[choco]: https://chocolatey.org/install