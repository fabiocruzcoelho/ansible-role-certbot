<h1 align="center">Welcome to role certbot 👋</h1>
<p>
  <a href="https://gitlab.com/estudosdevops/ansible/roles/certbot/-/commits/master">
  <img alt="pipeline status" src="https://gitlab.com/estudosdevops/ansible/roles/certbot/badges/master/pipeline.svg" /></a>
  <img alt="Version" src="https://img.shields.io/badge/version-0.1.0-blue.svg?cacheSeconds=2592000" />
  <a href="https://gitlab.com/estudosdevops/ansible/roles/certbot/-/blob/master/README.md" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
  <a href="https://gitlab.com/estudosdevops/ansible/roles/certbot/-/raw/master/LICENSE" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg" />
  </a>
  <a href="https://twitter.com/fcruzcoelho" target="_blank">
    <img alt="Twitter: fcruzcoelho" src="https://img.shields.io/twitter/follow/fcruzcoelho.svg?style=social" />
  </a>
</p>

> Installs and configures Certbot (for Let's Encrypt with nginx and cloudflare_dns).

## Install

- requirements.yml

```yml
---
- name: certbot
  src: fabiocruzcoelho.certbot
```

```sh
ansible-galaxy install -r requirements.yml
```

## Role Variables

Available variables are along with default values see: [defaults/main.yml](https://gitlab.com/estudosdevops/ansible/roles/certbot/-/blob/master/defaults/main.yml)

## Examplo playbook

```yml
---
- name: Lint it
  hosts: all
  gather_facts: yes
  become: yes
  vars:
    certbot_letsencrypt_create_if_missing: true
    zone: example.com
    email: janedoe@example.com
    token: 72d9c6c562bd8084509de315d37d6124636

  tasks:
    - name: Lint role certbot
      include_role:
        name: certbot
      vars:
        certbot_cloudflare_dns_zone: "{{ zone }}"
        certbot_cloudflare_dns_api_token: "{{ token }}"
        certbot_cloudflare_dns_email: "{{ email }}"
        certbot_cloudflare_dns_value_ip: "200.200.200.1"
        certbot_cloudflare_dns_record:
          - "*"
          - example.com
        certbot_certs:
          - domains:
              - "*.example.com"
              - example.com
```

## Run tests

> Dependence

- [cloudflare-api-token](https://support.cloudflare.com/hc/pt-br/articles/200167836-Gerenciamento-de-tokens-e-chaves-da-API)

- [ansible-role-tester](https://github.com/fubarhouse/ansible-role-tester)

```sh
git clone https://gitlab.com/estudosdevops/ansible/roles/certbot.git
```

```sh
make test
```

## Author

👤 **Fabio Coelho**

* Twitter: [@fcruzcoelho](https://twitter.com/fcruzcoelho)
* Github: [@fabiocruzcoelho](https://github.com/fabiocruzcoelho)
* LinkedIn: [@fcruzcoelho](https://linkedin.com/in/fcruzcoelho)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!
<br />Feel free to check [issues page](https://gitlab.com/estudosdevops/ansible/roles/certbot/-/issues).

## Show your support

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2020 [Fabio Coelho](https://github.com/fabiocruzcoelho).<br />
This project is [MIT](https://pt.wikipedia.org/wiki/Licen%C3%A7a_MIT) licensed.

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
