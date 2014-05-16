entwicklerbier.org
==================

Our Dokku deployed wordpress

Add a Database - we used MariaDB
  cd /var/lib/dokku/plugins
  git clone https://github.com/Kloadut/dokku-md-plugin mariadb
  dokku plugins-install
  mariadb:create blog


Deploy
  git remote add deploy dokku@entwicklerbier.org:blog
  git push deploy master

Link DB with Application
  mariadb:link blog blog
