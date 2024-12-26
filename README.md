Nginx Ansible role
=========

Installs nginx on Ubuntu. Role created within educational process and for educational purposes.

Requirements
------------

- Target machine is Ubuntu.

Role Variables
--------------

- nginx_installing_packages: list of apt nginx packages to be installed
- nginx_systemd_service_name: name of systemd nginx service
- nginx_static_files_general_path: path to all static files for nginx
- nginx_static_files_mode: permissions for static files for nginx
- nginx_available_sites_path: path to files of availabile sites
- nginx_conf_template_mode: permissions of nginx configuration file-template
- nginx_conf_validation_cmd: command to partially verify configuration template
- nginx_enabled_sites_path: path to files of enables sites
- nginx_server_blocks_domain_to_conf_template_and_static_files_path_dict: complex variable, dictionary, giving an ability to create lots of nginx server blocks. Dictionary, where key is domain and value is object, consisting of conf_template - path to ansible jinja2 template on host machine to be used as configuration file of domain-site - and static_files_path - path to static files directory for site on remote machine to be copied

Dependencies
------------


No dependencies.

Example Playbook
----------------

    - hosts: servers
      roles:
        - nginx


    - hosts: servers
      roles:
        - role: nginx
          vars:
            nginx_server_blocks_domain_to_conf_template_and_static_files_path_dict:
              first_domain:
                conf_template: "{{ inventory_dir }}/templates/first_domain.conf.j2"
                static_files_path: /tmp/first_domain/static
              second_domain:
                conf_template: templates/common.nginx.j2
                static_files_path: {{ second_domain_repo }}/documents
License
-------

MIT

Author Information
------------------

Grigorii Simonov
