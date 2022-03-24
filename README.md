OpenStore_DnnIdx Plugin
-----------------------

This DNN module is a plugin for OpenStore v4.  It enables products to be indexed into the standard DNN search database.

It requires a minimum version of DNN9.7.1 and OpenStore 4.1.5.

Installation
------------

- Install the OpenStore_DnnIdx_*.*.*_Install.zip as a normal DNN module, through the DNN extension.
- Go into the NBS Back Office>Admin>Plugins. Edit and activate the "IBF Index DNN Search" plugin listed.
- Ensure the NBS scheuler is running on the DNN scheduler. https://doc.openstore-ecommerce.com/#11498

Operation
---------

The OpenStore_DnnIdx plugin indexes products into the DNNsearch index by using the DNN scheudler.  The NBS scheduler module must be running on the DNN scheduler for the plugin to work.
If the NBS store debug setting is turned on, the plugin will clear down ALL page indexes for the portal (Including all tabs loaded by other modules) and reindex only products.

The DNN 9 index does tend to be very quick and in normal operation only changed products will be updated in the indexed, to avoid performace issues.

Due to performace and restrictions with the the DNN search provider API the index process does not remove deleted products from the DNN index (unless in debug mode).
To remove deleted product from the index you can either place the store in debug mode and run the OpenStore scheduler manually (or wait for the reindex) or use the DNN>Admin>Search-Admin option to reindex the search. 

NOTE: The OpenStore module should not be left in debug mode during high peak hours.

Search Type:  The OpenStore_DnnIdx uses a tab searchtype.
Although each product is not a tab in DNN, the resulting detail is regarded as a tab with a uinque URL.
For this reason we use SearchHelper.Instance.GetSearchTypeByName("tab").SearchTypeId

Customization
-------------

If you need to change the information that's being indexed, you can alter /Themes/config/default/dnnidxdetail.cshtml for that.

Like al razor scripts in OpenStore, you're advised to copy this file over to /Portals/?/Themes/config/default/dnnidxdetail.cshtml and change it there.


