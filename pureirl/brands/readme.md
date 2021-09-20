# PureIRL Network by PureMoto: Integration for Brands
 
The PureIRL Network empowers local brick & mortar stores by surfacing inventory information directly to those customers at peak engagement. [Learn more.](https://pureirl.com)

This document services as documentation for enabling Brand Partner websites to display live inventory levels for their products in local brick & mortar stores.

### 1. Provide products and mapping file

Please send a copy of the SKUs on your website containing the Product URL, Product Name, Image URL  SKU/Part Number and a column for each alternate sku that shops use to reprsent your product (for example distributor sku). Send this to [support@pureirl.com](support@pureirl.com). Once this step is completed you will be sent a Site ID which is needed for Step 2.

### 2. Install The PureIRL javascript snippet

The PureIRL snippet is a block javascript code that needs to be placed in your website product page template. Copy and paste it into your product page template above the closing </body> tag. Then, replace the SITEID ########-####-####-####-########## with the ID that was provided to you.

##### Snippet:

```js 
<script>(function(){var e=window,o=e.PureIRL=e.PureIRL||[];if(!o.init)if(o._isLoaded)e.console&&console.error&&console.error("PureIRL snippet included twice.");else{var n=document;o._isLoaded=!0,o.load=function(){var e=n.createElement("script");e.type="text/javascript",e.async=!0,e.src="https://puremoto.com/irl/api/embed";var o=n.getElementsByTagName("script")[0];o.parentNode.insertBefore(e,o)},o.VERSION="0.0.1",o.SITEID="########-####-####-####-##########",e.addEventListener("load",()=>o.load("panel"),!1)}})();</script>
```

### 3. Enable ‘Find in store’ button / SKU data attribute

Next you will create an button and action for your website visitors to launch the `Find in store` experience along with a unique SKU for a variant (i.e. size/color/specific fitment).

The SKU should be added to the button as a data attribute in the format: data-pureirl-sku="[variant sku]"

##### Sample:
```html
<button data-pureirl-sku="2010020-12-10">Find in-store</button>
```

You can see a live example of this using the TRY IT OUT call to action [here](https://pureirl.com/irl/partners)

### Download a working example:

Here is a working example which can be installed to run locally during setup and testing
[puremoto-irl-local.zip](https://github.com/thepurecollective/developer/blob/f1b9d44a967459c399ffe3f3ee9a33134c805ae9/irl/brands/puremoto-irl-local.zip).

### Next Steps

* If your products are found in dealers using a different SKU (such as one or several different) distributor skus, you will need to provide a mapping file to [support@pureirl.com](support@pureirl.com) containing the sku you use on your website mapped to the various skus that dealers may be using to sell this product. This can be provided in csv format and will need to be updated each time new products (please reach out to our team if you would like to automate the updates). 

* At time of implementation you provide the following information for skinning of the widget in the form of primary and secondary color using [RGB](https://www.w3schools.com/colors/colors_rgb.asp) values to [support@pureirl.com](support@pureirl.com).

### FAQs

##### Can I test on my local machine?
Your Site ID is restricted to your brand website root domain. You can test using (like in the working example) localhost:3001 or localhost:3002 for testing purposes. If you have a staging or development site you would like to add to the whitelist - please provide that URL to your account manager.

##### We use React/js and the script loads before we render the user selected SKU. How can we make this work?
In this case you can call ```window.PureIRL._reset()``` after you know that the attribute has been rendered.

For any additional questions, plese contact [support@pureirl.com](support@pureirl.com).