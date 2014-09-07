## WARNING: This role will be deprecated very soon

All of the functionality provided by this role and more is available in the [DebOps project](http://debops.org). If you are using some of my roles in conjunction with each other, you will find the move to DebOps most pleasurable.

This role will be **removed** from the **galaxy** and from **github** anywhere from 42 microseconds to 2-3 weeks after you read this message.

---


## What is ansible-dnsmasq? [![Build Status](https://secure.travis-ci.org/nickjj/ansible-dnsmasq.png)](http://travis-ci.org/nickjj/ansible-dnsmasq)

It is an [ansible](http://www.ansible.com/home) role to install dnsmasq and configure it so that you can map a TLD to localhost.

### What problem does it solve and why is it useful?

When developing applications on your work station it is annoying to have to type http://localhost. If your application requires sub-domains then it is even more lame because you would have to edit your hosts file for each project and sub-domain.

This role allows you to map something like `*.dev` to localhost so you can access URLs like http://myapp.dev or http://foo.bar.dev in your browser without any further configuration.

## Role variables

```
---
# The TLD to use.
dnsmasq_tld: dev

# The amount in seconds to cache apt-update.
apt_cache_valid_time: 86400
```

## Example playbook

For the sake of this example let's say you have a group called **dev** and you have a typical `site.yml` file.

To use this role edit your `site.yml` file to look something like this:

```
---
- name: ensure devbox is configured
- hosts: localhost

  roles:
    - { role: nickjj.dnsmasq, tags: dnsmasq }
```

Let's say you want to edit the TLD, you can do this by opening or creating `group_vars/app.yml` which is located relative to your `inventory` directory and then making it look something like this:

```
---
dnsmasq_tld: staging

```

## Installation

`$ ansible-galaxy install nickjj.dnsmasq`

## Requirements

Tested on ubuntu 12.04 LTS but it should work on other versions that are similar.

## Ansible galaxy

You can find it on the official [ansible galaxy](https://galaxy.ansible.com/list#/roles/1047) if you want to rate it.

## License

MIT