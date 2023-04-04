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
