# Jbrowse
## Jbrowse Password Setting

For additional reference, you can check: [How to Setup Apache Password Protect Directory with htaccess File](https://www.cyberciti.biz/faq/howto-setup-apache-password-protect-directory-with-htaccess-file/)

1. **Login as "Root"** 

2. **Make the `.htpasswd` file in the JBrowse directory.**
   ```bash
   sudo htpasswd -c /data01/epigenome/JBrowse/.htpasswd schmitzlab1
   ```

3.  **Apache should be configured "/var" directory. (/home directory is denied for authorization with root).**
   It will ask the new password. Type the new password!
   ```bash
  htpasswd -c  /var/www/html/secure/apasswords  schmitzlab1

   chown apache:apache /var/www/html/secure/apasswords

   chmod 0660 /var/www/html/secure/apasswords
   ```


4.  ** Note: should make .htaccess file in "/data01/epigenome/JBrowse/".**
   ```bash
   cd  /data01/epigenome/JBrowse/
   vi .htaccess

   Change the ".htaccess" file by typing below.
   AuthType Basic
   AuthName "Restricted Access"
   AuthUserFile /home/sec/var/www/html/secure/apasswords
   Require user schmitzlab1
