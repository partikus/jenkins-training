# POP in PHP


```
vagrant up && echo "take a coffee"
```

### Step 1

```
cd /var/www/
git clone https://github.com/partikus/symfony-demo.git
cd symfony-demo
git checkout -b origin/step_2 origin/step_2
composer install --prefer-dist
php bin/console server:start 10.0.0.200:8080
http://10.0.0.200:8080
```

```yaml
parameters:
    locale: en
    env(SYMFONY_SECRET): pgs
    env(SYMFONY_LOG): '%kernel.logs_dir%/%kernel.environment%.log'
    env(DATABASE_URL): 'sqlite:///%kernel.root_dir%/data/blog.sqlite'
```

### Step 2 

Running already existing tests
```
cd /var/www/symfony-demo/
php vendor/bin/phpunit -c phpunit.xml.dist
```

### Step 3
Page Object Pattern and Symfony Client 
```
git checkout -b origin/step_3 origin/step_3
composer install --prefer-dist
php bin/console server:stop
php bin/console server:start 10.0.0.200:8080
```

### Step 4
Page Object Pattern and Selenium
```
git checkout -b origin/step_4 origin/step_4
composer install --prefer-dist
php bin/console server:stop
php bin/console server:start 10.0.0.200:8080
```
