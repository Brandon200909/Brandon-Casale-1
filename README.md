# Brandon-Casale-1my-led-theme/
├── assets/
│   ├── styles.css
│   ├── featured-product.jpg
│   ├── led-strip.jpg
│   ├── led-lamp.jpg
├── config/
│   ├── settings_schema.json
├── layout/
│   ├── theme.liquid
├── sections/
│   ├── featured-product.liquid
│   ├── product-grid.liquid
├── templates/
│   ├── index.liquid
│   ├── product.liquid
│   ├── collection.liquid<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{ page_title }}</title>
  <link rel="stylesheet" href="{{ 'styles.css' | asset_url }}">
</head>
<body>
  <header>
    <div class="logo">LED Haven</div>
    <nav>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/collections/all">Shop All</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    {{ content_for_layout }}
  </main>

  <footer>
    <p>&copy; 2024 LED Haven. All rights reserved.</p>
    <div class="social-links">
      <a href="#">Facebook</a>
      <a href="#">Instagram</a>
      <a href="#">Twitter</a>
    </div>
  </footer>
</body>
</html><section id="hero">
  <h1>Transform Your Space with LED Magic</h1>
  <p>Discover innovative LED products to light up your life.</p>
  <a href="/collections/all" class="shop-now">Shop Now</a>
</section>

{% section 'featured-product' %}
{% section 'product-grid' %}<section id="featured">
  <h2>Featured Product</h2>
  <div class="product">
    <img src="{{ 'featured-product.jpg' | asset_url }}" alt="LED Turntable Clock">
    <div class="product-info">
      <h3>{{ all_products['led-turntable-clock'].title }}</h3>
      <p>A stylish LED clock with a vintage turntable design. Perfect for any modern space.</p>
      <p class="price">{{ all_products['led-turntable-clock'].price | money }}</p>
      <a href="{{ all_products['led-turntable-clock'].url }}" class="buy-now">Buy Now</a>
    </div>
  </div>
</section><section id="shop">
  <h2>Shop All Products</h2>
  <div class="product-grid">
    {% for product in collections['all'].products %}
      <div class="product-card">
        <img src="{{ product.featured_image | img_url: 'medium' }}" alt="{{ product.title }}">
        <h3>{{ product.title }}</h3>
        <p>{{ product.description | strip_html | truncate: 100 }}</p>
        <p class="price">{{ product.price | money }}</p>
        <a href="{{ product.url }}" class="buy-now">Buy Now</a>
      </div>
    {% endfor %}
  </div>
</section>body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  color: #333;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #222;
  color: #fff;
  padding: 10px 20px;
}

header .logo {
  font-size: 1.5em;
  font-weight: bold;
}

header nav ul {
  list-style: none;
  display: flex;
  gap: 15px;
}

header nav ul li a {
  color: #fff;
  text-decoration: none;
}

#hero {
  text-align: center;
  padding: 50px 20px;
  background: linear-gradient(45deg, #3b82f6, #9333ea);
  color: #fff;
}

#hero .shop-now {
  display: inline-block;
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #fff;
  color: #333;
  text-decoration: none;
  border-radius: 5px;
}

#featured .product {
  display: flex;
  gap: 20px;
  justify-content: center;
  align-items: center;
}

#featured img {
  width: 200px;
}

.product-grid {
  display: flex;
  gap: 20px;
  justify-content: center;
  flex-wrap: wrap;
}

.product-card {
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 10px;
  width: 200px;
}

.product-card img {
  width: 100%;
}

footer {
  background-color: #222;
  color: #fff;
  text-align: center;
  padding: 10px 20px;
  margin-top: 20px;
}[
  {
    "name": "Homepage Settings",
    "settings": [
      {
        "type": "text",
        "id": "hero_title",
        "label": "Hero Title",
        "default": "Transform Your Space with LED Magic"
      },
      {
        "type": "image_picker",
        "id": "featured_product_image",
        "label": "Featured Product Image"
      }
    ]
  }
]
