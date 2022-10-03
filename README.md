# Ansible Play: bitnami_renew_cert

### <sub-heading>

This play is for renewing a Let's Encrypt certificate installed using the bncert-tool or Lego tool.<br>
Reference: https://aws.amazon.com/premiumsupport/knowledge-center/lightsail-bitnami-renew-ssl-certificate/<br>
Tailored to my requirments for renewing the SSL certificate on my AWS Lightsail instance hosting wordpress.

## Requirements

community.general<br>
community.crypto

## Group Variables
Group variables defined in group_vars/all/cert_vars.yml
```shell
cert_email: <email> # The email used to register the certificate with LetsEncrypt
cert_domain: <domain> # The certificate domain registered with LetsEncrypt
cert_path: /opt/bitnami/letsencrypt/certificates/<domain>.crt
```

## Role Variables

Default role variables for the check_cert role are listed below (see ```defaults/main.yml```)
```shell
max_validity: 7 # maximum number of days of current certificate validity before renewal will be carried out
skip_check: no # carry out renewal regardless of current validity
```
## Dependencies

None

## Example Playbook
```yaml
    - hosts: all
      become: true
      roles:
        - check_cert
        - renew_cert
```

## License

MIT

## Author Information

This role was created in 2022 by [Lee Woodhouse](https://www.leewoodhouse.com/)
