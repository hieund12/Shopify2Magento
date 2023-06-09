# Compare db tables Shopify and Magento2
## PRODUCTS:
### Shopify:
Ở Shopify Thông tin sản phẩm được lưu trữ chủ yếu trong bảng products và variants.
- Bảng products: id, title (Name), body_html (Full Description), published_at (Status), handle (URL), meta_title, meta_description, tags (Product Tags).
- Bảng variants: id, product_id, sku (SKU), weight (Weight), option1, option2, option3 (Attributes), inventory_quantity (Quantity), price (Price), compare_at_price (Special Price).
- Về MANUFACTURERS: Shopify không có bảng dữ liệu riêng biệt, nhưng có thể sử dụng Product Tags hoặc Product Metafields.
- Về ảnh sản phẩm: Bảng product_images chứa id, product_id, position, src (Base Image và Additional Images).
- Về thông tin kho: Bảng inventory_items chứa id, product_id, variant_id, sku, inventory_quantity (Quantity), requires_shipping (Stock Availability), track_inventory (Manage Stock).
 - Bảng images: src (Base Image và Additional Images), 
 - Bảng options và values: Lưu các thuộc tính của sản phẩm (Attributes)
 - Bảng metafields: Lưu Meta Title và Meta Description
 - Bảng tags: Lưu Product Tags
 - Bảng collections: Lưu thông tin về Product Categories


