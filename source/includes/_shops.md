# Tiendas
Esta documentación te servirá de ayuda para la personalización del diseño y funciones de las tiendas. Encontrarás toda la información necesaria para construir, editar y agregar código a las tiendas que usan la plataforma SpinCommerce. 

Las secciones se divide en: 

* **Plantillas**: aspecto generales y cómo funciona un tema (theme). 

* **Estructura Plantillas**: cuáles son las plantilla de nuestros theme y como están construidas.

* **Programación liquid**: cómo programar una tienda usando etiquetas liquid.

* **Construyendo un Tema**: cómo personalizar un tema (theme) y código que te ayudará a potenciar una tienda. 

Si no encuentras lo que necesitas escribe a soporte@spincommerce.com para ayudarte. 

<aside class="notice">
En todos los planes de SpinCommerce puedes editar completamente las plantillas y personalizar el diseño de la tienda, permite cambiar aspectos gráficos, estructuras y características generales.<br>

A través del <b>editor avanzado</b> puedes acceder al código HTML/CSS/JS y <b>liquid</b>.
</aside>

<aside class="warning">
Para ver los ejemplo del código Liquid, en la columna derecha, debes hacer clic en el a pestaña Liquid. 
</aside>

## Plantillas

Las plantillas son una serie de archivos que construyen tu tienda, estos a su vez forman un tema (o theme), a continuación explicaremos como funcionan y como puedes modificarlos:

### Cambiar Tema (theme) 

