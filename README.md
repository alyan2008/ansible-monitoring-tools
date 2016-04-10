# Configuration OpenLDAP + phpldapadmin in docker containers

Before you run the playbook please do these actions:

1. Specify the host where you are going to install Ldap server in inventory.ini. Instead of x.x.x.x you should specify the IP address of you ldap server.
2. In openldap.yml do the next:
   - Generate two password (First for ldap root user, second for test user). You can use - http://passwordsgenerator.net/md5-hash-generator/
   - Specify your domain name insteatd of yourdomain.com.
   - Specify HASHED_PASSWD_ROOT and HASHED_PASSWD_USER which you got in the first step. You shoul write it instead of xxxx.
   - In section PASSWD_ROOT please specify ldap root password ( not hash!). Write it instead of xxxx.
   - Then you should specify details for your new user: username, fullname, surname and email.

3. To your hosts file on yout laptop please add line - ip_address_of_ldap_server ldapadmin.yourdomain.com. Instead of ip_address_of_ldap_server and yourdomain.com you should specify your parameters.
   
After that you can run playbook:

ANSIBLE_CONFIG=./ansible.cfg ansible-playbook -i inventory.ini openldap.yml

Once it finished you should have access to your ldap server on port 389 and phpldapadmin - http://ldapadmin.yourdomain.com/
