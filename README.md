## What is ansible-dnsmasq?

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

## License

MIT