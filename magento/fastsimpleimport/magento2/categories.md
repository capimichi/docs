# Categories


## Example 1



```php

/** @var \FireGento\FastSimpleImport\Model\Importer $importerModel */
$importerModel = $this->objectManager->create('FireGento\FastSimpleImport\Model\Importer');

$categoryArray = [
    [
        '_root' => 'Default Category',
        '_category' => 'FireGento TestCategory',
        'description' => 'Test',
        'is_active' => '1',
        'include_in_menu' => '1',
        'meta_description' => 'Meta Test',
        'available_sort_by' => 'position',
        'default_sort_by' => 'position',
    ],
];

$importerModel->setEntityCode('catalog_category');


try {
    $importerModel->processImport($categoryArray);
} catch (\Exception $e) {
    print_r($e->getMessage());
}

print_r($importerModel->getLogTrace());
print_r($importerModel->getErrorMessages());

```

## Example 2


```php

$data[] = array(
            '_root' => 'Default Category',
            '_category' => 'FireGento TestCategory',
            'description' => 'Test2',
            'is_active' => '1',
            'include_in_menu' => '1',
            'meta_description' => 'Meta Test',
            'available_sort_by' => 'position',
            'default_sort_by' => 'position',
            'is_anchor' => '1'
        );
        return $data;

```


## Example 3 (multi store view)

```php

 $data[] = array(
            '_root' => 'Default Category',
            '_category' => 'FireGento TestCategory DE',
            'description' => 'Test2',
            'is_active' => '1',
            'include_in_menu' => '1',
            'meta_description' => 'Meta Test',
            'available_sort_by' => 'position',
            'default_sort_by' => 'position',
            'is_anchor' => '1'
        );
        $data[] = array(
            '_store' => 'en',
            'name' => 'FireGento TestCategory EN',
            'description' => 'StoreViewLevel'
        );
        return $data;
        
```
