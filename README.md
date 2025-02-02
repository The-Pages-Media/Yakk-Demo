# Yakk 🤗 The Pages Media

## Preview Theme

URL: `https://tpm-yakk.myshopify.com/`

Password: `yakkyakkyakk`

## Modifications

Because there is a lack of standardization across Shopify websites when it comes to cart drawers, minor modifications have been made to the theme in order to help make sure the bulk gifting feature works in the drawer cart seamlessly.

### Yakk Button

See the [Yakk Button Snippet](/snippets/yakk-btn.liquid) for the button that will be rendered in the drawer cart.

```HTML
<div class="cart__ctas">
  <a id="yakk-cart-btn" href="{{ settings.bulk_gifting_page.url }}" class="button button--primary">
    {{ settings.bulk_gifting_btn_text }}
  </a>
</div>
<style>
  #yakk-cart-btn {
    margin: 1rem auto;
    width: 100%;
    background-color: {{ settings.yakk_btn_bg }};
    color: {{ settings.yakk_btn_text }};
  }
</style>
```

### Drawer Cart

See the [Drawer Cart Snippet](/snippets/cart-drawer.liquid) for the drawer cart that will be rendered in the theme.

```HTML
<!-- Yakk Button Start -->
{% if settings.bulk_gifting_enabled %}
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
  "id": "bulk_gifting_enabled",
  "label": "Enable Bulk Gifting",
  "default": false
},
{
  "type": "page",
  "id": "bulk_gifting_page",
  "label": "Bulk Gifting Page",
  "info": "Select the page that will be used for the bulk gifting."
},
{
  "type": "text",
  "id": "bulk_gifting_btn_text",
  "label": "Bulk Gifting Button Text",
  "info": "Enter the text for the bulk gifting button.",
  "default": "Send as Gift"
},
{
  "type": "color",
  "id": "yakk_btn_bg",
  "label": "Bulk Gifting Button Background",
  "default": "#000000"
},
{
  "type": "color",
  "id": "yakk_btn_text",
  "label": "Bulk Gifting Button Text",
  "default": "#ffffff"
}
```
