# Snipe-it-Inventory

![flow](http://www.plantuml.com/plantuml/png/VP71RiCW38RlFCL_J5-XFQnJJvDscBGdeCHPF150sAd6suyKQOcYQ2TRy7tu5xwAsgppvCspCUVFfLoCuG7Tcu0L5caimivwnFitENqvGKSAw0h9oG0hEWlrc1FYWpAK9zgZmFdchGWF1LPmYq7coTuzNPwNeZ7LXhmGkX2RiKaIG3zAELYFdXxi3jxVyXoKldA5DIuOKkR9vlAFkyltwXo9n5nQl4soO_w3CgUHwiW_8VGyc0DrDqY4j3ghiVv6ErZrdVhEZe9GbPlGy6ijorP_0G00)

Documentation &amp; instrunctions for Lba Snipe-it inventory

by Gringo & Daniel


# Table of Contents

1. [Snipe-it-Inventory](#snipe-it-inventory)
   - [Documentation & Instructions for Lba Snipe-it inventory](#documentation--instrunctions-for-lba-snipe-it-inventory)
      - [1. ASSETS](#1-assets)
      - [2. LICENSES](#2-licenses)
      - [3. ACCESSORIES](#3-accessories)
      - [4. CONSUMABLES](#4-consumables)
      - [5. COMPONENTS](#5-components)
      - [6. PEOPLE](#6-people)
      - [7. Settings](#7-settings)
         - [7.1 Categories](#71-categories)
         - [7.2 Assets Models](#72-assets-models)
         - [7.3 Locations](#73-locations)
      - [8. QR code](#8-qr-code)
   - [Importing Asset and More](#importing-asset-and-more)
   - [Usage](#usage)
      - [Identify Classification](#identify-classification)
         - [ES 1](#es-1)
         - [ES 2](#es-2)
         - [ES 3](#es-3)
      - [User experience](#user-experience)



[Presentation link](https://www.canva.com/design/DAF-ptVJ3W0/7udp7TozioKCdRgNQnhQdg/edit?utm_content=DAF-ptVJ3W0&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

[AI assisten for Snipe-IT](https://www.phind.com/search?home=true)

## Documentation For Snipe-it Graphic Interface

### 1. ASSETS
Items of value that an organization owns and uses for its operations. They can include a wide range of items.
Assets can contain other categories such as licenses, accessories, consumables, and components.

Examples:
- Laptops
- Desktops
- Servers
- Mobile phones

### 2. LICENSES
Digital or physical permissions that grant the user the right to use software or services.

Examples:
- Microsoft Office licenses
- Adobe Creative

### 3. ACCESSORIES
Peripherals or additional hardware that are not integral to the main function of a device but are necessary for its operation. They are typically used alongside devices for enhanced functionality or user experience.

Examples:
- Mice
- Keyboards
- Monitors

### 4. CONSUMABLES
Reusable items. Unlike accessories, consumables are used up and need to be replaced once they are depleted. subset of assets but are specifically focused on items that are used up and need to be tracked and replaced.

Examples:
- Toner cartridges
- Ink cartridges
- Paper

### 5. COMPONENTS
Parts of a larger asset or system that are essential for its operation but are not the main device themselves.

Examples:
- CPUs in computers
- RAM sticks
- Hard drives

### 6. PEOPLE
Users or employees who are assigned to assets or are responsible for their use and maintenance. This category is crucial for tracking who is using what and ensuring that assets are allocated and used appropriately.

Examples:
- Edu
- Botzo team

### 7. Settings

Under settings in dashbar you can find 3 main aspects/fields that allow for a structured approach to asset management, ensuring that your inventory is well-organized, easily tracked, and maintained.

#### 7.1 Categories
Used to group assets, licenses, accessories, consumables, and components into logical groups based on their function, type, etc.. Example: hardware, software

Categories are used by both assets and accessories. Categories describe the general type of asset or accessory, such as “wireless keyboards”, “laptops”, and so on.

>Contains attributes that are inherited by both the assets and accessories that belong to them, such as _whether to email the end-user when an item has been checked out to them, whether to require the user to click on a link to show that they have received the asset or accessory, and whether or not the user should be emailed a EULA._

Every asset and accessory needs to belong to a category, so you’ll need to set these up before adding assets.

>Alternative, you can create Categories on the fly if you import via CSV.

#### 7.2 Assets Models
Asset Models act as templates for creating new assets. They define common attributes that are shared by all assets of a particular type, such as the manufacturer, category, and custom fields.

--> STANDARDIZATION

Every asset needs an asset model, so setting these up next will help you start adding assets. Asset models can be things like the make and model of a laptop or desktop machine.

When you create new assets, you’ll select whichever asset model makes sense.

Asset models are important because they carry certain attributes which are inherited by the assets you create, such as depreciation type, end of life, and whether or not to show MAC address fields on the asset.

Individual assets can be marked as requestable, and asset models can also be marked as requestable, which allows users within Snipe-IT to request a specific asset, or any asset that matches the asset model they require.

#### 7.3 Locations
Specify the shelf in the lab. A user can navigate the lab as an IP address, going to shelf 2, row 4 column 5 (2.4.5).

### 8. QR code

QR codes, when scanned on a mobile device using a QR scanner app, will open the asset details page of the asset whose QR code was scanned.

## Importing Asset and More

 Always run a backup (Admin > Backups) before running the importer, so that you have a clean place to roll back to if something goes wrong.

You can **import CSV** files through the web interface.

```
php artisan snipeit:import path/to/your/file.csv
```

The importer reads the first row of the CSV file to determine what each column is _(The value in the header cell MUST MATCH one of the following options)_.

Please make sure there are no leading or trailing spaces in the header column names, and no blan

### Sample Asset Import
>Full Name,Email,Username,item Name,Category,Model Name,Manufacturer,Model Number,Serial number,Asset Tag,Location,Notes,Purchase Date,Purchase Cost,Company,Status,Warranty,Supplier

| Field             | Example Data         | Required | Notes                                                                                                                    |
|-------------------|----------------------|----------|--------------------------------------------------------------------------------------------------------------------------|
| Full Name         | Firstname Lastname   | No       | No commas. First name first, last name last                                                                              |
| Email             | you@example.com      | No       | If empty, will be generated using the email_format and domain you provide in Admin > Settings                           |
| Username          | yourname.lastname   | No       | If empty, will be generated using the username_format you provide in Admin > Settings                                  |
| Model Name        | MBP Retina 13-inch   | Yes      | Created if it doesn't exist                                                                                              |
| Manufacturer      | Apple                | No       | Created if a value is provided but it doesn't yet exist                                                                   |
| Model Number      | MacbookPro12,1       | No       |                                                                                                                          |
| Serial            | C20095805496869045H6 | No       |                                                                                                                          |
| Asset Tag         | KJH90890             | Yes      |                                                                                                                          |
| Notes             | Karens old machine   | No       |                                                                                                                          |
| Image             | Filename.jpg         | No       | If Present, this is the basename of the image associated with the item. Images must be manually uploaded to public/uploads/assets. |
| Status            | Ready to Deploy      | No       | A status label applied to the item. Created if it doesn't exist. If you leave this blank and provide a username, it will automatically be checked out to that user. If you leave this blank without a user, it will automatically be set to Ready to Deploy. |
| Warranty months   | 15                   | No       | Time in months until warranty expires                                                                                    |
| Checkout Type     | user                 | No       | Should we checkout to a user or to a location? Defaults to user, and user is implied if the field does not exist.      |
| Checkout Location | Planet Mars          | No       | Name of Location to be checked out to if checkout_type is location. This Location will be created if it does not exist. |
| Order Number      | PO-007               | No       | The Purchase Order # for the asset. Will be shown next to Purchase Cost. This Purchase Order will be created if it does not exist. |
| Supplier          | Mike's Tech Shop     | No       | Supplier name                                                                                                            |
| Item Name         | Karen 2015           | No       |                                                                                                                          |
| Company           | MacandDonalds        | No       | Created if it doesn't exist. Leave this blank if you don't need to support multiple companies.                          |
| Category          | Laptop               | Yes      | Created if it doesn't exist                                                                                              |
| Location          | San Diego            | No       | Created if it doesn't exist                                                                                              |
| Purchase Date     | 2015-01-12           | No       | Can take any date format that can be translated by strtotime()                                                           |
| Purchase Cost     | 2999.99              | No       | Cost of asset (no commas or currency symbols)                                                                            |



>ES: _Bonnie Nelson,bnelson0@cdbaby.com,bnelson0,eget nunc donec quis,quam,massa id,Linkbridge,6377018600094472,27aa8378-b0f4-4289-84a4-405da95c6147,970882174-8,Daping,"Curabitur in libero ut massa volutpat convallis. Morbi odio odio, elementum eu, interdum eu, tincidunt in, leo. Maecenas pulvinar lobortis est.",2016-04-05,133289.59,Alpha,Undeployable,14,Blogspan_

### Sample Licenses Import
>Name,Email,Username,Item name,Category,serial number,manufacturer,purchase date,purchase cost,purchase_order,order number,Licensed To Name,Licensed to Email,expiration date,maintained,reassignable,seats,company,supplier,notes

| Field          | Example Data        | Required | Notes                                                    |
|----------------|---------------------|----------|----------------------------------------------------------|
| Item Name      | Karen 2015          | No       |                                                          |
| Company        | MacandDonalds       | No       | Created if it doesn't exist. Leave this blank if you don't need to support multiple companies. |
| Category       | Laptop              | Yes      | Created if it doesn't exist                              |
| Location       | San Diego           | No       | Created if it doesn't exist                              |
| Purchase Date  | 2015-01-12          | No       | Can take any date format that can be translated by strtotime() |
| Purchase Cost  | 2999.99 (no commas or currency symbols) | No  | Cost of asset                                            |


>ES: _Aenean fermentum. Donec ut mauris eget massa tempor convallis. Nulla neque libero, convallis eget, eleifend luctus, ultricies eu, nibh."_

### Sample Accessories Import
>ItemName,PurchaseDate,PurchaseCost,Location,Company,OrderNumber,Category,Requestable,Quantity

| Field          | Example Data        | Required | Notes                                                    |
|----------------|---------------------|----------|----------------------------------------------------------|
| Item Name      | Karen 2015          | No       |                                                          |
| Company        | MacandDonalds       | No       | Created if it doesn't exist. Leave this blank if you don't need to support multiple companies. |
| Category       | Laptop              | Yes      | Created if it doesn't exist                              |
| Location       | San Diego           | No       | Created if it doesn't exist                              |
| Purchase Date  | 2015-01-12          | No       | Can take any date format that can be translated by strtotime() |
| Purchase Cost  | 2999.99             | No       | Cost of asset (no commas or currency symbols)            |
| Quantity       | 15                  | No       | Amount of item in stock. Defaults to 1                   |


>ES: _Walter Carter,09/01/2006,,metus. Vivamus,Macromedia,J935H60W,Customers,False,278_

### Sample Consumables Import
>Item Name,Purchase Date,Purchase Cost,Location,Company,Order Number,Category,Requestable,Quantity

| Field          | Example Data        | Required | Notes                                                    |
|----------------|---------------------|----------|----------------------------------------------------------|
| Item Name      | Karen 2015          | No       |                                                          |
| Company        | MacandDonalds       | No       | Created if it doesn't exist. Leave this blank if you don't need to support multiple companies. |
| Category       | Laptop              | Yes      | Created if it doesn't exist                              |
| Location       | San Diego           | No       | Created if it doesn't exist                              |
| Purchase Date  | 2015-01-12          | No       | Can take any date format that can be translated by strtotime() |
| Purchase Cost  | 2999.99             | No       | Cost of asset (no commas or currency symbols)            |
| Quantity       | 15                  | No       | Amount of item in stock. Defaults to 1                   |


>ES: _arcu.,09/22/2007,48.34,ornare,Google,N961E50A,Amoxicillin,False,252_

### Sample Components Import
>Item Name,Purchase Date,Purchase Cost,Location,Company,Order Number,Serial number,Category,Quantity

| Field          | Example Data        | Required | Notes                                                    |
|----------------|---------------------|----------|----------------------------------------------------------|
| Item Name      | Karen 2015          | No       |                                                          |
| Company        | MacandDonalds       | No       | Created if it doesn't exist. Leave this blank if you don't need to support multiple companies. |
| Category       | Laptop              | Yes      | Created if it doesn't exist                              |
| Location       | San Diego           | No       | Created if it doesn't exist                              |
| Purchase Date  | 2015-01-12          | No       | Can take any date format that can be translated by strtotime() |
| Purchase Cost  | 2999.99 (no commas or currency symbols) | No  | Cost of asset                                            |


>ES: __

### Sample Users Import
>First Name,Last Name,email,User name,Location,Phone Num,Job Title For User,Employee Number,Company

| Field          | Example Data        | Required | Notes                                                    |
|----------------|---------------------|----------|----------------------------------------------------------|
| Item Name      | Karen 2015          | No       |                                                          |
| Company        | MacandDonalds       | No       | Created if it doesn't exist. Leave this blank if you don't need to support multiple companies. |
| Category       | Laptop              | Yes      | Created if it doesn't exist                              |
| Location       | San Diego           | No       | Created if it doesn't exist                              |
| Purchase Date  | 2015-01-12          | No       | Can take any date format that can be translated by strtotime() |
| Purchase Cost  | 2999.99 (no commas or currency symbols) | No  | Cost of asset                                            |


>ES: _Karalee,Carroll,kcarroll5@devhub.com,kcarroll5,Huaidian,86-(303)287-0739,Civil Engineer,1530903416,Schuster LLC_




## Usage

### Identify Classification

#### ES 1
Example 1: A Laptop
1. Is it a physical object? Yes, a laptop is a physical object.
2. Is it used up over time? No, while a laptop may wear out over time, it is not 'consumed' like printer paper or ink.
3. Is it an external device? No, a laptop is a standalone device, not an external addition to another device.
4. Therefore, the laptop is classified as an Asset.
#### ES 2
Example 2: Ink Cartridge
1. Is it a physical object? Yes, an ink cartridge is a physical object.
2. Is it used up over time? Yes, an ink cartridge is used up as it prints and needs to be replaced.
3. Therefore, the ink cartridge is classified as a Consumable.
#### ES 3
Example: A Raspberry Pi
1. Is it a physical object? Yes, a Raspberry Pi is a physical object.
2. Is it used up over time? No, a Raspberry Pi does not get consumed like printer paper or ink; it may wear out but is not used up in the traditional sense of a consumable.
3. Is it an external device? No, while it can be part of a larger system, a Raspberry Pi is typically a standalone device or a core component for various projects, not an external addition like a peripheral.
4. Therefore, the Raspberry Pi is classified as an Asset.

### User experience

1. Create your profile (or the profile of your team)
2. Check-out items:

    a. Navigate to the item in the Snipe-IT inventory.

    b. Select "Checkout" and choose the user to whom the item is being checked out.

    c. Optionally, specify the expected return date and any additional notes.

    d. Confirm the action to check out the item.

3. Check-in items:
    a. Navigate to the item in the Snipe-IT inventory.
    b. Select "Checkin" and choose the user to whom the item is being returned.
    c. Optionally, provide any notes about the condition of the item or the reason for the check-in.
    d. Confirm the action to check in the item.
4. Search items
5. Create user inventory