Cuando abres tu tienda en SpinCommerce el *theme* que viene por defecto es el **Theme Básico**, puedes verlo funcionando en esta [demo](http://themebasico.spincommerce.com/). Para cambiarlo debes entrar a **Apariencia**, hacer clic en **Temas**, y una vez que hayas seleccionado el tema para tu tienda, hacer clic en **Usar este diseño** para instalarlo. 

<aside class="warning">

Al cambiar de tema se eliminarán permanentemente todas las plantillas actuales con los cambios que realizaste, se reemplazarán por las del tema seleccionado. Además se agregarán contenidos adicionales que son específicos del tema que estás instalando que te ayudarán en su administración.

</aside>

### Editar Plantillas

Para editar un *theme* o crear uno nuevo, tenemos un editor de código muy fácil de usar, debes entrar a a **Apariencia**, hacer clic en **Editor de Plantilla**. En la pantalla selecciona el archivo que quieras modificar, también puedes crear uno nuevo. 

Te recomendamos que si vas a editar el código entender el sistema de plantillas que se explicarán a continuación así como también la programación usando código *liquid*. 

### Funcionamiento Plantillas

Tu tema (o theme), tiene una **colección de archivos** que controlan la estructura y funcionamiento. Al abrir una tienda por defecto tendrás instalado el [Theme Básico](http://themebasico.spincommerce.com/).

<aside class="notice">
En las plantillas los archivos principales tienen la extensión .liquid. Estos tienen código de programación escrito en ese lenguaje. Además las plantillas pueden utilizar otros códigos de programación como HTML, CSS y JavaScript.
</aside>

**En el Editor de Plantillas encontrarás:**

> Código `liquid` para insertar archivos creados CSS o JS, agregar en `layout.liquid` para funcionamiento global.

``` liquid
	{{ 'file.css' | asset_url | stylesheet_tag }}
	{{ 'file.js' | asset_url | javascript_tag }}
	
```	
* **Plantillas:** Archivos que viene por defecto en tu tienda. Estos archivos controlan los aspectos de diseño y funcionamiento de tu tema, haz clic en el archivo que quieras modificar, se abrirá en el editor a la derecha de la pantalla. <br> Además puedes crear nuevos archivos `.liquid`, `.css` y `.js` y añadirlos a tu tienda, haciendo clic en **'Agregar nueva'**. 


* **Archivos:** Puedes añadir archivos de imagen (JPG y PNG), PDF o archivos de programación como CSS o JS. <br> Al hacer clic en el archivo que hayas añadido puedes ver la ruta (url), la cual puedes agregar (copiar/pegar) en cualquier archivo de tu tienda. 

### Agregar archivos

En el editor puedes crear nuevos archivos `.liquid`, `.css` y `.js` y añadirlos a tu tienda, haciendo clic en **'Agregar nueva'**. 

También puede subir archivo haciendo clic en *Elegir archivos*, puedes subir archivos CSS, JS, JPG, PNG, PDF y GIF.

Te recomendamos que si vas a agregar una librería o cualquier tipo de archivo que no vas a modificar puede subir desde tu computador. Pero si vas a agregar código de programación que podría ser que edites en el futuro puedes crear una plantilla y agregarlo donde corresponda. 

Si agregar un archivo desde tu computadora para agregarlo al tema tienes que copiar la URL, y pegarla donde corresponda, por ejemplo en el caso de agregar una imagen, copiar la URL y agregas:

<div class="center-column"></div>
``` liquid
<img src="https://spincommercecdn.imgix.net/560/products/22da6720-6634-4c22-a982-f0510fc7976e/linkedin.jpg?timestamp=1523906780" alt="descripcion">
```
<br>


## Estructura Plantillas

Estas son las plantillas que vienen por defecto en los temas, puedes modificarlas o agregar nuevas. 

Plantilla | Descripción | Ruta
-------------- | -------------- | --------------
[layout.liquid](/#layout-liquid) | Plantilla principal de cualquier tema. Encuentras el código del *header*, el *footer*, navegación (menús) y otras variables globales.  | 
[home.liquid](/#home-liquid) | Plantilla con código de la página de inicio. | `/`
[products.liquid](/#products-liquid)| Plantilla que muestra todos los productos visibles de la tienda. | `/products`
[category.liquid](/#category-liquid) | Plantilla que muestra los productos visibles de cada categoría o subcategoría. | `/categories/category-slug/subcategory-slug`
[brand.liquid](/#brand-liquid) | Plantilla que muestra los productos de cada marca. | `/brands/brand-slug`
[search.liquid](/#search-liquid) | Plantilla que muestra los resultados de búsqueda. | `/products/search`
[product.liquid](/#product-liquid) | Plantilla que se utiliza para mostrar el contenido de cada producto creado. | `/products/product-slug` 
[page.liquid](/#page-liquid) | Plantilla que se utiliza para mostrar cada página de la tienda. | `/pages/page-slug`
[form.liquid](/#form-liquid) | Plantilla que se utiliza para mostrar cada formulario de la tienda. | `/form/form-slug`
[cart.liquid](/#cart-liquid) | Plantilla del carro de compras con productos agregados al carro y botón hacia el *checkout*. | `/cart`
[_item.liquid](/#item-liquid) | Este es un archivo llamado *partial* es un código que puedes insertar en la tienda y en este caso tiene el código para mostrar un producto del listado, esta incluido en `home.liquid`, `category.liquid`, `search.liquid`, `brand.liquid` y `products.liquid`. | 
[_js_cart.liquid](/#_js_cart-liquid) | Archivo *partial* para el carro de compras dinámico ajax | 
[style.css](/#style-css) | Archivo con el código CSS que personaliza el diseño de la tienda. |
[script.js](/#script-js) | Archivo que define funcionamientos específicos (ej.: galería de productos), esta escrito en lenguaje jQuery (Javascript)  | 


### layout.liquid

``` liquid
<html>
  <head>
    <title>{{ shop.name }}</title>
    <meta name="description" content="{% current_description %}">
  </head>
  <header></header>
  <body>
    {{ content }}
  </body>
  <footer></footer>
</html>
```	
> Si estas en la página de inicio, el código {{ content }} se reemplazará por el contenido de esa plantilla.

``` liquid
<html>
  <head>
    <title>Tienda de Decoración</title>
    <meta name="description" content="Vendemos muebles de madera y objetos de decoración">
  </head>
  <header></header>
  <body>
    <h1>¡Bienvenido a la nueva Tienda de Decoración!</h1>
  </body>
  <footer></footer>
</html>
```	

Es la plantilla principal de la tienda. 
La estructura básica de una plantilla de layout debe tener todo lo que se mostrará en la tienda, como *header*, menús principales, links a redes sociales, logotipo de la tienda, archivos que necesites insertar (CSS, JS), códigos de seguimiento, *footer*, además es donde defines la estructura general y básica de tu tienda. 

La importancia de esta plantilla es que tiene un atributo dinámico que muestra el contenido de cada template (plantilla), el código es: `{{ content }}`. 
 

Es decir, si estás visitando la página de una producto el código: `{{ content }}` se reemplazará por el que tengas en la plantilla `product.liquid`.

### home.liquid
Esta es la página de inicio de la tienda, y los contenidos se insertan donde este el atributo `{{ content }}` de la plantilla principal `layout.liquid`.

En esta plantilla puedes insertar textos, imágenes, contenidos destacados (que pueden usarse como banner, carrusel de imágenes o lo que prefieras), productos destacados, en oferta, nuevos o los que definas en la programación. 


### products.liquid

> Código para mostrar todos los productos de la tienda, muestra sólo nombre y link de cada producto.

``` liquid
{% for product in products %}
	<a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
{% else %}
	<p> No hay productos en la tienda</p>
{% endfor %}
``` 

> Código para mostrar todos los productos pero se dividen por página (se define una cantidad de productos por página), se agrega páginación. Muestra nombre, primera imagen, link, precio y precio comparación de cada producto. 

``` liquid
  {% paginate products by 16 %}
    {% for product in paginate.collection %}   
    	<div class="product">
    	
			<a href="{{product.url}}" title="{{ product.name }}" class="product-image">
	        	<img src="{{product.first_image.url | resize: 'w=500'}}" alt="{{ product.name }}" />
	        </a>
	        
	    	<a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
    	
			<div class="prices">
				{% if product.comparison_price > 0 %}
					<strike class="product-price-comparison">{{product.formatted_comparison_price}}</strike>
				{% endif %}
				<span class="product-price">{{product.formatted_price}}</span>
			</div>	
    	
    	 </div>
    {% endfor %}
    
    <div class="pagination">
    	{{ paginate | default_pagination }}
    </div>
  {% endpaginate %}
``` 

En esta plantilla muestra **todos los productos visibles** de tu tienda con la información que determines.

Se utilizan [etiquetas de iteración](/#etiquetas-de-iteracion) para ejecutar un código que mostrará el listado de productos de la tienda. 


En el primer ejemplo se mostrará el nombre del producto y el link correspondiente, en el segundo ejemplo con paginación se muestra la primera imagen, además del precio (precio de comparación si existe), con nombre del producto y link al producto.

<aside class="notice">
Por defecto el listado de los productos se mostrarán por orden alfabético de la A a la Z. 
</aside>

### category.liquid

> Código para mostrar el título y el campo de texto de la categoría. 

``` liquid
<h1>{{ category.name }}</h>
<div>
 {{ category.content }}
</div>

```

> Resultado sería:

``` liquid
<h1>Muebles</h>
<div>
 En esta sección entrarás todos los muebles de nuestra tienda. 
</div>

```

> Este código permite mostrar todos los productos de la categoría pero se dividen por página dependiendo de la cantidad definida, se agrega paginación. Muestra sólo el nombre y link del producto.

``` liquid

{% paginate category.products by 16 %}
    {% for product in paginate.collection %}
      <a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>   
    {% endfor %}
    
    <div class="pagination">
     {{ paginate | default_pagination }}
    </div>
{% endpaginate %}
  
``` 


Plantilla para mostrar los **productos que están asignados en una categoría o subcategoria**. 

Permite agregar código para generar contenido que sólo se mostrará en las páginas de categorías, por ejemplo una imagen destacada (usando el campo de descripción de la categoría o contenidos destacados). 

En esta plantilla defines la estructura como quieres mostrar estos productos, ya sea 1, 2 o 3 columnas, entre otras características. 

<aside class="notice">
Por defecto los productos se mostrarán por orden alfabético de la A a la Z. 
</aside>



### brand.liquid

> Este código muestra todos los productos de la marca asignada pero se dividen por página dependiendo de la cantidad definida, se agrega paginación. Muestra sólo el nombre y link del producto.

``` liquid

{% paginate brand.products by 16 %}
    {% for product in paginate.collection %}
    	<a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>  
    {% endfor %}
    
    <div class="pagination">
    {{ paginate | default_pagination }}
    </div>
{% endpaginate %}
  
``` 

Plantilla para mostrar **todos los productos que están asignados en una marca**. 

Permite agregar código para generar contenido que sólo se mostrará en las páginas de esa marca, por ejemplo una imagen destacada (usando contenidos destacados), o mostrar sólo el nombre de la marca: `brand.name`. 

En esta plantilla defines la estructura como quieres mostrar estos productos, ya sea 1, 2 o 3 columnas, entre otras características. 

<aside class="notice">
Por defecto los productos se mostrarán por orden alfabético de la A a la Z. 
</aside>



### product.liquid
Esta plantilla muestra la información de un sólo producto de la tienda. Esta información es la que se agrega en el administrador de tu tienda, en esta plantilla defines como la quieres mostrar. 

El objeto general es `product`, con este puedes programar la plantilla para mostrar cada uno de sus atributos.


**Nombre Producto**
 
<div class="center-column"></div>
``` liquid
{{ product.name }}
```
<br>
**Descripción**

<div class="center-column"></div>
``` liquid
{{ product.description }}
```
<br>
**Precio**

<div class="center-column"></div>
``` liquid
{{ product.formatted_price }}
```
<br>

**Precio de Comparación**<br> 
Con una condicional si es que tiene un valor el precio:

<div class="center-column"></div>
``` liquid
{% if product.comparison_price > 0 %}
	{{ product.formatted_comparison_price }}
{% endif %}
```
<br>
**Marca** <br> 
Con una condicional si es que tiene marca asignada:

<div class="center-column"></div>
``` liquid
{% if product.brand.name.size > 0 %}
	<a class="{{ product.brand.slug }}" href="{{ product.brand.url }}">{{ product.brand.name }}</a>
{% endif %}
```
<br>
**SKU**<br> 
Con una condicional, si el producto tiene variantes, mostrará los SKU de cada una de las variantes que tenga el producto. 

<div class="center-column"></div>
``` liquid
{% if product.variants %}
	<div class="product_sku">
	{% for variant in product.variants %}
         {% if variant.sku.size > 0 %}
      		<span class="sku_wrapper">SKU: <span class="sku">{{ variant.sku }}</span></span>
         {% endif %}
	{% endfor %}
	</div>
{% endif %}
```

###**product.liquid (botón carro de compras)**<br>

``` liquid
<form class="add-to-cart" action="/cart/add" method="post">
{% if product.has_any_available_variant %}
  	{% if product.variants.size > 1 %}
    <div class="selector-variants">
  		<label for="productSelect-option-0">Seleccionar</label>
  		<select class="single-option-selector" name="variant" id="productSelect-option-0">
        {% for variant in product.variants %}
          <option value="{{variant.id}}" {% unless variant.is_available %}disabled{% endunless %}>{{variant.name}} 	{% unless variant.is_available %}(agotado){% endunless %}</option>
        {% endfor %}
  		</select>
  	</div>
  	{% else %}
    <input type="hidden" name="variant" value="{{product.first_variant.id}}">
	{% endif %}

	<div class="input-cart clear">
	  <input type="number" name="quantity" size="2" value="1" id="cart-quantity" min="1">
	  <button type="submit" name="add" id="cart-button" class="submit">
	  	<span id="AddToCartText">Agregar al Carro</span>
	  </button>
	</div>
	{% else %}
	  <div class="no-stock">Producto sin stock</div>
	{% endif %}
</form>
```

Además en esta plantilla deberás añadir **el botón para agregar el producto al carro de compras**, con las variantes para seleccionar el producto (cuando hay más de una variante). Y mostrar el mensaje "Producto sin stock" cuando no hay disponibilidad del producto. 

<aside class="notice">Debes tener en cuenta que cualquier modificación que realices al botón para agregar el producto al carro de compras puede modificar su comportamiento. Recomendamos mantener este código completo. </aside>


###**product.liquid (imágenes del producto)**<br>

> Código para mostrar todas las imágenes que se hayan agregado en el producto, con una condicional si tiene imágenes agregadas. 

``` liquid
{% if product.has_images %}
    <ul>
        {% for image in product.images %}
          	<li>
            	<img src="{{image.url | resize: 'w=800'}}" alt="{{ product.name }}" />
		    </li>
       {% endfor %}
    </ul>
{% endif %}
```

> También puede mostrar sólo la primera imagen de tu producto usando el siguiente código: 

``` liquid
<img src="{{ product.first_image.url | resize: 'w=800' }}" alt="{{ product.name }}" />
```

Para mostrar las imágenes puedes hacerlo usando [etiquetas de iteración](/#etiquetas-de-iteracion), permitirá visualizar todas las imágenes que se hayan agregado al producto desde el administrador de tu tienda. 

### page.liquid

``` liquid
	<h1>{{ page.title }}</h1>
	<div>{{ page.content }}</div>
```

Plantilla para mostrar la información de cada página de tu tienda. En esta plantilla puedes definir la estructura y como se mostrará la información que ingresaste en el administrador de tu tienda. 


### form.liquid

> Información general de la plantilla:

``` liquid
	<h1>{{ form.name }}</h1>
	<div>{{ form.content }}</div>
```

> Para mostrar el formulario:

``` liquid
<form action="/forms/{{ form.slug }}/submit" accept-charset="UTF-8" method="POST">

	{% for input in form.inputs %}
		<label for="{{ input.name.downcase }}" >{{ input.name }} {% if input.required %} * {% endif %}
		{{ input.html classes: "form-control" }}
	{% endfor %}
	
	<small class="note">* Completa los campos requeridos</small>
	<input type="submit" value="Enviar" class="button submit center">	
	{{invisible_captcha}}
</form>
```

> Si el mensaje fue enviado puedes agregar una condicional:

``` liquid
{% if form.sent %}
	  <p>Mensaje enviado correctamente</p>
{% endif %}
```

Plantilla para mostrar la información de cada formulario de tu tienda. En esta plantilla puedes definir la estructura y como se mostrará la información que ingresaste en el administrador de tu tienda. 

### search.liquid 

``` liquid
<h1>{{ products_search | size }} producto(s) encontrado(s)</h1>

<ul>
{% paginate products by 16 %}
    {% for product in products_search %}
        <li class="product">
    	
			<a href="{{product.url}}" title="{{ product.name }}" class="product-image">
	        	<img src="{{product.first_image.url | resize: 'w=500'}}" alt="{{ product.name }}" />
	        </a>
	        
	    	<a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
    	
			<div class="prices">
				{% if product.comparison_price > 0 %}
					<strike class="product-price-comparison">{{product.formatted_comparison_price}}</strike>
				{% endif %}
				<span class="product-price">{{product.formatted_price}}</span>
			</div>	
    	
		</li>
{% endfor %}
    
<div class="pagination">
    {{ paginate | default_pagination }}
</div>
{% endpaginate %}
</ul>
```

Plantilla para mostrar los resultados de la búsqueda de productos. También puedes usar el código con páginación para separar los resultados por página. 

### cart.liquid

``` liquid
{% if cart.items.size > 0 %}
<form action="/cart/apply" method="post">
<table border="0" cellspacing="5" cellpadding="5" class="cart_table">
      <thead>
        <tr>
          <th colspan="2">Producto</th>
          <th>Variante</th>
          <th>Precio</th>
          <th>Cantidad</th>
          <th>Subtotal</th>
          <th>&nbsp;</th>
        </tr>
      </thead>
      <tbody>
      
      {% for item in cart.items %}

        <tr>
          <td><img alt="nombre producto" src="{{item.product.first_image.url | resize: 'w=75&h=75' }}"></td>
          <td><a href="{{item.product.url}}">{{item.product_name}}</a></td>
          <td>{{item.variant_name}}</td>
          <td>{{item.formatted_unit_price}}</td>
          <td><input name="items[]quantity" size="2" type="number" value="{{item.quantity}}"></td>
          <td>{{item.formatted_total_price}}</td>
          <td>
            <input name="items[]id" type="hidden" value="{{item.id}}">
            <a class="remove" href="/cart/remove?item={{item.id}}" title="Eliminar producto del carro">Remover</a>
          </td>

        </tr>
        {% endfor %}
      </tbody>
      <tfoot>
	      <tr>
	        <td>&nbsp;</td>
	        <td>&nbsp;</td>
	        <td>&nbsp;</td>
	        <td>&nbsp;</td>
	        <td>Subtotal*:</td>
	        <td colspan="2"><strong>{{cart.formatted_subtotal_price}}</strong></td>
	      </tr>
      {% if cart.discount_total > 0 %}
        <tr>
          <td>&nbsp;</td>
          <td>&nbsp;</td>
          <td>&nbsp;</td>
          <td>&nbsp;</td>
          <td>Descuento:</td>
          <td colspan="2"><strong>- {{ cart.formatted_discount_total }}</strong></td>
        </tr>
      {% endif %}
	      <tr>
	        <td>&nbsp;</td>
	        <td>&nbsp;</td>
	        <td>&nbsp;</td>
	        <td>&nbsp;</td>
	        <td>Total:</td>
	        <td colspan="2"><strong>{{cart.formatted_total}}</strong></td>
	      </tr>
	  </tfoot>
    </table>

    <a href="/" title="seguir comprando">« Seguir comprando</a>
    <input name="update" type="submit" value="Recalcular">
    <input name="checkout" type="submit" value="Pagar mi orden »">

</form>
{% else %}
    <p>Tu carro de compras está vacío. Revisa nuestros <a href="/products">productos</a> y agrégalos al carro.</p>
{% endif %}
 ```

Plantilla del carro de compras de la tienda. Contiene lo que es la información de cada producto que se ha agregado al carro de compras, el subtotal, descuento (si existe) y monto total. 

Además botón para *seguir comprando* (por defecto con link a la página de inicio de la tienda), botón para *recalcular* la compra (en el caso que se hayan aumentado o disminuido la cantidad de unidades de un producto) y por último el botón para *Pagar mi orden*, con link a la página del *checkout*.

<aside class="notice">Debes tener en cuenta que cualquier modificación que realices en el carro de compras puede modificar su funcionamiento. Recomendamos mantener este código completo. </aside>

### _item.liquid

Los archivos que tiene un guión bajo antes de cada nombre se llaman *partials*, en este tipo de archivos puedes agregar código de programación que será reutilizado en varias partes del mismo tema. Se usa el siguiente atributo para insertarlo en una plantilla:

<div class="center-column"></div>
``` liquid
{% include 'item' %}
```
<br>
En el editor SpinCommerce puedes crear nuevos archivos `liquid` que siempre se crearan como *partials*. 

Por defecto todos los temas traen el archivo `_item.liquid` creado, que tiene el código del objeto `product`, y sirve para mostrarlo en cada listado de producto, por ejemplo, se utiliza con las etiquetas de iteración de listado de productos de la tienda. 

``` liquid
<ul id="products-items">
    {% paginate products by 15 %}
    	{% for product in paginate.collection %}
			{% include 'item' %}    
		{% endfor %}
		 <div class="pagination">
		{{ paginate | default_pagination }}
		 </div>
	{% endpaginate %}
</ul>
```

> el archivo _item.liquid básico tiene el siguiente código para mostrar información de un producto:

``` liquid
<div class="item">
    <a href="{{product.url}}" title="{{ product.name }}" class="product-image">
        <img src="{{product.first_image.url | risize: 'w=278&h=278&fit=crop'}}" alt="{{ product.name }}" />
    </a>

    <h4 class="product-model">
      <a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
    </h4>

    <div class="prices">
      {% if product.comparison_price > 0 %}
        <strike class="product-price-comparison">{{product.formatted_comparison_price}}</strike>
      {% endif %}
    <span class="product-price">{{product.formatted_price}}</span>
</div>
```

### _js_cart.liquid

El archivo `_js_cart.liquid` también es un archivo *partial* que encuéntras en el [Theme Loa](http://themeloa.spincommerce.com/), tiene el código de funcionamiento de **Carro Ajax**. 

### style.css

Archivo por defecto con código en programación CSS. Tiene los estilos generales de la tienda, cómo colores, tipografías, estructuras, botones, menús, entre otros. 

Para modificar colores buscar el comentario `/* main colors for quick changes` donde están las etiquetas que modifican la mayoría de colores del theme. 

### script.js

Archivo por defecto con código en programación jQuery (javascript). 

Todos los temas (*themes*) tienen programación que incluye el funcionamiento de carrousel de imágenes de la página de inicio y galería de producto (incluido el plugin de Flexslider), también código y condicionales para saber el tamaño del navegador y validación de algunas opciones de los formularios. 

Algunos temas traen programación relacionada con el funcionamiento del menú en dispositivos móviles, funcionamiento del menu lateral de categorías y/o marcas. Y además si el tema tiene Foundation (theme Básico, Corp y Retail) permite activar la librería Javascript del framework. 


## Programación Liquid

Las plantillas que tiene formato `.liquid` usan el **lenguaje de programación** *liquid*, este código se compone por etiquetas con lógicas de programación que le dicen a las plantillas como deben funcionar en la tienda. Las puedes reconocer porque usan los siguientes caracteres: 

Ejemplo nombre de la tienda, donde se usa los etiquetas de texto (devuelven datos) usando doble llave para abrir `{{` y para cerrar `}}`:

<div class="center-column"></div>
``` liquid
	{{ shop.name }}
```	
<br>
Ejemplo de condicional, donde se usa las etiquetas lógicas, y se usan  llave y porcentaje de apertura `{%` y cierre `%}`:

<div class="center-column"></div>
``` liquid
	{% if template == 'page' %} ... {% endif %}
```

### Introducción a Liquid

Liquid es un código de programación para templates, que tiene que tener un markup y lenguaje simple, fácil de entender e implementar. 

Un ejemplo de un código *liquid* de una tienda, que muestra el listado de los nombres de todos los productos creados y visibles de la tienda, además agrega paginación, este código se encuentra en la plantilla `products.liquid`:

<div class="center-column"></div>
``` liquid
{% paginate products by 6 %}
  {% for product in paginate.collection %}
    {{ product.name }}
  {% endfor %}
    {{ paginate | default_pagination }}
{% endpaginate %}
```	

<aside class="notice">
En las plantillas .liquid se puedes agregar y combinar código HTML con el código liquid.
</aside>


En este otro ejemplo sólo mostraremos la descripción del producto, que se reemplazará por el contenido que corresponda, este código esta en la plantilla `product.liquid`.


<div class="center-column"></div>
``` liquid
<div class="entry">
  {{ product.description }}
</div>
```
<br>
Se reemplazará por:

<div class="center-column"></div>
``` liquid
<div class="entry">
  Esta es la descripción del producto.
</div>
```

### Aspectos Básicos

Liquid es una combinación de etiquetas, objetos y filtros para cargar **contenido dinámico**.
El código liquid se reemplazará en tu tienda por el contenido que corresponda.

* **Objects / Objectos**<br>
Los objetos contienen atributos que se usan para mostrar contenido dinámico en una página. 
Ejemplo Objetos:

<div class="center-column"></div>
``` liquid
{{ product.name }} 
// output: Zapatos negros
```

* **Tags / Etiquetas**<br>
Las etiquetas conforman la lógica de programación que le dice qué hacer a las plantillas.
Ejemplo Etiquetas:

<div class="center-column"></div>
``` liquid
{% if template == 'products' %}.....{% endif %}
```

* **Filters / Filtros**<br> 
Los filtros se utilizan para modificar la salida de cadenas, números, variables y objetos. 
Ejemplo Filtros:

<div class="center-column"></div>
``` liquid
{{ 'style.css' | asset_url | stylesheet_tag }} 
// output: <link href="/stylesheets/style.css" rel="stylesheet" type="text/css">
```

### Objetos: Slug (o handles)

Los slug o (handles en inglés), se utilizan para acceder a los atributos de los objetos de liquid. Por defecto, un slug es el título del objeto en minúsculas, donde cualquier espacio y/o caracteres especiales son reemplazados por guiones (-). La mayoría de los objetos de las tiendas tienen slug como: productos, categorías, menús, destacados.

Por ejemplo el código liquid para mostrar el contenido de una página con el nombre **'Sobre Nosotros'**, donde su slug es `sobre-nosotros`, el código sería el siguiente:

<div class="center-column"></div>
``` liquid
{{ pages.sobre-nosotros.content }}
```


<aside class="notice">
<b>Cómo se crea un slug:</b><br>
Cada vez que creas un objeto en tu tienda, como por ejemplo un producto con el nombre 'Silla', automáticamente se crear el slug 'silla', si ya existía un producto con ese slug se agregará un guión y un número que se va incrementando, por ejemplo: 'silla-1', 'silla-2', así sucesivamente.<br><br>

Los espacios son reemplazados por guiones, por ejemplo 'Silla de madera', su slug sería 'silla-de-madera'.
</aside>


El **slug también determina la URL del objeto**, por ejemplo una página con el nombre 'Sobre Nosotros' y el slug 'sobre-nosotros', la URL será:<br>
`https://mitienda.spincommerce.com/pages/sobre-nosotros`

Debes tener en cuenta que si cambias el nombre al objeto, automáticamente se actualizará el slug. Pero también puedes cambiar solamente el nombre del slug editándolo.

<b>Los objetos (liquid) que tienen slug en SpinCommerce son:</b>

- Productos
- Páginas
- Formularios
- Categorías y subcategorías
- Menús de navegación
- Contenidos destacados
- Marcas

### Objetos: Variables

Lo **objetos en Liquid**, contienen atributos, que son contenidos dinámicos que se muestran en una página. Por ejemplo, el objeto producto tiene el atributo denominado `name` que se puede utilizar para generar el nombre del producto, que se debe usar como `product.name`.

**Los objetos de liquid también se conocen a menudo como variables y existen diferentes tipos:**

- cadena de texto (ej.: nombre de la tienda)
- número (ej.: precio de un producto)
- un conjunto de elementos (ej.: productos de una categoría)
- un objeto que a su vez contiene otras variables, (ej.: `brand` que contiene `brand.name` y `brand.url`).

Para mostrar el atributo de un objeto, se debe envolver el nombre del objeto usando `{{` para abrir y `}}` para cerrar, como se muestra a continuación:

<div class="center-column"></div>
``` liquid
{{ product.name }}
```
<br>
En el ejemplo se mostraría el nombre del producto, por ejemplo: <b>'Silla madera'</b>.


### Objetos: Variables globales
Los siguientes objetos se pueden utilizar y acceder desde cualquier archivo del tema (theme) y se definen como objetos globales o variables globales:

**Generales**

- `template`
- `shop`

**Productos**

- `products`
- `categories`
- `paginate`
- `brand`

**Links**

- `menus`
- `menu_category`
- `menu_brand`
- `current_url`

**Carro**

- `items_count`
- `order`

**Contenidos**

- `featured`
- `pages`

### Objetos: Variables locales
Otras variables dependen del contexto y sólo están disponibles en algunas plantillas.

Un ejemplo de esto es `cart`, que no está disponible en un formulario de contacto pero sí en la plantilla del carro: `cart.liquid`.

### Etiquetas condicionales

Estas etiquetas crean condiciones que deciden si se ejecutan bloques de código Liquid.



**Etiqueta `if`**</br>
Ejecuta un bloque de código sólo si se cumple una determinada condición (es decir, si el resultado es verdadero).

<div class="center-column"></div>
``` liquid
{% if product.name == 'Sillas Madera' %}
 Este es el producto Sillas Madera
{% endif %}
``` 

</br>
**Etiqueta `unless`**</br>
Similar a `if`, pero ejecuta un bloque de código sólo si **no** se cumple una determinada condición (es decir, si el resultado es falso).

<div class="center-column"></div>
``` liquid
{% unless product.name == 'Silla Madera' %}
 Este no es el producto Silla Madera
{% endunless %}
```
</br>
También se puede utilizar:
</br>

<div class="center-column"></div>
``` liquid
{% if product.name != 'Sillas Madera' %}
 Este es el producto Sillas Madera
{% endif %}
```
</br>
**Etiquetas `else / elsif`**<br>
Agrega más condiciones a un bloque `if` o `unless`.

<div class="center-column"></div>
``` liquid
{% if template == 'category' %}
 {{ category.name }}
{% elsif template == 'products' %}
 Productos
{% endif %}
```

</br>
**Condiciones multiples `and` / `or`**</br>
Puede utilizar los operadores `and` y `or` para incluir más de una condición en una etiqueta de flujo de control y pueden ser usados juntos para crear condiciones condicionales complejas.

Si utilizas múltiples operadores `and` y `or` al mismo tiempo, tenga en cuenta que los operadores `and` serán evaluados primero, luego los operadores `or`.

<div class="center-column"></div>
``` liquid
{% if template == 'products' or template == 'category' %}
 <h1>Estos son los productos de la tienda</h1>
{% endif %}
```
</br>

**Etiquetas `case` / `when`**</br>
Crea una instrucción para cambiar y ejecutar un bloque de código particular cuando una variable tiene un valor específico. `Case` inicializa la instrucción y cambia cuando las sentencias definen las diversas condiciones.

Opcionalmente puede agregar una instrucción `else` al final del caso para proporcionar código para ejecutar si ninguna de las condiciones se cumplen.

<div class="center-column"></div>
``` liquid
{% case category.name %}
  {% when 'Muebles' %}
  Estos son los productos de la categoría muebles
  {% when 'Destacados' %}
  Conoce nuestros productos destacados
  {% when 'Nuevos' %}
  Tenemos nuevos productos en la tienda
  {% else %}
  Conoce nuestros productos
{% endcase %}
```

### Operadores lógicos y comparación

> Ejemplo de condicional para mostrar el título de la plantilla:

``` liquid

  {% if template == 'category' %}
  <b>{{ category.name }}</b>
  {% elsif template == 'brand' %}
  <b>{{ brand.name }}</b>
  {% elsif template == 'search' %}
  <b>{{ products_search | size }} producto(s) encontrado(s)</b>
  {% elsif template == 'products' %}
  <b>Productos</b>
  {% endif %}  

``` 

Liquid tiene acceso a muchos operadores lógicos y de comparación. Puedes utilizar operadores para crear condicionales.

Operador | Función 
-------------- | --------------
`==` | igual
`!=` | no es igual
`>` | mayor que
`<` | menor que
`>=` | mayor o igual
`<=` | menor o igual
`or` | condición A o condición B
`and` | condición A y condición B

### Etiquetas de iteración



Las etiquetas de iteración ejecutan repetidamente bloques de código.

**Código `for`**<br>
Ejecuta repetidamente un bloque de código. Para obtener una lista completa de atributos disponibles en un bucle.

Este bucle muestra el nombre con link de todos los productos disponibles en la tienda.

<div class="center-column"></div>
``` liquid
{% for product in products %}
 <a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
{% endfor %}
```
</br>
**Código `else`**<br>
En este caso se habla de retorno de un bucle que se ejecutará si el resultado es cero (por ejemplo, una tienda que no tiene productos).

<div class="center-column"></div>
``` liquid
{% for product in products %}
 <a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
{% else %}
 <p> No hay productos en la tienda</p>
{% endfor %}
```

### Filtros

Los filtros son métodos simples que modifican la salida de números, textos, variables y objetos. Se colocan dentro de una etiqueta de salida con doble llaves `{{` para abrir y para cerrar `}}`, además tienen una barra vertical que lo divide `|`.

Entonces un filtro para mostrar sólo 30 caracteres de la descripción de un producto se escribe así:

<div class="center-column"></div>
``` liquid
{{ product.description | truncate: 30 }}
```
<br>
En la tienda verás esto:

<div class="center-column"></div>
``` liquid
Macetero cerámica negra ...
```
<br>
Además se puede usar 1 o más filtros, en el siguiente ejemplo a la descripción del producto, se le aplica un filtro adicional para que todo el parámetro este en mayúsculas:

<div class="center-column"></div>
``` liquid
{{ product.description | truncate: 30 | upcase }}
```
<br>
Que se mostraría así en la tienda:

<div class="center-column"></div>
``` liquid
MACETERO CERÁMICA NEGRA ...
```

<br>
Estos son algunos filtros que puede usar en tu tienda.

**Filtros de cadenas de texto (string)**

Filtro | Función 
-------------- | --------------
`capitalize` | Convierte a mayúscula la primera letra del parámetro de entrada
`downcase` | Convierte todo el parámetro de entrada a minúsculas
`upcase` | Convierte todo el parámetro de entrada a mayúsculas
`truncate` | Corta un string a los X caracteres deseados
`truncatewords` | Corta un string a las X palabras deseadas
`strip_html` |  Saca todo el HTML de la cadena de texto
`strip_newlines` | Saca todos los ‘enters’ (\n) de la cadena de texto
`newline_to_br` | Reemplaza todos los ‘enters’ (\n) con un HTML `<br>`
`replace` | Reemplaza el valor de cierto string (`replace:‘Negro’,‘Blanco’`)
`split`| Divide un string utilizando un patrón parámetro (`split:-`)

**Filtros de array**

Filtro | Función 
-------------- | --------------
`first` | Devuelve el primer elemento de un parámetro de tipo array
`last` | Devuelve el último elemento de un parámetro de tipo array
`join` | Concatenar los elementos de un array con cierto carácter entre ellos (`join: ', '`)
`sort` |  Ordenar los elementos del array (`sort: 'name'`, `sort: 'price'` )
`map` | Devuelve un array con la propiedad de los miembros de otro array
`size` | Devuelve el tamaño de un array o string (cadena de caracteres)

**Filtros matemáticos**

Filtro | Función 
-------------- | --------------
`minus` | Resta un número de otro (`minus:2`)
`plus` |  Suma un número a otro (`plus:‘1’`)
`times` | Multiplica un número por otro (`times:4`)
`divided_by` | Divide un número por otro (`divided_by:2`)

**Filtros generales**

Filtro | Función 
-------------- | --------------
`asset_url` | Ruta de los archivos de la tienda
`resize` | Para pasar parámetros y modificar imagen (`resize: 'w=500'`)

## Construyendo un Tema

Ejemplos de código para insertar en las plantillas, que permiten modificar o agregar diferentes características. 


### Insertar archivos JS o CSS

``` liquid
{{ 'file.css' | asset_url | stylesheet_tag }}
{{ 'file.js' | asset_url | javascript_tag }}
```

Si en el editor de la tienda creaste un **nuevo archivo CSS o JS** y quieres agregarlo a la tienda, debes pegar el código correspondiente en la plantilla.  

Para que este disponible en toda la tienda debes agregarlo en la plantilla `layout.liquid`. El nombre del archivo será el que escribiste al crearlo, en el ejemplo `file.css` o `file.js`.

### Insertar *partial* con `include`

> Código para insertar un `partial` en cualquier plantilla de la tienda.

``` liquid

{% include 'nombre' %}

```

Un *partial* es un archivo en formato `liquid` que se crea en el editor de tiendas del administrador de Spincommerce y se verá así: `_nombre.liquid`. 

En este archivo puedes agregar código de programación HTML y/o liquid e  insertarlo en cualquier plantilla de la tienda. Sirve para evitar duplicar código, ya que puedes insertar fragmentos de programación donde lo necesites y varias veces si es necesario.

<aside class="notice"> Cuando se crea el archivo se le agrega un guión bajo `_nombre.liquid` pero al insertarlo con la etiqueta `include` sólo agrega el nombre del archivo creado.</aside> 

### Condicionales por template

> Código de ejemplo de condicional de templates para mostrar el título de cada página. 

``` liquid
{% if template == 'category' %}
  <b>{{ category.name }}</b>
{% elsif template == 'brand' %}
  <b>{{ brand.name }}</b>
{% elsif template == 'search' %}
  <b>{{ products_search | size }} producto(s) encontrado(s)</b>
{% elsif template == 'products' %}
  <b>Productos</b>
{% endif %} 
 ``` 
 
> En la plantilla de producto también puedes usar:

``` liquid
{% if product %}
	Lo que quieras mostrar sólo en la plantilla del producto.
{% endif %}
 ``` 

Puedes crear condicionales para insertar diferentes código de programación en diferentes plantillas de la tienda pero programandolo desde el `layout.liquid`. 

Los templates de SpinCommerce son:

* home
* search
* brand
* category
* products
* product
* page
* form
* cart


### Código de Google Analytics

``` liquid
{{ shop.google_analytics }}
```

Código que se inserta antes del cierre del `</header>`, que interpreta lo que se agrega en *Preferencias > Información General* en el campo de texto de Google Adwords en el administrador de la tienda. 


### Código de Google Tag Manager 

``` liquid
{{ shop.google_tag_manager }}
```

Código que se inserta al principio del `<body>`, que interpreta lo que se agrega en *Preferencias > Información General* en el campo de texto de Google Tag Manager en el administrador de la tienda. 


### Código redes sociales

``` liquid
<ul> 
  {% if shop.facebook_url %} 
  <li class="facebook-link"> 
    <a target="_blank" title="Facebook!" href="{{shop.facebook_url}}">Conócenos!</a> 
  </li> 
  {% endif %} 
  
  {% if shop.twitter_url %} 
  <li class="twitter-link"> 
    <a target="_blank" title="Twitter!" href="{{shop.twitter_url}}">Síguenos!</a> 
  </li> 
  {% endif %}
   
  {% if shop.instagram_url %}   
  <li class="instagram-link"> 
    <a target="_blank" title="Instagram!" href="{{shop.instagram_url}}">Visítanos</a> 
  </li> 
  {% endif %} 
  
  {% if shop.pinterest_url %}   
  <li class="pinterest-link"> 
    <a target="_blank" title="Pinterest!" href="{{shop.pinterest_url}}">Visítanos</a> 
  </li> 
  {% endif %} 
  
  {% if shop.youtube_url %} 
  <li class="youtube-link"> 
    <a target="_blank" title="Youtube!" href="{{shop.youtube_url}}">Visítanos</a> 
  </li> 
  {% endif %} 
  
  {% if shop.googleplus_url %} 
  <li class="google-link"> 
    <a target="_blank" title="Google+!" href="{{shop.googleplus_url}}">Conócenos!</a> 
   </li> 
  {% endif %} 
  
</ul>
```

Los links a las redes sociales se agregar en *Preferencias > Redes Sociales* en el administrador de la tienda. 

Este código se debe agregar donde se quieran mostrar los links a las redes sociales de la tienda. Por defecto esta en el *footer* de cada *theme* disponible.

### Navegación Categorías

``` liquid
<ul class="vertical menu">
  {% for menu_category in categories %}
  <li class="{% if category and category.name == menu_category.name %}current {% endif %}">
    <a href="{{ menu_category.url }}">{{ menu_category.name }}</a>

    {% if menu_category.has_subcategories %}
     <ul class="submenu menu vertical nested">
      {% for subcategory in menu_category.subcategories %}
        <li class="{% if subcategory.name == category.name %} current {% endif %}">
          <a href="{{subcategory.url}}">→ {{subcategory.name}}</a>
        </li>
      {% endfor %}
  	 </ul>
    {% endif %}
   </li>
  {% endfor %}
</ul>
```
Es un menú de navegación que se crea de forma automática al agregar este código en una plantilla de la tienda, de preferencia en `layout.liquid` en las plantillas de productos, categorías, marcas o donde determines. 

Utiliza etiquetas de iteración para listar todas las **categorías** creadas en el administrador de la tienda con sus respectivos links, si esa categoría tiene una **sub categoría** creada, mostrará la lista de esas sub categorías con sus respectivos links. 

### Navegación Marcas

``` liquid
<ul class="menu">
  	{% for menu_brand in brands %}
  	<li class="{% if brand and brand.name == menu_brand.name %} current {% endif %}">
    	<a href="{{ menu_brand.url }}">{{ menu_brand.name }}</a>
	</li>
	{% endfor %}
</ul>
```  
             
Es un menú de navegación que se crea de forma automática al agregar este código en una plantilla de la tienda, de preferencia en `layout.liquid` en las plantillas de productos, categorías, marcas o donde determines. 

Utiliza etiquetas de iteración para listar todas las **marcas** creadas en el administrador de la tienda con sus respectivos links.


### Menú Navegación Personalizado

> Código de menú de navegación personalizado donde el slug es `main`.

``` liquid
<ul>
  {% for link in menus.main.links %}
    <li class="{% if current_url == link.url %} current {% endif %}">
      <a href="{{ link.url }}" {% if link.target %} target="blank"{% endif %}>{{ link.name }}</a>
    </li>
  {% endfor %}
</ul>
```	         

Un menú de navegación personalizado, es un menú donde cada item se debe agregar desde el administrador de la tienda en *Contenidos > Navegación*, cada *menú* tiene un [slug](/#objetos-slug-o-handles), que es el que permite determinar que menú es el que se mostrará al insertar el código. 

Los objetos que se pueden usar son:

* link.url / dirección URL del item
* link.target / si el link se abre en la misma ventana u otra ventana
* link.name / nombre del link 
* link.slug / nombre del link en formato de texto tipo slug


### Menú Navegación Personalizado Categorías

> Código de menú de navegación personalizado donde el slug es `categories`.

``` liquid
<ul class="menu">
  {% for link in menus.categories.links %}
    <li class="{% if category.name == link.name %} current {% endif %}">
      <a href="{{ link.url  }}" {% if link.target %} target="blank" {% endif %}>{{ link.name }}</a>
      {% if link.is_category? %}
          {% if link.category.has_subcategories %}
            <ul class="submenu">
            {% for subcategory in link.category.subcategories %}
              <li class="{% if subcategory.name == category.name %} current {% endif %}">
                <a href="{{ subcategory.url }}">{{ subcategory.name }}</a>
                </li>
            {% endfor %}
            </ul>
          {% endif %}
      {% endif %}
    </li>
  {% endfor %}
</ul>
```

Código para crear un **menú personalizado para las categorías de productos**, en este caso las etiquetas de iteración muestras los link de cada categoría que se agregué en *Contenidos > Navegación* en el menú con el slug `categories`, si la categoría tiene sub categorías mostrará el listado de las sub categorías con su respectivo link. 

### Menú Navegación por página de Categoría

> Código de menú de navegación personalizado donde el slug es `main`.

``` liquid
<!-- si la plantilla es categoría -->
{% if template == 'category' %}

  	{% if category.has_subcategories and !link.url == category.url %}
         {% assign category_list = category.subcategories %} 
         {% assign category_title = category.parent_category.name %}
    {% elsif category.has_parent %}
          {% assign category_list = category.parent_category.subcategories %}
          {% assign category_title = category.parent_category.name %}
	{% else %}
		  {% assign category_list = category.subcategories %}
		  {% assign category_title =  category.name %}
	{% endif %}
	
	<h4>{{ category_title }}</h4>
    <ul>
		{% for list_category in category_list %}
		<li class="{% if list_category.name == category.name %} current {% endif %}">
		    <a href="{{ list_category.url }}">{{ list_category.name }}</a>
		</li>
		{% endfor %}
    </ul>
    
{% endif %}
```

Este menú de navegación automático para mostrar las categorías. Este código permite mostrar solamente los links a las sub categorías de la categoría que estoy visitando, es decir, si estoy visitando la página de la categoría `Muebles` de mi tienda y tiene creados las sub categorías `Sillas` y `Mesas`, esos serán los nombre y links que se verán en el menú.

### Contenidos Destacados

> En el código de ejemplo el `slug` es `banners`:

``` liquid
<ul>
	{% for featured in featured_contents.banners.links limit:3 %}
	<li>
      	<a title="Saber más" href="{{ featured.url }}" {% if featured.target %} target="blank" {% endif %}>
	  		<img src="{{ featured.img_url | resize: 'w=380&h=280&fit=crop' }}" alt="{{ featured.title }}" />
	  		{% if featured.title.size > 0 %}
	  		<span class="title">{{ featured.title }}</span>
	  		{% endif %}
	  		{% if featured.description.size > 0 %}
	  		<span class="description">{{ featured.description }}</span>
	  		{% endif %}
    	</a>
	</li>
	{% endfor %}
</ul>
```

Los contenidos destacados se agregan en *Contenidos > Destacados* en el administrador de la tienda, y permiten agregar una imagen, con un link, título (opcional) y descripción (opcional). 

Se pueden insertar en cualquier plantilla de la tienda, y el elemento de referencia es el [slug](/#objetos-slug-o-handles) que se crea automático al crear un contenido destacado en el administrador de la tienda. 

<aside class="notice">
Si se modifica el `slug` de una contenido destacado en el administrador de la tienda, se debe modificar en el código programado para mostrarlo. 
</aside>

Un contenido destacado te permite hacer galerías, mostrar banners, carruseles de imágenes, etc. 

### Control de imágenes

A cualquier imagen de la tienda se le pueden asignar tamaños personalizados, usando el filtro `resize`. Además de otras propiedades que te permiten controlar las imágenes. Por ejemplo:

<div class="center-column"></div>
``` liquid
{{ image.url | resize: 'w=500&h=500&fit=crop' }} 
```
<br>
El ejemplo anterior modifica la imagen a 500x500 pixeles, centrada y se corta las partes de la imagen que no corresponden al tamaño personalizado. Siempre se debe usar con la dirección URL de la imagen.

En el ejemplo `w` se refiere a width (ancho), `h` a height (alto) y `fit` al ajuste de la imagen y la propiedad `crop` recorta el exceso de imagen que no se ajusta al tamaño definido. El resultado será el ancho y alto establecido sin deformar la imagen.

Para saber más sobre el control de tamaño de la imagen puedes revisar esta documentación: [Size](https://docs.imgix.com/apis/url/size).

Si quieres usar la imagen de tamaño original (tamaño en el cual se subió a la plataforma) agrega:

<div class="center-column"></div>
``` liquid
 {{ image.url }}
 ```
 
 <br>
 Lista de filtro que puedes aplicar en `resize`:
 
 * `w=500&h=500` : Tamaño personalizado pero mantiene proporciones
 * `w=500&h=500&fit=crop` : Tamaño personalizado, lo fuerza y no mantiene proporciones originales
 * `w=500` : Ancho personalizado, mantiene proporciones
 * `h=500` : Alto personalizado, mantiene proporciones

Se puede hacer pruebas en la aplicación [sandbox](https://sandbox.imgix.com/create) y pegar el código correspondiente, siempre usando `resize` para contenido dinámico.
 
 <br>
 <br>
 