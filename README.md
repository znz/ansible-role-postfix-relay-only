# postfix with relayhost

- Setup postfix with relayhost

## Requirements

- Debian
- Ubuntu

## Role Variables

see defaults/main.yml

## Dependencies

None.

## Example Playbook

    ---
    - hosts: all
      sudo: yes
      roles:
      - role: znz.postfix-relay-only
        postfix_main_cf:
          compatibility_level: 2
          smtp_tls_security_level: "encrypt"
          smtp_tls_wrappermode: "no"
          smtp_sasl_auth_enable: "yes"
          smtp_sasl_password_maps: "hash:/etc/postfix/sasl/sasl_password"
          smtp_sasl_tls_security_options: "noanonymous"
          smtp_sasl_mechanism_filter: "login"
          smtp_tls_CApath: "/etc/ssl/certs/ca-certificates.crt"
        postfix_relay_smtp_server: "smtp.gmail.com"
        postfix_relay_smtp_port: 587
        postfix_relay_smtp_user: "my.email@gmail.com"
        postfix_relay_smtp_pass: "my-gmail-password"
        postfix_alias_root: "my.email@gmail.com"

## License

MIT License
