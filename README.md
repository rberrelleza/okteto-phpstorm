# okteto-phpstorm

Demo of a phpstorm project integrated with a Okteto-based development environment running in Kubernetes.

## Instructions
1. Launch your development environment in Kubernetes
    
        okteto up --remote=22000

1. Create an reverse tunnel for port 9000

        ssh -p 22000 -R 9000:localhost:9000 root@localhost 
        
1. Install/update your dependencies in your development environment

        okteto exec -- composer install
        
1. Open PHPStorm, load the project, and run your tests by right-clicking on `phpunit.xml` and select the `run phpunit.xml` option. 
