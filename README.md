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

Add necessary variables to /home/dokku/blog/ENV needed by wordpress see [WordPress.org secret-key service](https://api.wordpress.org/secret-key/1.1/salt/)
  export AUTH_KEY=__GENERATED_AUTH_KEY__
  export SECURE_AUTH_KEY=__GENERATED_SECURE_AUTH_KEY__
  export LOGGED_IN_KEY=__GENERATED_LOGGED_IN_KEY__
  export NONCE_KEY=__GENERATED_NONCE_KEY__
  export AUTH_SALT=__GENERATED_AUTH_SALT__
  export SECURE_AUTH_SALT=__GENERATED_SECURE_AUTH_SALT__
  export LOGGED_IN_SALT=__GENERATED_LOGGED_IN_SALT__
  export NONCE_SALT=__GENERATED_NONCE_SALT__

Link DB with Application
  mariadb:link blog blog
