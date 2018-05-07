# MWP Twig Tambahan
menambahkan beberapa function pada twig template

## Penggunaan
Letakkan file `core.php` atau copas aja kedalam plugin MWP di `includes/modules/vendor/twig/twig/lib/twig/extension/core.php`

## Tambahan functions

- `shuffle()` function untuk me random array
- `base64en()` function seperti `base64_encode()`
- `str_text()` function seperti `sanitize_title()` kemudian di `str_replace('-', ' ', $value)`
- `source_url()` function untuk meredirect url source ke domain.com/source/`ksu93akiekl` url dalam base64_encode

## Contoh

```
<div class="card-columns popup-gallery">
{% set google_images = get_google_images(1,100,keyword,'any') %}
{% if google_images %}
{% for image in shuffle(google_images) %}
<div class="card"><div class="d-block"><a href="{{image.source_url}}" title="{{ str_text(image.title) }} {{ str_text(image.image_alt) }}" class="img-source"><img class="card-img-top" src="{{image.thumbnail}}" alt="{{ str_text(image.title) }} {{ str_text(image.image_alt) }}"></a></div><div class="card-body"><p class="card-text">{{ str_text(image.title) }} {{ str_text(image.image_alt) }}</p></div><div class="card-footer"><small class="text-muted"><a href="{{ source_url(base64en(image.source_page_url)) }}" target="_blank">Source</a></small></div></div>
{% endfor %}
{% endif %}
</div>

```
