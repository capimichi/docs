# Import products

## Example 1

```php
$data[] = array(
                'sku' => 'FIREGENTO-' . $i,
                'attribute_set_code' => 'Default',
                'product_type' => 'simple',
                'product_websites' => 'base',
                'name' => 'FireGento Test Product ' . $i,
                'price' => '14.0000',
                'ean' => "1234",
                'color' => "PurpleBlue"
                //'visibility' => 'Catalog, Search',
                //'tax_class_name' => 'Taxable Goods',
                //'product_online' => '1',
                //'weight' => '1.0000',
                //'short_description' => NULL,
                //'description' => '',
            ); 

```
 
## Example 2

```php
/** @var \FireGento\FastSimpleImport\Model\Importer $importerModel */
$importerModel = $this->objectManager->create('FireGento\FastSimpleImport\Model\Importer');

$productsArray = [
    [
        'sku' => 'firegento-test',
        'attribute_set_code' => 'Default',
        'product_type' => 'simple',
        'product_websites' => 'base',
        'name' => 'FireGento Test Product',
        'price' => '14.0000',
    ],
];

try {
    $importerModel->processImport($productsArray);
} catch (\Exception $e) {
    $output->writeln($e->getMessage());
}

print_r($importerModel->getLogTrace());
print_r($importerModel->getErrorMessages());
```
