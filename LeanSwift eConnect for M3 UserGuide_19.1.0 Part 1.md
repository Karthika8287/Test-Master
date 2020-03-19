# USER MANUAL

## LeanSwift eConnect

**for Infor M3 &amp; Magento**

    
**Part I – Configuration**

    
**Product Version 19.1.0**



**ECONNECT 19.1.0 USER MANUAL**

## GENERAL INFORMATION
## System Overview

**LeanSwift eConnect for Infor M3** provides a powerful, seamless integration between Magento and Infor M3 ERP. The product consists of a base Magento extension that extends standard Magento functionality and offers several transactions to ensure your eCommerce websites contain up-to-date information from your M3 ERP. There exist a number of optional add-on extensions too for additional functionality

**LeanSwift eConnect for Infor M3** is available for Magento Open Source and Magento Commerce and for Infor M3 version 7.x and above. It is also compatible with multi-tenant cloud editions of Infor M3 (CloudSuite).

**LeanSwift eConnect for Infor M3** employs a layered architecture to allow flexibility in supporting different versions of Magento and Infor M3 and to allow independent upgrades.


### Architecture

Prior to version 19.1.0, the product architecture included LeanSwift eLink as the integration/interfacing application for the Magento extension to communicate with Infor M3.

Version 19.1.0 includes the following:

1. Infor ION as the integration platform, an alternative to LeanSwift eLink  
2. Replace CRON jobs that pull information for syncing data between M3 and Magento/eConnect with event-based data push from M3 via ION/Eventhub/MEC  
3. Use ION REST API framework to make M3 API calls 

The new version will coexist with the older version of eConnect which uses LeanSwift eLink and all new installations of eConnect have the ability to choose the connection protocol to M3, that is, either eLink or ION.



**Architecture with LeanSwift eLink**

**Architecture with ION for multi-tenant Cloud M3**





**Transactions**

eConnect 19.1.0 includes the following set of standard transactions like its previous versions:

- Product Addition
- Product Information Sync
- Price Sync (Base &amp; Customer prices)
- Inventory Sync
- Customer Registration
- Customer Addition
- Customer Information Sync
- Customer Address Sync
- Order Creation
- Order Information Sync
- Shipment Sync
- Invoice Sync
- Order History
- Invoice History

These transactions can, if necessary, be modified and new transactions can be added to fulfill specific customer requirements.

With 19.1.0 we have included new features:
- BOD Mapping
- Initial Load / Import

**User interface**

During setup, the Magento Admin panel is used to configure which transactions that should be used and how they should function. There is also additional background configuration within the Connector.

**Validated Versions**

- Magento Commerce 2.3.1
- Magento Open Source 2.3.1
- Infor M3 13.4
- LeanSwift eLink 7.6.3
- RabbitMQ 3.6.10
- Infor ION Grid 12.0.2.0.20180308-135417.2
- ION Desk 12.0.24
- Event Hub 2.2.13
- Event Analytics 2.2.13
- MEC 11.4.3.0.9 201801090841-185
- M3 BOD Content Pack M3BODs\_15.5.0.5\_Content

## Points of Contact

