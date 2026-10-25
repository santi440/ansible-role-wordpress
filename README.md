# Role wordpress (Apache)

Instala y configura WordPress con Apache/PHP y una base de datos MySQL o
MariaDB. Soporta Debian, Ubuntu y Rocky Linux/CentOS/RHEL.

## Requisitos

- Ansible 2.15 o superior.
- El role `geerlingguy.mysql` para aprovisionar la base de datos.
- En RedHat se usa `php-fpm` con `proxy_fcgi`; en Debian/Ubuntu se usa
  `mod_php`.

## Variables principales

| Variable | Default | Descripción |
| --- | --- | --- |
| `wordpress_version` | `6.6.2` | Versión de WordPress (`latest` para la última). |
| `wordpress_install_dir` | `/var/www/wordpress` | Directorio de instalación. |
| `wordpress_domain` | `localhost` | `ServerName` del virtual host. |
| `wordpress_http_port` | `80` | Puerto HTTP de Apache. |
| `wordpress_db_name` | `wordpress` | Nombre de la base. |
| `wordpress_db_user` | `wp_user` | Usuario de la base. |
| `wordpress_db_password` | `change_me` | Password (sobreescribir con vault). |
| `wordpress_db_host` | `localhost` | Host de la base. |

## Uso

```yaml
- hosts: wordpress
  become: true
  roles:
    - role: santi.wordpress
```

## Pruebas

```bash
export PATH=/ruta/al/venv/bin:$PATH
ansible-galaxy install -r requirements.yml
yamllint .
ansible-lint
molecule test
```

## Licencia

GPL-2.0-or-later.
