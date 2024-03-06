# Snipe-it-Inventory

![flow](http://www.plantuml.com/plantuml/png/VP71RiCW38RlFCL_J5-XFQnJJvDscBGdeCHPF150sAd6suyKQOcYQ2TRy7tu5xwAsgppvCspCUVFfLoCuG7Tcu0L5caimivwnFitENqvGKSAw0h9oG0hEWlrc1FYWpAK9zgZmFdchGWF1LPmYq7coTuzNPwNeZ7LXhmGkX2RiKaIG3zAELYFdXxi3jxVyXoKldA5DIuOKkR9vlAFkyltwXo9n5nQl4soO_w3CgUHwiW_8VGyc0DrDqY4j3ghiVv6ErZrdVhEZe9GbPlGy6ijorP_0G00)

Documentation &amp; instrunctions for Lba Snipe-it inventory

by Gregorio Orlando

## Documentation For Snipe-it Graphic Interface

### Categories

Categories are used by both assets and accessories. Categories describe the general type of asset or accessory, such as “wireless keyboards”, “laptops”, and so on.

>Contains attributes that are inherited by both the assets and accessories that belong to them, such as _whether to email the end-user when an item has been checked out to them, whether to require the user to click on a link to show that they have received the asset or accessory, and whether or not the user should be emailed a EULA._

Every asset and accessory needs to belong to a category, so you’ll need to set these up before adding assets.

#### Create Category:

1. Click on the gear icon to open Settings
2. Click on the Categories to get to the main Categories section
3. Create your new Categories _(which you will need to select when you are creating your assets)_.

>Alternative, you can create Categories on the fly if you import via CSV.

## Asset Tags

unique identifier for assets within your system. Each one must be unique, and is often used in conjunction with Asset Labels. They identify each unique piece of hardware so that you know which specific device it is.

For users who don't need asset labels, the unique serial number of each device is often used as the asset tag, or you can turn on auto-incrementing asset tags in *Admin > Settings*, which will generate a unique asset tag for you when you create new assets.

## Asset Labels

Go to any of the asset listing views (Ready to Deploy, Deployed, etc) and use the checkboxes in the leftmost column to select the assets you'd like to generate labels for. Once you've finished your selection, scroll down to the bottom of the asset listing table, and select "Generate Labels" from the dropdown list.

Then you can print these and have them next to the hardware.

## Asset Models

Every asset needs an asset model, so setting these up next will help you start adding assets. Asset models can be things like the make and model of a laptop or desktop machine
>ES: Apple 13″ Retina

When you create new assets, you’ll select whichever asset model makes sense.

Asset models are important because they carry certain attributes which are inherited by the assets you create, such as depreciation type, end of life, and whether or not to show MAC address fields on the asset.

Individual assets can be marked as requestable, and asset models can also be marked as requestable, which allows users within Snipe-IT to request a specific asset, or any asset that matches the asset model they require.

## Barcode & QRcode

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
>FullName,Email,Username,itemName,Category,ModelName,Manufacturer,Model Number,SerialNnumber,AssetTag,Location,Notes,Purchase Date,PurchaseCost,Company,Status,Warranty,Supplier

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

