# Building a WordPress Project with DDEV

# Create DDEV Project

ddev config --project-type=wordpress --docroot=. --create-docroot

# Create DDEV Project Manually

```

ddev config 

Project name (wordpress-ddev): 

The docroot is the directory from which your site is served.
This is a relative path from your project root at /Users/user/projects/wordpress-ddev
 
Leave docroot empty (hit <RETURN>) to use the location shown in parentheses.
Or specify a custom path if your index.php is in a different directory.
Or use '.' (a dot) to explicitly set it to the project root.
 
Docroot Location (project root): 
Found a php codebase at /Users/user/projects/wordpress-ddev. 
Project Type [backdrop, cakephp, craftcms, drupal, drupal6, drupal7, drupal8, drupal9, drupal10, drupal11, generic, laravel, magento, magento2, php, shopware6, silverstripe, symfony, typo3, wordpress] (php): wordpress

Configuration complete. You may now run 'ddev start'. 

```

# DDEV Describe

```

ddev describe

┌───────────────────────────────────────────────────────────────────────────────────────────┐
│ Project: wordpress-test ~/projects/wordpress-test https://wordpress-test.ddev.site        │
│ Docker platform: docker-desktop                                                           │
│ Router: traefik                                                                           │
├──────────────┬──────┬────────────────────────────────────────────────┬────────────────────┤
│ SERVICE      │ STAT │ URL/PORT                                       │ INFO               │
├──────────────┼──────┼────────────────────────────────────────────────┼────────────────────┤
│ web          │ OK   │ https://wordpress-test.ddev.site               │ wordpress PHP 8.3  │
│              │      │ InDocker -> Host:                              │ Server: nginx-fpm  │
│              │      │  - web:80 -> 127.0.0.1:51319                   │ Docroot: '.'       │
│              │      │  - web:443 -> 127.0.0.1:51318                  │ Perf mode: mutagen │
│              │      │  - web:8025 -> 127.0.0.1:51320                 │ Node.js: 22        │
├──────────────┼──────┼────────────────────────────────────────────────┼────────────────────┤
│ db           │ OK   │ InDocker -> Host:                              │ mariadb:10.11      │
│              │      │  - db:3306 -> 127.0.0.1:51317                  │ User/Pass: 'db/db' │
│              │      │                                                │ or 'root/root'     │
├──────────────┼──────┼────────────────────────────────────────────────┼────────────────────┤
│ Mailpit      │      │ Mailpit: https://wordpress-test.ddev.site:8026 │                    │
│              │      │ Launch: ddev mailpit                           │                    │
├──────────────┼──────┼────────────────────────────────────────────────┼────────────────────┤
│ Project URLs │      │ https://wordpress-test.ddev.site               │                    │
│              │      │ , https://127.0.0.1:51318,                     │                    │
│              │      │ http://wordpress-test.ddev.site:               │                    │
│              │      │ 33001, http://127.0.0.1:51319                  │                    │
└──────────────┴──────┴────────────────────────────────────────────────┴────────────────────┘

```

# WordPress Commands

```
-- Download

ddev wp core download

-- Install

ddev wp core install \
--url=https://wordpress-test.ddev.site \
--title="My WordPress Test" \
--admin_user=admin \
--admin_password=admin \
--admin_email=admin@example.com

-- List Plugins

ddev wp plugin list

+---------+----------+--------+---------+----------------+-------------+
| name    | status   | update | version | update_version | auto_update |
+---------+----------+--------+---------+----------------+-------------+
| akismet | inactive | none   | 5.6     |                | off         |
| hello   | inactive | none   | 1.7.2   |                | off         |
+---------+----------+--------+---------+----------------+-------------+

-- List Themes

ddev wp theme list

+-------------------+----------+--------+---------+----------------+-------------+
| name              | status   | update | version | update_version | auto_update |
+-------------------+----------+--------+---------+----------------+-------------+
| twentytwentyfive  | active   | none   | 1.4     |                | off         |
| twentytwentyfour  | inactive | none   | 1.4     |                | off         |
| twentytwentythree | inactive | none   | 1.6     |                | off         |

-- Create Admin User

ddev wp user create admin2 admin2@example.com --role=administrator --user_pass=admin

-- Change Admin Password

ddev wp user update admin --user_pass=admin

-- Update Url

ddev wp option get siteurl
ddev wp option get home

ddev wp option update siteurl https://wordpress-ddev.ddev.site
ddev wp option update home https://wordpress-ddev.ddev.site

-- Delete Theme

ddev wp theme list
ddev wp theme deactivate eduvision
ddev wp theme delete eduvision

-- Open WordPress Page 

ddev launch

```

# Links

https://wordpress-test.ddev.site

https://wordpress-test.ddev.site/wp-admin

# Deploy on GitHub

```
git init
git status
git add .
git commit -m "Initial commit: DDEV WordPress Test"

git remote add origin https://github.com/devrazec/wordpress-test.git
git branch -M main
git push -u origin main

```
