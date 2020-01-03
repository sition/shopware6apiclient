
# description of API endpoints for shopware 6

http://www.shopwaredemo.nl/api/v1/_info/swagger.html



# shopware6apiclient


# example

require_once __DIR__ . '/vendor/autoload.php'; 

use Sition\Shopware6\ShopwareClient;

$test = new ShopwareClient( 'http://www.shopwaredemo.nl', 'CLIENT_ID', 'CLIENT_SECRET' );


# get product

$response = $test->request( 'GET', 'product?filter[product.active]=1&filter[product.productNumber]=SWDEMO10007'); 

$body = json_decode($response->getBody()->getContents(), true);

var_dump($body);


# create category


$body = array(  "name" => "test cat" );

$response = $test->request('POST','category',$body);

$body = json_decode($response->getBody()->getContents(), true);

# get complete order including all details

```php
$jayParsedAry = [
    "total-count-mode" => 0,
    "page" => 1,
    "limit" => 25,
    "filter" => [
        [
            "type" => "equals",
            "field" => "stateId",
            "value" => "4c22d7bf1bcd40f1b74385fb28420056" // open orders
        ]
    ],
    "associations" => [
        "lineItems" => [
            "associations" => [
                "product" => [
                    "associations" => [
                        "tax" => [
                        ]
                    ]
                ]
            ]
        ],
        "currency" => [
        ],
        "orderCustomer" => [
        ],
        "language" => [
        ],
        "salesChannel" => [
        ],
        "addresses" => [
            "associations" => [
                "country" => [
                ],
                "countryState" => [
                ],
                "salutation" => [
                ]
            ]
        ],
        "deliveries" => [
            "associations" => [
                "shippingMethod" => [
                ],
                "shippingOrderAddress" => [
                    "associations" => [
                        "country" => [
                        ],
                        "countryState" => [
                        ],
                        "salutation" => [
                        ]
                    ],
                ]
            ]
        ],
        "transactions" => [
            "associations" => [
                "paymentMethod" => [
                ]
            ]
        ],
        "documents" => [
            "associations" => [
                "documentType" => [
                ]
            ]
        ],
        "tags" => [
        ]

    ],
    "aggregations" => [
        [
            "name" => "BillingAddress",
            "type" => "entity",
            "definition" => "order_address",
            "field" => "billingAddressId",
            // opmerking: CountrId is al opgehaald in Adresses array, evenals stateid en salutation.

        ],
    ]

];
```


$response = $test->request( 'POST', 'search/order', $jayParsedAry);
$body = json_decode($response->getBody()->getContents(), true);