This document and the software it describes are provided by LeanSwift Solutions Inc. For additional information regarding support, licensing, functionality etc. please contact LeanSwift Solutions Inc. via contact form at [http://www.leanswift.com](http://www.leanswift.com/)or email [info@leanswift.com](http://info@leanswift.com)

## Organization of the Manual

This manual is not intended to cover any standard Magento functionality or user experience. The Magento user experience is customized and slightly different in each eCommerce implementation – though the general workflow issimilar.

This manual describes the configuration of LeanSwift eConnect for Infor M3. For a detailed description of the standard transaction, please refer to Part II of the User Manual.

_Section 2_ includes the configuration required within LeanSwift eConnect Magento extension via the Magento Admin panel.

## Acronyms and Abbreviations

ERP – Enterprise Resource Planning 
B2B – Business to Business
B2C – Business to Consumer
RMA – Return Materials Authorization

## CONFIGURATION

## Magento Configuration

To support the use of LeanSwift eConnect for Infor M3, configuration is required within Magento, in LeanSwift eLink, in Infor OS and also within the M3 ERP system is required. This section covers the configuration within _Magento_.

Log in to Magento Admin Panel using the URL provided to you and the applicable user credentials.

## System Menu

### Configuration

To access the LeanSwift Configuration, click the **Leanswift** tab, and select the **Configuration** option under **econnect-ION**.



Also pay attention to which configuration scope you&#39;re working under.



For further information about _Configuration scope_ in Magento, please refer to the following article:

[http://www.magentocommerce.com/knowledge-base/entry/understanding-store-scopes](http://www.magentocommerce.com/knowledge-base/entry/understanding-store-scopes)

### Configuration/LeanSwift

Navigate to the **LeanSwift Solutions** sub-menu down in the left-hand side configuration menu.

Here, there will be several sections under the LeanSwift sub-menu.





### Configuration/LeanSwift/eConnect

The **eConnect-ION** section contains the vast majority of the settings for base eConnect, and the details of each group is covered in the following sections of this document.

The following sections are included in the eConnect configuration:





## eConnect-General

The General section contains a number of basic settings that are generic for this instance of eConnect.





**Service Configuration**

M3 Connection Protocol: Provides a choice for the admin to choose between Leanswift eLink/ION version of eConnect. There are 2 options, Leanswift eLink and ION. eConnect picks the configuration based on the option chosen.

**General Configuration**

**Email**

Define the e-mail address that will be used for error alerts if exceptions were to occur in Magento and when any transaction in eConnect is not working due to service being down

**Use M3 order history**

This parameter refers to the retrieval of order history from M3 from Magento front-end.

Select &quot;Yes&quot; to retrieve the order history from the ERP system in real-time when the user selects Order History in My Account. This will make order history seamless between Magento and the ERP and any order changes in the back-end ERP will be displayed in Magento instantly.

Select &quot;No&quot; to only use the order history from Magento when the user selects Order History in My Account.

**Display Invoice**

Set this option to &#39;Yes&#39; in order to retrieve Invoice history details from M3. Please note that this does not apply to the B2C configuration when a single customer# in M3 is used for all orders.



In this case, the invoice history from Magento is always displayed by default.

**Debug/log data**

Select &quot;Yes&quot; to log additional information in Magento. This setting is recommended in test but should be set to &quot;No&quot; in production to improve performance.

## eConnect-ION

## General Configuration

**ION API Service URL:** ION service URL is entered here. This establishes the connection to ION.



## Basic Data

The **Basic Data** section of the configuration contains a number of key settings needed for the various transactions within LeanSwift eConnect.



**Company**

The default company within M3. Setting can be defined on Default or Store level.



**Division**

The default division within M3. Setting can be defined on Default or Store level.

**Facility**

The default facility within M3. Setting can be defined on Default or Store level.

**Warehouse**

The default facility within M3. Setting can be defined on Default or Store level. This setting is currently used as input to all transactions except the Order Entry.

**Price List**

This refers to the Price List within M3 from which the list price/MSRP/Retail price is synchronized for a site. This setting is optional and can be left blank. Also note that if prices for a site should be synchronized, the &#39;Price&#39; attribute must also be included as part of the mapping within the &#39;Production Synchronization&#39; setup that&#39;s covered later in this manual.

**Currency code**

Only required if &#39;Price code&#39; is filled in and is then used to ensure the right price list in M3 is used for price synchronization.

**Order type**

The default order type to use for Order creation. This setting can be managed on a Default or Website level.

**Document Class**

  The default document class is Co02. It is the class used while sending Order comments to M3



## Authentication

The **Authentication** group contains the settings related to the web service authentication using the OAuth2.0 standard that eConnect employs.

This section is configured by LeanSwift during product installation.





To ensure the security of eConnect, OAuth2.0 is always enabled by default.

The M3 User is the user with which we connect to ION API&#39;s

We have a &#39;Test connection&#39; button to verify if connection is up

## Shipping Method

This section manages the mapping between the Shipping methods that have been enabled within Magento (_Leanswift &gt; eConnect-ION Configuration &gt; Sales &gt; Shipping Methods_) and the Delivery method- &amp; term within M3.



To add an additional mapping entry, simply press the &#39;Add&#39; button, and select the Magento Shipping Method value to map

Then, in the right two columns (M3 Delivery Method &amp; M3 Delivery Term) – key in the M3 values to which the Shipping method should be mapped:



Following this, remember to save the configuration by pressing &#39;Save Config&#39; at the top of the page.



## Product Addition/ Synchronization

There exists functionality to conveniently map your M3 items to your Magento webshop. _Leanswift &gt; econnect-ION &gt; Configuration &gt;Product Addition/Synchronization. In the current version, simple and configurable products are supported using this process, for all other product types, the default Magento process of importing via CSV is in place.

You can control the Product sync in website level by choosing Yes/No option in the Enable field. Each of the features, addition of new items, and syncing of existing can be controlled independently of each other.

Set Enable to Yes to enable this feature.

Apart from this, Addition and Sync can be turned on/off individually.

The Dropdown attributes that needs to be synced can be added in the Dropdown attributes field. Multiple values can be selected.

Batch size and Sync from Date features are removed in this version as sync happens instantly unlike in eLink version which requires a cron to be triggered.

The New product status should be set to No to ensure the products do not appear in the webshop and set to Yes to appear.

&#39;Style SKUs as Configurable Products&#39; can be set to Yes if we want style items and can be set to No      to save them as simple items



### Product attribute mapping

In order to ensure that the solution can deal with the flexibility and complexity of M3, the configuration allows you to specify what values from M3 should be mapped to the attributes which you have defined in magento. A Default field is provided to map a default value to any of the M3 field.



**Product Addition conditions:**

As the most common scenario faced is that your M3 instance will contain far more items than you wish to have available in your webshop, eConnect comes with the ability to provide configurable criteria for selecting which items to include from M3.





In Addition to this, we also have option to choose if it is &#39;Any/All&#39; of all conditions.

The main product tables are MITMAS, MITBAL and MITFAC.





### Product Synchronization - Item Disabling
Configuration is provided to Enable or Disable the products in Magento.
Set yes to Disable the product status and map the required conditions.



## Product Synchronization - Category Mapping

When items are imported into Magento, they will need to have at least one product category to which they will be associated with. When this information is available in M3, this can be used to avoid duplication of record maintained.



The category mapping is flexible enough to allow for more than one field in M3 to define which category it should belong to in Magento. The first step is to define the order and which fields in M3 will indicate category. The M3 Category source value should be entered in one continuous string.

Once the source is entered, Items gets created into magento and the categories are created based on Source.

The first source value acts as a Parent and rest of the source value forms sub-categories.

Once Category source is defined, any changes can cause abnormality in the behavior of product Addition/sync.In addition, a default category can be used for values which are missing values in the fields which have been defined for category mapping.





## Product Synchronization - AttributeSet Mapping

Magento uses the concept of attributes sets which allows products with similar features to be grouped and share a common set of attributes. Shoes for example would maybe need different attributes than the rental heavy equipment item. In order to ensure that items are imported and synced to Magento using the correct set of attributes, configuration is provided to assist in defining what M3 values indicate the product attribute set which the item will belong to.





Similar to category mapping, a feature has been provided to define the behavior for attribute sets which have changed or those which do have a matching M3 value as has been defined.

   To enable this feature &#39;Change AttributeSet for existing products&#39;is set to Yes



## Customer General Configuration

This section now contains the key parameters for how to handle customer creation, both for a B2B- and a B2C site.

NOTE! The &#39;Customer Template ID&#39; field has dual function depending on whether the Customer Registration feature is used or not. For a single site, these features are mutually exclusive in that one is intended for B2B- and the other for B2Cuse.

**Enable Registration**

This feature is intended for a B2B setup where new customers are allowed to register themselves on the front-end.

If **Enable Registration** is set to &#39;Yes&#39;, eConnect will remove the **Create New Customer** parameter as this indicates the site being configured is a B2B site where every customer always exists already when an order is placed.



When **Enable Registration** is set to &#39;Yes&#39;, this indicates that as new customers register from the Magento front-end [customer registration extension not supplied as part of eConnect], a customer record is added in Magento – and a customer in a preliminary status (status 10) is created within M3.

A manual process is assumed within M3, where a Customer service/Accounting responsible would review these preliminary customers (credit checks etc.) – and if they are approved as a new customer the status in M3 is manually changed to active (20). While the customer status in M3 is preliminary (10), the customer in question can&#39;t place an order within Magento (eConnect performs a real-time check against M3 during the checkout process to validate the customer status). Products can be added to cart and the cart saved, but the checkout process can&#39;t be completed.

Setting **Enable Registration** to &#39;No&#39; disables the registration feature completely, which then in turn enables the Create New Customer parameter:
