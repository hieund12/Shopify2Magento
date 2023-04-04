To create a custom attribute in Magento 2, follow these steps:

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
After creating the custom attribute, you can use it in your product import process. Make sure to include the attribute code in your Magento 2 CSV file for a successful import.

### Compare db tables Shopify and Magento2
1. PRODUCTS:
#### Shopify:
 - Bảng products: title, handle (URL), body_html (Full Description), created_at, updated_at, published_at (Status), product_type, vendor (Manufacturer)
 - Bảng variants: sku, weight, weight_unit, price, compare_at_price (Special Price), inventory_quantity (Quantity), inventory_management (Manage Stock)
 - Bảng images: src (Base Image và Additional Images)
 - Bảng options và values: Lưu các thuộc tính của sản phẩm (Attributes)
 - Bảng metafields: Lưu Meta Title và Meta Description
 - Bảng tags: Lưu Product Tags
 - Bảng collections: Lưu thông tin về Product Categories

#### Magento 2:
 - Bảng catalog_product_entity: sku, created_at, updated_at
 - Bảng catalog_product_entity_varchar: name, url_key (URL)
 - Bảng catalog_product_entity_text: description (Full Description)
 - Bảng catalog_product_entity_int: manufacturer, status
 - Bảng catalog_product_entity_decimal: weight, price, special_price
 - Bảng catalog_product_entity_media_gallery: base_image, additional_images
 - Bảng cataloginventory_stock_item: qty (Quantity), is_in_stock (Stock Availability), manage_stock
 - Bảng catalog_product_website: Lưu thông tin về sản phẩm và website
 - Bảng eav_attribute: Lưu thông tin về các thuộc tính của sản phẩm (Attributes)
 - Bảng catalog_product_entity_varchar và catalog_product_entity_text: Lưu Meta Title và Meta Description
 - Bảng tag và tag_relation: Lưu Product Tags

2.	PRODUCT CATEGORIES:
#### Shopify:
 - Shopify sử dụng một cấu trúc dữ liệu đơn giản hơn cho các danh mục sản phẩm, thường được gọi là Collections. Các thông tin chính được lưu trữ trong bảng collections.
 - Các trường liên quan trong bảng collections gồm: id, title (Name), body_html (Description), published_at (Status), image, handle (URL), meta_title, meta_description.
#### Magento 2:
 - Magento 2 có một cấu trúc phức tạp hơn cho các danh mục sản phẩm. Thông tin về danh mục được lưu trữ trong hai bảng chính: catalog_category_entity và catalog_category_entity_varchar.
 - Các trường liên quan trong bảng catalog_category_entity gồm: entity_id, parent_id, path, position, level, children_count.
 - Các trường liên quan trong bảng catalog_category_entity_varchar gồm: entity_id, attribute_id, store_id, value (Name, Description, Meta Title, Meta Description).

3.	MANUFACTURERS:
#### Shopify:
 - Shopify không có một bảng dữ liệu riêng biệt cho nhà sản xuất. Tuy nhiên, bạn có thể sử dụng tính năng Product Tags hoặc Product Metafields để lưu trữ thông tin về nhà sản xuất.
#### Magento 2:
 - Magento 2 sử dụng bảng eav_attribute để lưu trữ thông tin về nhà sản xuất. Trường liên quan: attribute_id, entity_type_id, attribute_code (Name).

4.	TAXES:
#### Shopify:
 - Shopify lưu trữ thông tin về thuế trong bảng tax_rates và tax_rules.
 - Bảng tax_rates gồm các trường: id, country_code (Country), percentage (Percent).
 - Bảng tax_rules không có trường tương ứng với Tax Class, nhưng bạn có thể sử dụng Product Type hoặc Product Tags để phân loại sản phẩm theo loại thuế.
#### Magento 2:
 - Magento 2 lưu trữ thông tin về thuế trong bảng tax_calculation_rate và tax_calculation_rule.
 - Bảng tax_calculation_rate gồm các trường: tax_calculation_rate_id, tax_country_id (Country), tax_region_id, tax_postcode, code (Name), rate (Percent).
 - Bảng tax_calculation_rule gồm các trường: tax_calculation_rule_id, code (Name), tax_calculation_rate_id (Tax Rate), customer_tax_class_id (Tax Class).