#### Magento 2:
1. Thông tin chung về sản phẩm:
- catalog_product_entity: entity_id, sku, created_at, updated_at, has_options, required_options
- catalog_product_entity_varchar: entity_id, attribute_id, store_id, value (Name, Meta Title, Meta Description, URL)
- catalog_product_entity_text: entity_id, attribute_id, store_id, value (Full Description)
- catalog_product_entity_int: entity_id, attribute_id, store_id, value (Status, Manufacturer, Stock Availability, Manage Stock)
- catalog_product_entity_decimal: entity_id, attribute_id, store_id, value (Price, Special Price, Weight)
- catalog_product_entity_media_gallery: value_id, attribute_id, entity_id, value (Base Image, Additional Images)
2. Thông tin về Product Tags:
Magento 2 không có chức năng Product Tags mặc định. Tuy nhiên, có thể sử dụng các extension của bên thứ ba hoặc tạo một [custom attribute](https://github.com/hieund12/magento2/blob/main/README.md#to-create-a-custom-attribute-in-magento-2-follow-these-steps) để quản lý Product Tags.

3. Thông tin về Variants (còn gọi là Configurable Products):
- catalog_product_super_attribute: product_super_attribute_id, product_id, attribute_id, position
- catalog_product_super_attribute_label: product_super_attribute_id, store_id, value (Attributes)
- catalog_product_super_link: parent_id, product_id
- catalog_product_relation: parent_id, child_id
4. Thông tin về Quantity, Stock Availability, Manage Stock:
- cataloginventory_stock_item: item_id, product_id, stock_id, qty (Quantity), min_qty, use_config_min_qty, is_qty_decimal, backorders, use_config_backorders, min_sale_qty, use_config_min_sale_qty, max_sale_qty, use_config_max_sale_qty, is_in_stock (Stock Availability), low_stock_date, notify_stock_qty, use_config_notify_stock_qty, manage_stock (Manage Stock), stock_status_changed_auto, use_config_qty_increments, qty_increments, use_config_enable_qty_inc, enable_qty_increments, is_decimal_divided, website_id

##	PRODUCT CATEGORIES:
#### Shopify:
 - Shopify sử dụng một cấu trúc dữ liệu đơn giản hơn cho các danh mục sản phẩm, thường được gọi là Collections. Các thông tin chính được lưu trữ trong bảng collections.
 - Các trường liên quan trong bảng collections gồm: id, title (Name), body_html (Description), published_at (Status), image, handle (URL), meta_title, meta_description.
#### Magento 2:
 - Magento 2 có một cấu trúc phức tạp hơn cho các danh mục sản phẩm. Thông tin về danh mục được lưu trữ trong hai bảng chính: catalog_category_entity và catalog_category_entity_varchar.
 - Các trường liên quan trong bảng catalog_category_entity gồm: entity_id, parent_id, path, position, level, children_count.
 - Các trường liên quan trong bảng catalog_category_entity_varchar gồm: entity_id, attribute_id, store_id, value (Name, Description, Meta Title, Meta Description).

##	MANUFACTURERS:
#### Shopify:
 - Shopify không có một bảng dữ liệu riêng biệt cho nhà sản xuất. Tuy nhiên, bạn có thể sử dụng tính năng Product Tags hoặc Product Metafields để lưu trữ thông tin về nhà sản xuất.
#### Magento 2:
 - Magento 2 sử dụng bảng eav_attribute để lưu trữ thông tin về nhà sản xuất. Trường liên quan: attribute_id, entity_type_id, attribute_code (Name).

##	TAXES:
#### Shopify:
 - Shopify lưu trữ thông tin về thuế trong bảng tax_rates và tax_rules.
 - Bảng tax_rates gồm các trường: id, country_code (Country), percentage (Percent).
 - Bảng tax_rules không có trường tương ứng với Tax Class, nhưng bạn có thể sử dụng Product Type hoặc Product Tags để phân loại sản phẩm theo loại thuế.
#### Magento 2:
 - Magento 2 lưu trữ thông tin về thuế trong bảng tax_calculation_rate và tax_calculation_rule.
 - Bảng tax_calculation_rate gồm các trường: tax_calculation_rate_id, tax_country_id (Country), tax_region_id, tax_postcode, code (Name), rate (Percent).
 - Bảng tax_calculation_rule gồm các trường: tax_calculation_rule_id, code (Name), tax_calculation_rate_id (Tax Rate), customer_tax_class_id (Tax Class).


### To create a custom attribute in Magento 2, follow these steps:

1. Log in to the Magento 2 Admin Panel.
2. Navigate to Stores > Attributes > Product in the left sidebar menu.
3. Click the "Add New Attribute" button in the top right corner.
4. Fill in the required fields for your custom attribute:
- Attribute Code: Enter a unique identifier for the attribute (e.g., custom_vendor). Use lowercase letters and underscores only.
- Default Label: Enter the attribute's label, which will be displayed in the admin panel and on the storefront (e.g., Custom Vendor).
- Catalog Input Type for Store Owner: Choose the input type for the attribute (e.g., Text Field, Dropdown, etc.).
5. Configure the additional settings in the "Attribute Properties" section:
- Values Required: Set to "Yes" if a value must be entered for this attribute.
- Input Validation for Store Owner: Choose the validation type for the attribute (e.g., alphanumeric, numeric, etc.). This is optional and depends on the input type you selected.
6. Set the "Advanced Attribute Properties" as needed:
- Attribute Code: This is automatically filled based on your entry in step 4.
- Scope: Choose the scope of the attribute (Global, Website, or Store View). Global is the most common choice.
- Unique Value: Set to "Yes" if each product must have a unique value for this attribute.
7. Input Validation for Store Owner: Choose the validation type for the attribute (e.g., alphanumeric, numeric, etc.). This is optional and depends on the input type you selected.
- In the "Manage Labels" section, you can add translations for your attribute label if your store supports multiple languages.
8. To make the custom attribute visible on the storefront, go to the "Storefront Properties" section and set the following options:
- Use in Search: Set to "Yes" if you want the attribute to be used in search.
- Visible in Advanced Search: Set to "Yes" if you want the attribute to be visible in the advanced search form.
- Comparable on Storefront: Set to "Yes" if you want the attribute to be available for comparison.
- Use in Layered Navigation: Set to "Yes" if you want the attribute to be used in layered navigation.
- Position: Set the position of the attribute in the layered navigation block.
- Use for Promo Rule Conditions: Set to "Yes" if you want the attribute to be used in promotional rule conditions.
- Allow HTML Tags on Storefront: Set to "Yes" if you want to allow HTML tags in the attribute value on the storefront.
- Visible on Catalog Pages on Storefront: Set to "Yes" if you want the attribute to be visible on catalog pages.
- Used in Product Listing: Set to "Yes" if you want the attribute to be used in product listings.
- Used for Sorting in Product Listing: Set to "Yes" if you want the attribute to be used for sorting in product listings.
9. Click "Save Attribute" in the top right corner to create the custom attribute.

> After creating the custom attribute, you can use it in your product import process. Make sure to include the attribute code in your Magento 2 CSV file for a successful import.


## Variant fields in magento 2
In Magento 2, product variants are usually managed using Configurable Products. Configurable products have multiple associated Simple Products, which represent the different variants based on specific attributes like size, color, etc. Here's a list of the fields relevant to variants in Magento 2:

1. Product SKU: A unique identifier for each product variant. Each associated Simple Product will have its own SKU.
2. Attribute Set: The set of attributes used to describe the product variants. For example, a clothing product may have attributes like size and color.
3. Attribute Code: The unique code for each attribute used in the configurable product.
4. Attribute Value: The value of the attribute for a specific product variant. For example, the size attribute may have values like Small, Medium, or Large.
5. Price: The price of each product variant. Prices can be set individually for each associated Simple Product.
6. Special Price: A discounted price for the product variant, if applicable. This field is optional.
7. Cost: The cost of goods for each product variant. This field is optional and used for calculating profit margins.
8. Weight: The weight of each product variant. This information is used for shipping calculations.
9. Quantity: The stock quantity for each product variant. This information is used for inventory management.
10. Stock Status: The stock availability status for each product variant (In Stock or Out of Stock).
11. Visibility: The visibility settings for each product variant in the catalog and search results. Simple products associated with configurable products are usually set to "Not Visible Individually."
12. Tax Class: The tax class for each product variant. This information is used for tax calculations.
13. Images: Product images for each variant. You can set different images for each associated Simple Product to showcase the specific variant.

These fields are associated with Simple Products that are linked to a Configurable Product, representing the different variants of the product. When importing or managing product variants in Magento 2, you will need to work with these fields to create and update the required product data.


### How to create attribute (for import)
You need to create the "color" attribute and add it to the attribute set in Magento 2 before importing the products. Please follow these steps:

1. Log in to your Magento 2 admin panel.
2. Go to Stores > Attributes > Product.
3. Click "Add New Attribute" button.
4. Fill in the required fields:
- Attribute Code: color (use lowercase)
- Default Label: Color
- Catalog Input Type for Store Owner: Dropdown
- Values Required: Yes (if you want the color to be required for all products)
5. Click "Save Attribute" to create the attribute.
6. Go to Stores > Attributes > Attribute Set.
7. Select the "Default" attribute set (or the attribute set you're using for your products).
8. Drag the newly created "Color" attribute from the "Unassigned Attributes" column to the "Groups" column under an appropriate group (e.g., Product Details).
9. Click "Save" to update the attribute set.

### To display configurable products in the Magento 2 storefront, follow these steps:
1. Log in to your Magento 2 Admin Panel.
2. Navigate to Catalog > Products.
3. Click the "Add Product" dropdown and select "Configurable Product."
4. Fill in the required product details, such as Name, SKU, Price, Tax Class, etc.
5. In the "Configurations" section, click on "Create Configurations."
6. Select the attributes you want to use for the configurable product (e.g., size, color). You can either use existing attributes or create new ones.
7. Click "Next" and configure the attribute options. For example, if you chose the "Size" attribute, you would specify the available sizes (Small, Medium, Large, etc.).
8. Click "Next" again, and set the specific details for each simple product associated with the configurable product (e.g., SKU, price, quantity, images).
9. Click "Next" to review your configurations, and click "Generate Products" to create the associated simple products.
10. After generating the simple products, fill in any additional information and assign the configurable product to the appropriate categories.
11. Set the product's visibility to "Catalog, Search" or "Catalog" under the "Search Engine Optimization" section to make it visible in the storefront.
12. Save your changes by clicking the "Save" button at the top right corner.
13. Clear the Magento cache by navigating to System > Cache Management and clicking "Flush Magento Cache."
14. Visit the storefront, and you should see the configurable product in the assigned categories, where customers can select different options and add the product to their cart.

Note: If you don't see the configurable product in the storefront, ensure that it is enabled, in stock, and has a positive quantity. Also, check that the associated simple products are set to "Not Visible Individually."







