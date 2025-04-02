# Mediaclip Custom Cart Integration - Dawn Theme Sample

This repository contains a sample implementation of the Mediaclip custom cart integration based on Shopify's Dawn theme. It serves as a practical reference for developers who need to implement Mediaclip personalization features with custom cart functionality.

## Overview

While Mediaclip offers built-in theme blocks for handling personalized products in Shopify carts, this sample demonstrates how to create a custom implementation when more specific requirements exist. The Dawn theme has been adapted to showcase:

- Custom cart line item display for Mediaclip projects
- Integration with the Mediaclip Shopify JavaScript Cart API
- Proper quantity handling for personalized products
- Pre-checkout validation implementation
- Error messaging for validation issues
- Project thumbnail management

## Purpose

This sample theme is intended as a reference implementation rather than a production-ready solution. It illustrates key integration points and code patterns that developers can adapt to their own themes and specific requirements.

## Key Implementation Files

- `main-cart-items.liquid`: Modified cart template and inject custom JavaScript
- `main-cart-footer.liquid`: Disable the Checkout button by default

## Implementation Highlights

### Cart Initialization

```javascript
let onMediaclipReady = async () => {
    let mediaclipShopify = window.mediaclipShopify;
    let mediaclipCartApi = mediaclipShopify.getCartApi();
    await mediaclipCartApi.init(...);
    // ...
}

document.addEventListener("DOMContentLoaded", async () => {
  if (window.mediaclipShopify === undefined) {
    document.addEventListener('OnMediaclipShopifyReady', async () => {
      await onMediaclipReady();
    })
  } else {
    await onMediaclipReady();
  }
});
```
### Checkout Validation

```javascript
checkoutButton.addEventListener('click', async (event) => {
  // Prevent default checkout behavior
  event.preventDefault();
  // Run validation
  let validationResult = await mediaclipCartApi.executeMediaclipValidationAndFixCart(false);
  // Handle validation results
  // ...
});
```

## Important Notes

- This sample is based on Shopify's Dawn theme and demonstrates adaptation techniques
- All code should be reviewed and adapted to your specific theme and requirements
- The sample focuses on cart functionality and assumes Mediaclip is properly installed
- This is not intended as a drop-in solution but as a reference implementation

## Documentation

For comprehensive details on the Mediaclip Shopify JavaScript Cart API, please refer to the [official Mediaclip documentation](https://docs.mediaclip.com/shopify/js-api/).

## Support

This sample repository is provided as a reference implementation. For support with your own Mediaclip integration, please contact the Mediaclip support team.