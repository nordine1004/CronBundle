
This bundle provides some command to operates CRUD on `CronJob` entity, which as purpose to ease CRON task management on large apps.

## Installation
In your `composer.json`
  ```
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/Numerique1/CronBundle.git"
        }
    ]
```
Then run
  `composer require numerique1/cron-bundle`
## Configuration
  #### Symfony 4
  In your `services.yaml` :
```
    Numerique1\Bundle\CronBundle\Command\:
        resource: '../vendor/numerique1/cron-bundle/Command/*'
```

***

## Good to know :
  - This bundle use PHP [DateInterval](http://php.net/manual/fr/class.dateinterval.php) for CronJob execution interval

#### Crontab syntax
Example of job definition:

*<sup>1</sup>  *<sup>2</sup>  *<sup>3</sup>  *<sup>4</sup>  *<sup>5</sup>  __user command to be executed__

 - <sup>1</sup> minutes (0-59)
 - <sup>2</sup> hour (0-23)
 - <sup>3</sup> day of month (1-31)
 - <sup>4</sup> month (1-12)
 - <sup>5</sup> day of week (0-6)
#### Exemples

Create a `CronJob`:
```php
php app/console cron:cronjob:create
```
List all `CronJob`:
```php
php app/console cron:cronjob:list
```
Delete a `CronJob`:
```php
php app/console cron:cronjob:delete
```

#### Execution
To execute your previously created `CronJob` you may add the execute command in your server's `crontab`:
```php
5 * * * * php app/console cron:cron:run
```

***

## TODO
  * TESTS.
  * Logs `CronJob` errors to be able to manage them.
  * Add a `$name` unique property on `CronJob` entity to be able to have multiple job for same command.
  * Create `CronResult` entity to save date and messages of each run.
