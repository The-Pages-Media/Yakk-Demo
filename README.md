# Yakk 🤗 The Pages Media

## Preview Theme

URL: `https://tpm-yakk.myshopify.com/`

Password: `yakkyakkyakk`

## Modifications

Because there is a lack of standardization across Shopify websites when it comes to cart drawers, minor modifications have been made to the theme in order to help make sure the bulk gifting feature works in the drawer cart seamlessly.

You can implement the button without theme settings (settings schema). Theme settings allows for more control for the merchant.

### Yakk Button

See the [Yakk Button Snippet](/snippets/yakk-btn.liquid) for the button that will be rendered in the drawer cart.

```HTML
<div class="cart__ctas">
  <a id="yakk-cart-btn" href="{{ settings.yakk_page.url }}" class="button button--primary">
    {{ settings.yakk_btn_text }}
  </a>
</div>
<style>
  #yakk-cart-btn {
    margin: 1rem auto;
    width: 100%;
    background-color: {{ settings.yakk_btn_bg_color }};
    color: {{ settings.yakk_btn_txt_color }};
  }
</style>
```

### Drawer Cart

See the [Drawer Cart Snippet](/snippets/cart-drawer.liquid) for the drawer cart that will be rendered in the theme.

```HTML
<!-- Yakk Button Start -->
{% if settings.yakk_enabled %}
  {% render 'yakk-btn' %}
{% endif %}
<!-- End Yakk Button -->
```

### Settings Schema

The [Settings Schema](/config/settings_schema.json) has been modified with the existing Cart Settings to ensure the bulk gifting feature works and can be selectively enabled when the drawer cart is in use.

```json
{
  "type": "header",
  "content": "Bulk Gifting"
},
{
  "type": "paragraph",
  "content": "Enable bulk gifting if using a drawer cart."
},
{
  "type": "checkbox",
  "id": "yakk_enabled",
  "label": "Enable Bulk Gifting",
  "default": false
},
{
  "type": "page",
  "id": "yakk_page",
  "label": "Bulk Gifting Page",
  "info": "Select the page that will be used for the bulk gifting."
},
{
  "type": "text",
  "id": "yakk_btn_text",
  "label": "Bulk Gifting Button Text",
  "info": "Enter the text for the bulk gifting button.",
  "default": "Send as Gift"
},
{
  "type": "color",
  "id": "yakk_btn_bg_color",
  "label": "Bulk Gifting Button Background Color",
  "default": "#000000"
},
{
  "type": "color",
  "id": "yakk_btn_txt_color",
  "label": "Bulk Gifting Button Text Color",
  "default": "#ffffff"
}
```
