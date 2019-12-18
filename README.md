
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


