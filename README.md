# Symfony 

## Exerices 

1. Affichez les profils connaissant leurs noms prénoms et lieu de résidence
2. Les données sont stockées dans un tableau (constante) array dans la classe `DefaultController`

Dans le classe DefaultController on peut créer une méthode `people`

```php
<?php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;

final class DefaultController extends AbstractController
{
    const PEOPLE = [
        [
            'name' => 'John Doe',
            'age' => 30,
            'address' => '123 Main St, Anytown, USA'
        ],
        [
            'name' => 'Jane Smith',
            'age' => 25,
            'address' => '456 Oak Ave, Anytown, USA'
        ],
        [
            'name' => 'Alice Johnson',
            'age' => 28
        ],
        [
            'name' => 'Bob Brown',
            'address' => '789 Pine Rd, Anytown, USA'
        ],
        [
            'name' => 'Charlie Davis'
        ]
    ];

    #[Route('/default', name: 'app_default')]
    public function index(): Response
    {
        return $this->render('default/index.html.twig', [
            'controller_name' => 'DefaultController',
        ]);
    }

    // création d'une autre méthode pour servir la page people
    #[Route('/people', name: 'app_default')]
    public function people(): Response
    {
        return $this->render('default/people.html.twig', [
            'peoples' => self::PEOPLE,
        ]);
    }
}

``` 
