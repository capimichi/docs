# Products

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

## Example 3 (multiselect)

```php
 $data = [];
        for ($i = 1; $i <= 1; $i++) {
            $data[] = array(
                'sku' => 'FIREGENTO-' . $i,
                'attribute_set_code' => 'Default',
                'product_type' => 'simple',
                'product_websites' => 'base',
                'name' => 'FireGento Test Product ' . $i,
                'price' => '14.0000',
                'ean' => "1234",
                'multiselect' => 'Test|Test3'
            );
        }
        return $data;
```

## Example 4 (configurable)

```php
$products = [];
        $products [] = array(
            'sku' => "SIMPLE-BLUE-SMALL",
            'attribute_set_code' => 'Default',
            'product_type' => 'simple',
            'product_websites' => 'base',
            'name' => 'FireGento Simple Product Blue,Size Small',
            'price' => '1.0000',
            'color' => 'blue',
            'size' => 'S'
        );
        $products [] = array(
            'sku' => "SIMPLE-RED-MIDDLE",
            'attribute_set_code' => 'Default',
            'product_type' => 'simple',
            'product_websites' => 'base',
            'name' => 'FireGento Simple Product Red,Size Middle',
            'price' => '1.0000',
            'color' => 'red',
            'size' => 'M'
        );

        $products [] = array(
            'sku' => 'CONFIG-Product',
            'attribute_set_code' => 'Default',
            'product_type' => 'configurable',
            'product_websites' => 'base',
            'name' => 'FireGento Test Product Configurable',
            'price' => '10.000',
            'configurable_variation_labels' => 'Color',
            'configurable_variations' => array(
                array(
                    'sku' => 'SIMPLE-BLUE-SMALL',
                    'color' => 'blue',
                    'size' => 'S'),
                array(
                    'sku' => 'SIMPLE-RED-MIDDLE',
                    'color' => 'red',
                    'size' => 'M'),
            )

        );
```

## Example 5 (bundle)

```php
$simpleProducts = [];
        $bundleProduct = array(
            'sku' => 'Bundle-Product',
            'attribute_set_code' => 'Default',
            'product_type' => 'bundle',
            'product_websites' => 'base',
            'name' => 'FireGento Test Product Bundle',
            'price' => '10.000',

            'bundle_price_type' => 'dynamic',
            'bundle_sku_type' => 'dynamic',
            'bundle_price_view' => 'Price range',
            'bundle_weight_type' => 'dynamic',


        );

        $colors = array("blue", "black");
        $bundleValues = '';
        for ($i = 0; $i < 2; $i++) {

            $color = $colors[$i];
            $sku = 'SIMPLE-' . $color;
            $simpleProducts[] = array(
                'sku' => $sku,
                'attribute_set_code' => 'Default',
                'product_type' => 'simple',
                'product_websites' => 'base',
                'name' => 'FireGento Test Product Simple - ' . $color,
                'price' => '14.0000',
                'additional_attributes' => "color=" . $color

            );
            $bundleAttributes = array(
                "name" => "Color",
                "type" => 'radio',
                'required' => '1',
                'sku' => $sku,
                'price' => '14.0000',
                'default' => $i,
                'default_qty' => '1.0000',
                'price_type' => 'fixed'
            );


            $bundleValues .= $this->arrayToAttributeString($bundleAttributes) . "|";

        }
        $bundleProduct["bundle_values"] = $bundleValues;
        print_r($bundleProduct);


        $data = array_merge($simpleProducts, array($bundleProduct));


        return $data;
```

## Fields

| Field |
| ------------- |
| sku |
| store_view_code |
| attribute_set_code |
| product_type |
| categories |
| product_websites |
| name |
| description |
| short_description |
| weight |
| product_online |
| tax_class_name |
| visibility |
| price |
| special_price |
| special_price_from_date |
| special_price_to_date |
| url_key |
| meta_title |
| meta_keywords |
| meta_description |
| base_image |
| base_image_label |
| small_image |
| small_image_label |
| thumbnail_image |
| thumbnail_image_label |
| swatch_image |
| swatch_image_label |
| created_at |
| updated_at |
| new_from_date |
| new_to_date |
| display_product_options_in |
| map_price |
| msrp_price |
| map_enabled |
| gift_message_available |
| custom_design |
| custom_design_from |
| custom_design_to |
| custom_layout_update |
| page_layout |
| product_options_container |
| msrp_display_actual_price_type |
| country_of_manufacture |
| additional_attributes |
| qty |
| out_of_stock_qty |
| use_config_min_qty |
| is_qty_decimal |
| allow_backorders |
| use_config_backorders |
| min_cart_qty |
| use_config_min_sale_qty |
| max_cart_qty |
| use_config_max_sale_qty |
| is_in_stock |
| notify_on_stock_below |
| use_config_notify_stock_qty |
| manage_stock |
| use_config_manage_stock |
| use_config_qty_increments |
| qty_increments |
| use_config_enable_qty_inc |
| enable_qty_increments |
| is_decimal_divided |
| website_id |
| related_skus |
| related_position |
| crosssell_skus |
| crosssell_position |
| upsell_skus |
| upsell_position |
| additional_images |
| additional_image_labels |
| hide_from_product_page |
| bundle_price_type |
| bundle_sku_type |
| bundle_price_view |
| bundle_weight_type |
| bundle_values |
| bundle_shipment_type |
| associated_skus |
