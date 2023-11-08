# noobient.selinux_cil

## Synopsys

This role lets you install SELinux CIL policies.

## Parameters

| Name | Required | Example | Description |
|---|---|---|---|
| `module` | yes | `noobient-nginx` | Module filename in your `templates` directory without the `.j2` suffix. |

## Examples

```yml
- include_role:
    name: bviktor.selinux_cil
  vars:
    module: noobient-nginx
```

`noobient-nginx.j2`:

```
; Allow httpd_t to serve requests at all
(allow httpd_t http_port_t (tcp_socket (name_connect)))
; Allow httpd_t to connect to MySQL
(allow httpd_t mysqld_port_t (tcp_socket (name_connect)))
; Allow httpd_t to proxy upstream servers
(allow httpd_t http_cache_port_t (tcp_socket (name_connect)))
```

## Return Values

N/A

## Support

| Platform | Support | Status |
|---|---|---|
| Linter | ✅ | [![Lint](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/lint.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/lint.yml) |
| AlmaLinux 8 | ✅ | [![AlmaLinux 8](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/almalinux-8.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/almalinux-8.yml) |
| AlmaLinux 9 | ✅ | [![AlmaLinux 9](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/almalinux-9.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/almalinux-9.yml) |
| Fedora 37 | ✅ | [![Fedora 37](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/fedora-37.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/fedora-37.yml) |
| Ubuntu 18.04 | ❌ | N/A |
| Ubuntu 20.04 | ❌ | N/A |
| Ubuntu 22.04 | ❌ | N/A |
