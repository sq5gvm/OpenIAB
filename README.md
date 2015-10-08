This is a cloned repository from [OpenIAB](https://github.com/onepf/OpenIAB). Master branch is just a clone of the current version (as of writing this, 0.9.8.7). Checkout  [developer](https://github.com/lumley/OpenIAB/tree/developer) branch for the following:
 * a working implementation for [Cafe Bazaar]()
 * a [way to track the currency of a purchase for Amazon store](#amazon_currency_tracking)

OpenIAB is an open source library which provides an easy way for the developers to develop their apps/games in a way that one APK will work in all the stores and automatically use the right in-app purchase API under each store. OpenIAB also provides an open in-app billing API that stores could implement to support all the built APK files using this library. Currently there are already 5 stores that support the Open API: Yandex.Store, SlideME, Appland, Aptoide and AppMall. The open stores don't need extra libraries to be included with your project, only the OpenIAB core is required to support all of them. 

OpenIAB supports the following stores:
* Open Stores (stores working via Open Protocol)
  * Appland
  * Aptoide
  * AppMall
  * SlideMe
  * Yandex.Store
*  Wrapped Stores (stores that don't work via Open Protocol but wrapped with the same interface)
  * Google Play
  * Samsung Apps
  * Nokia Store
  * Amazon AppStore
  * Cafe Bazaar

For detailed instructions, please visit [our wiki](https://github.com/onepf/OpenIAB/wiki). 
Contact akarimova@onepf.org if you have any business comments or questions about the library.

## <a name="amazon_currency_tracking">How to track the currency from a purchase from Amazon</a>
In order to avoid changing too much the behavior of OpenIAB's store, we have added the market's locale following the country ISO Code ISO_3166-1 (two capital letters that specify only country but not region) to the original JSON receipt built by OpenIAB.

So the _Purchase_ object received in _IabHelper.OnIabPurchaseFinishedListener_ should have the following original JSON:

    {
    "orderId"           : "purchaseResponse.getRequestId"
    "productId"         : "receipt.getSku"
    "purchaseStatus"    : "purchaseRequestStatus.name"
    "userId"            : "purchaseResponse.getUserId()" // if non-null
    "marketCountryCode" : "purchaseResponse.getMarketplace()" // if non-null <--- new field
    "itemType"          : "receipt.getItemType().name()" // if non-null
    "purchaseToken"     : "receipt.getReceiptId()"
    }
Where _marketCountryCode_ is the value for [userData](https://developer.amazon.com/public/apis/earn/in-app-purchasing/javadocs-v2/in-app-purchasing-2.0-api-reference).getMarketplace() from Amazon. 

## Rules for contributing
Please provide your contributions to the original OpenIAB repository.

## License

    Copyright 2012-2015 One Platform Foundation

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
 
