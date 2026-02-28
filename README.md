# noobient.selinux_cil

## Synopsys

This role lets you install SELinux CIL policies.

## Parameters

| Name | Required | Example | Description |
|---|---|---|---|
| `module` | yes | `noobient-nginx` | Module filename in your `templates` directory without the `.j2` suffix. |
| `custom_src` | no | `my-module-template` | Use `<custom_src>.cil.j2` as the template file instead of the default `<module>.cil.j2`. Useful when creating multiple modules from the same template file. |
| `semodule_dir` | no | `/opt/selinux/modules` | Use custom directory for the installed SELinux modules instead of the default `/usr/local/etc/selinux/modules`. |

## Examples

```yml
- include_role:
    name: noobient.selinux_cil
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
| AlmaLinux 10 | ✅ | [![AlmaLinux 10](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/almalinux-10.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/almalinux-10.yml) |
| Fedora 42 | ✅ | [![Fedora 42](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/fedora-42.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/fedora-42.yml) |
| Fedora 43 | ✅ | [![Fedora 43](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/fedora-43.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-selinux_cil/actions/workflows/fedora-43.yml) |
| Ubuntu 22.04 | ❌ | N/A |
| Ubuntu 24.04 | ❌ | N/A |
| Ubuntu 26.04 | ❌ | N/A |
