# restful-api-service-with-slimwork
restful api service

How to Install Slim
We recommend you install Slim with Composer. Navigate into your project’s root directory and execute the bash command shown below. This command downloads the Slim Framework and its third-party dependencies into your project’s vendor/ directory.

composer require slim/slim:3.*
Require the Composer autoloader into your PHP script, and you are ready to start using Slim.

<?php
require 'vendor/autoload.php';


$app = new \Slim\App();

//route

$app->get('/', function (Request $req,  Response $res, $args = []) {
    return $res->withStatus(400)->write('Bad Request');
});

$app->get('/', function (Request $req,  Response $res, $args = []) {
    $myvar1 = $req->getParam('myvar'); //checks both _GET and _POST [NOT PSR-7 Compliant]
    $myvar2 = $req->getParsedBody()['myvar']; //checks _POST  [IS PSR-7 compliant]
    $myvar3 = $req->getQueryParams()['myvar']; //checks _GET [IS PSR-7 compliant]
});


// named parameter:
$app->get('/hello/{name}', /*...*/);

// optional segment:
$app->get('/news[/{year}]', /*...*/);
