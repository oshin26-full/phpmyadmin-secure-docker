phpMyAdmin with Extra Security (Docker)

This setup creates a phpMyAdmin instance with two layers of access protection—not just the standard phpMyAdmin login, but an additional password prompt (called Basic Auth) from Nginx before that.

Contents

- db MySQL, where data is stored
- phpmyadmin an application for managing databases via a browser
- webserver_pma Nginx acts as a gateway requesting the Basic Auth password before allowing access to phpMyAdmin

to Use

1. Clone this repo
2. Replace all instances of YOUR-PASSWORD-HERE in docker-compose.yml with your own password
3. Create a password file for Basic Auth (requires the htpasswd tool, usually part of the apache2-utils package on Linux):
   bash
   htpasswd -c .htpasswd YOUR-USERNAME

5. Run:
bash
   docker compose up -d

5. Open http://localhost:8081 a popup will appear asking for a username and password first (the ones you created in step 3), and then you’ll be taken to the regular phpMyAdmin login page

Notes

- The .htpasswd file was intentionally not uploaded here because it contains encrypted passwords — create your own following the steps above
- Change all default passwords before using the system for real
