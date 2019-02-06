Symfony Standard Edition
========================

**WARNING**: This distribution does not support Symfony 4. See the
[Installing & Setting up the Symfony Framework][15] page to find a replacement
that fits you best.

Welcome to the Symfony Standard Edition - a fully-functional Symfony
application that you can use as the skeleton for your new applications.

For details on how to download and get started with Symfony, see the
[Installation][1] chapter of the Symfony Documentation.

What's inside?
--------------

The Symfony Standard Edition is configured with the following defaults:

  * An AppBundle you can use to start coding;

  * Twig as the only configured template engine;

  * Doctrine ORM/DBAL;

  * Swiftmailer;

  * Annotations enabled for everything.

It comes pre-configured with the following bundles:

  * **FrameworkBundle** - The core Symfony framework bundle

  * [**SensioFrameworkExtraBundle**][6] - Adds several enhancements, including
    template and routing annotation capability

  * [**DoctrineBundle**][7] - Adds support for the Doctrine ORM

  * [**TwigBundle**][8] - Adds support for the Twig templating engine

  * [**SecurityBundle**][9] - Adds security by integrating Symfony's security
    component

  * [**SwiftmailerBundle**][10] - Adds support for Swiftmailer, a library for
    sending emails

  * [**MonologBundle**][11] - Adds support for Monolog, a logging library

  * **WebProfilerBundle** (in dev/test env) - Adds profiling functionality and
    the web debug toolbar

  * **SensioDistributionBundle** (in dev/test env) - Adds functionality for
    configuring and working with Symfony distributions

  * [**SensioGeneratorBundle**][13] (in dev env) - Adds code generation
    capabilities

  * [**WebServerBundle**][14] (in dev env) - Adds commands for running applications
    using the PHP built-in web server

  * **DebugBundle** (in dev/test env) - Adds Debug and VarDumper component
    integration

All libraries and bundles included in the Symfony Standard Edition are
released under the MIT or BSD license.

Enjoy!

[1]:  https://symfony.com/doc/3.4/setup.html
[6]:  https://symfony.com/doc/current/bundles/SensioFrameworkExtraBundle/index.html
[7]:  https://symfony.com/doc/3.4/doctrine.html
[8]:  https://symfony.com/doc/3.4/templating.html
[9]:  https://symfony.com/doc/3.4/security.html
[10]: https://symfony.com/doc/3.4/email.html
[11]: https://symfony.com/doc/3.4/logging.html
[13]: https://symfony.com/doc/current/bundles/SensioGeneratorBundle/index.html
[14]: https://symfony.com/doc/current/setup/built_in_web_server.html
[15]: https://symfony.com/doc/current/setup.html
# config-react-symfony

Configuration mariage avec react et symfony 

  * Linux Debian: 9.6

  * Apache 2: 2.4.5

  * php: 7.0

  * composer: 1.2.2-1

  * Node.js: 8.13.0-1nodesource1

Les frameworks principaux qui seront installés étaient à la version suivante lors de l’édition de ce guide:

  * Symfony: 3.4.19

  * React: 16.6

Créer la base de données

mysql -u root -p
CREATE DATABASE symforeactdb 
CHARACTER SET utf8;
GRANT ALL ON symforeactdb.* TO symforeactuser IDENTIFIED BY 
'apassword';

  * $ sudo ln -s /MY_REP/mysymforeactproject/web /var/www/html/symforeact
  * $ sudo chown `whoami`:www-data /MY_REP/mysymforeactproject/web
  * $ sudo chown-R`whoami`:www-data/MY_REP/mysymforeactproject/var/cache
  * $ sudo chown-R`whoami`:www-data/MY_REP/mysymforeactproject/var/logs
  * $ sudo chown-R`whoami`:www-data/MY_REP/mysymforeactproject/var/sessions
  * $ sudo chmod-R775/MY_REP/mysymforeactproject/var/cache
  * $ sudo chmod-R775/MY_REP/mysymforeactproject/var/logs
  * $ sudo chmod-R775/MY_REP/mysymforeactproject/var/sessions

Éditez  le  fichier  /etc/apache2/sites-available/000-default.conf :


`<VirtualHost *:80>
        ServerAdmin webmaster@example.com
        ServerName ladiwa-cours01.univ-lemans.fr
        DocumentRoot "/var/www/html/symforeact/"
        <Location "/symforeact/">
                AllowOverride None
                Require all granted
                Options -Indexes

                RewriteEngine On
                RewriteBase /
                RewriteCond %{REQUEST_FILENAME} -f [OR]
                RewriteCond %{REQUEST_URI} ^/symforeact/?$
                RewriteRule ^ - [L]
                RewriteRule ^ app_dev.php [L]
        </Location>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost> `

Activer le module d’Apache pour la réécriture d’URL : 
 * $ sudo a2enmod rewrite

Prenez en compte les changements de configuration en exécutant la commande
 * $ sudo systemctl restart apache2

Vous pouVez donc lancer un build du frontend pour le développement
 * $ npm run build:dev

Pour développer rapidement, vous pouvez exécuter un serveur node (avec hot rel
oading, etc.)

 * $ npm start

Le serveur est de base en écoute sur le port 3000 : http://localhost:3000

Pour tester l'intégration avec Symfony, ou pour mettre votre serveur en production
 * $ npm run build:prod

http://localhost/symforeact/
