# Create, publish and use your first composer package

touch `composer.json`

```json
    "name": "varius/hello-composer",
    "description": "A simple hello world composer package",
    "type": "library",
    "license": "MIT",
    "authors": [
        {
            "name": "varius",
            "email": "itbeard@inbox.lv"
        }
    ],
    "minimum-stability": "stable",
    "autoload": {
        "psr-4": {"varius\\HelloWorld\\": "src/"}
    },
    "require": {}
}
```

## **PSR-4 Autoload**

PSR-4 is the current autoload standard that defines a key by mapping from namespaces to paths, relative to the package root. When autoloading a class like Varius\\\HelloWorld\Index, a prefix Vitalis\\ pointing to a directory src/ means that the autoloader should look for a file named src/HelloWorld/index.php and include it if present.

```sh
mkdir src && touch src/index.php
```

```php
<?php 

namespace vitalis\HelloWorld;

class Index
{
    public function greet($greet = "Hello World")
    {
        return $greet;
    }
}
```

## **Hosting Our Package**

In order to publish our “hello-word” pacTo register our newly created package on Packagist simply, go to https://packagist.org create an account with them if don’t have one and then submit the URL of our repository, as shown below:kage in Packagist, you will need to host our package in a repository first with version control as GIT, Subversion or Mercurial. As earlier stated, we are going to use GitHub to host our package.

## **Register package on Packagist**

To register our newly created package on Packagist simply, go to https://packagist.org create an account with them if don’t have one and then submit the URL of our repository, as shown below:

![Packagist](https://www.w3resource.com/w3r_images/Packagist.png)

Once our package is accepted, our dashboard will look like the one shown below:

![dashboard](https://www.w3resource.com/w3r_images/Packagist_dashboard.png)

The auto-update warning is simply telling us that our package is not auto updated. We will be fixing that in the next tutorial, but for now lets quickly create another project to then consume this package we created.

## **Requiring and Testing Our Package.**

To test the package we just published, quickly create a new project directory and initialize composer in this directory just like we did above, the composer.json file for this composer will look like this:

```json
{
    "name": "vitalis/hello-composer",
    "description": "A simple hello world composer package",
    "type": "library",
    "license": "MIT",
    "authors": [
        {
            "name": "Ogbonna Vitalis",
            "email": "agavitalisogbonna@gmail.com"
        }
    ],
    "minimum-stability": "stable",
    "autoload": {
        "psr-4": {"vitalis\\HelloWorld\\": "src/"}
    },
    "require": {}
}

```

Now we must require the package we just published using the composer install command as shown in the code snippet below

```sh
composer require vitalis/hello-composer
```

Also ensure that the minimum-stability of the package you want to install is the same as the one you are installing it in, so as to avoid some annoying errors.

## Using the installed Package

To use our installed package, we create an “index.php” at the root of our “test-hello-composer” directory and then require the just downloaded file as shown in the code snippet below:

```php
<?php

require_once __DIR__ . '/vendor/autoload.php';

use vitalis\HelloWorld\Index;

$greeting = new Index();

echo $greeting->greet("Hello Composer");

}
```

In the above code snippet we required the “vendor/autoload.php” where and then used the namespace of the package we downloaded to enable us instantiate a class in this package.

## **Testing our Code**

To test if our code is working, we navigate to this “test-hello-composer” directory from the terminal and run the “index.php” file using “php” command, as shown in the code snippet below:

```bash
php index.php
```

Voila!!! We have successfully created, published and used our first composer package. If you love this tutorial, don’t forget to share, like and comment. Follow us on twitter for more updates.

You can get the complete versions of this packages on GitHub at hello-composer and test-hello-composer.

In the next tutorial, we look at how to auto-update our packages using webhook. See you soon.

---



## PHP: Tips of the Day

You could also take a look at the DatePeriod class:

```php
$period = new DatePeriod(
     new DateTime('2010-10-01'),
     new DateInterval('P1D'),
     new DateTime('2010-10-05')
);
```

Which should get you an array with DateTime objects.

To iterate

```php
foreach ($period as $key => $value) {
    //$value->format('Y-m-d')       
}
```

Ref : https://bit.ly/3f87o8T