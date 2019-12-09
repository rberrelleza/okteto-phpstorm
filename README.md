# okteto-phpstorm

Demo of a phpstorm project integrated with a Okteto-based development environment running in Kubernetes.

## Instructions
1. Launch your development environment in Kubernetes
    
        okteto up --remote=22000

1. Create an reverse tunnel for port 9000

        ssh -p 22000 -R 9000:localhost:9000 root@localhost 
        
1. Install/update your dependencies in your development environment

        okteto exec -- composer install
        
1. Open PHPStorm
1.Configure a remote SSH interpreter with the following configurations:
 
     | Setting | Value |
     | ------: | :----------- |
     | Host    | localhost |
     | User    | root |
     | Port    | 22000 |
     | Interpreter| /usr/local/bin/php |
     | Path mappings| $ProjectRoot -> /okteto |
 
1. Add a test framework, pick the remote interpreter you created in the previous step, and set the composer autoloader's path to `/okteto/vendor/autoload.php`
 
1. Run your tests by right-clicking on `phpunit.xml` and select the `run phpunit.xml` option. 
