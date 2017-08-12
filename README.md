Ansible Role: Nexcess Cloud App - Magento2
==================================================

# Overview
This Ansible role is designed to be used with the Nexcess Application Cloud set of playbooks for environment creation and code deployment.
See: [ansible-playbook-cloud-app](https://github.com/nexpoehler/ansible-playbook-cloud-app)
Includes support for Redis and Varnish.

# Role Variables
See `defaults/main.yml` for a complete list of available variables.

## Role Variables: Standard Deploy
### Build Creation Step
    nex_app_magento_public_key: [public key goes here]
	nex_app_magento_private_key: [private key goes here]
See [magento documentation](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html)

    magento_crypt_key: [encryption key]
The Magento encryption key used for encryption of sensitive data in the application database.

### Deployment Step

    magento_upgrade: true
Run bin/magento setup:upgrade as part of application deployment.	

    magento_clean_cache: true
Run bin/magento cache:clean as part of application deployment.
	
	magento_set_mode: true
Run bin/magento deploy:mode:set production as part of application deployment.

## Role Variables: Fresh-install Deploy
The role can be used to perform a fresh install of Magento (currently used primarily for testing).

    # build-time variables for use with fresh install
    magento_fresh_install: [false]
    magento_project_name: "magento/project-community-edition"
    magento_base_url: "http://{{ nex_app_domain }}/"
    magento_base_url_secure: "https://{{ nex_app_domain }}/"
    magento_admin_firstname: "Magento"
    magento_admin_lastname: "User"
    magento_admin_email: "example@user.com"
    magento_admin_user: "admin"
    magento_admin_pass: "[ADMIN PASSWORD]"
    magento_backend_frontname: "admin"
    magento_lang: "en_US"
    magento_currency: "USD"
    magento_timezone: "America/New_York"	

# License
MIT
