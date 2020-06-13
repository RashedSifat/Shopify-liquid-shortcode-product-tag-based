# Shopify-liquid-shortcode-product-tag-based
Developed the product shortcode to use in shopify pages, blogs, collection pages to show the products filtered by its Product Tags.

<h4>Example:</h4>
<pre><code> [product name="T-shart"] </pre></code>

The above shortcode can be used in collection pages, pages, blogs from Shopify admin in HTML format. The shortcode retreive all the product which contain the tag "T-shirt".

I followed this artile to show the products but it didnt serve me properly so, i edited the code, yuo can also check this out before using my code:
https://patdryburgh.com/blog/shopify-shortcodes/


Shopify PRODUCT SHORTCODE to SHOW SPECIFIC TAGED PRODUCTS.

<h4>File Directory:</h4>

Upload the bellow Four files to the Snippet directory from the Theme. <br/>
shortcode.liquid<br/>
shortcode-render.liquid<br/>
shortcode-product.liquid<br/>
shortcodeTemplate.liquid<br/>


No need to edit the shortcode.liquid and shortcode-render.liquid files. 
In "shortcode-product.liquid" files the code start with:


<pre><code>{% capture productHandle %}<br/>	
    {% include 'shortcode-render' render:'name' %}<br/>
{% endcapture %}<br/>
</pre></code>


From the shortcode [product name="T-shart"], it capture the name for example "T-shirt". The "productHandle" is assigned to "spec" 

<pre><code>{% assign spec = productHandle %}</pre></code>

<code><pre> {% paginate collections.all.products by 10000 %}</code></pre> Pagination is used to go through the 10000 products as default it can be grab only 50 products.


Then the bellow code is used to retreive the products from all collection which contains the Required Tag.

<pre><code>{% for product in collections.all.products %}
  	{% assign noRepeat = 0 %}
  	{% for tag in product.tags %}
		  {% if spec contains tag and noRepeat == 0 %}
      		{%include 'ShortcodeTemplate'%}
  			  {% assign noRepeat = 1 %}
  		{% endif %}
	  {% endfor %}
{% endfor %}</code></pre>

Here "noRepeat" variable is used to ignore the repeated tags like if a product contains the tags: T-shirt, T-shirt-small, T-shirt-large then, without "noRepeat", it'll show the same product three times.

The template to visible the product with a style is "ShortcodeTemplate". you can use any other existing theme template or custom one.


<h4>The Final Input:</h4>
<pre> <code> <h2> T-Shirt Products</h2> 
[product name="T-shart"] </code> </pre>


If you still face any issue to use the codes, feel free to contact me at: <a href="mailto:me.sifat@live.com">me.sifat@live.com</a>
Or, Directly hire me: <a href="https://www.upwork.com/o/profiles/users/~01c3507b22db0d551a/">Hire on Upwork</a>

Happy Coding!
