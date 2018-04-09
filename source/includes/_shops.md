# Tiendas
Ayuda para la personalización del diseño y funciones de las tiendas. En esta documentación encontrarás toda la información necesaria para construir, editar y agregar código a las tiendas que usan la plataforma SpinCommerce.

Si no encuentras lo que necesitas escribe a soporte@spincommerce.com para ayudarte. 

<aside class="notice">
En todos los planes de SpinCommerce puedes editar completamente las plantillas y personalizar el diseño de la tienda, permite cambiar aspectos gráficos, estructuras y características generales.<br>

A través del <b>editor avanzado</b> puedes acceder al código HTML/CSS/JS y <b>liquid</b>.
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
	{{ 'style.css' | asset_url | stylesheet_tag }}
	{{ 'file.js' | asset_url | javascript_tag }}
	
```	
* **Plantillas:** Archivos que viene por defecto en tu tienda. Estos archivos controlan los aspectos de diseño y funcionamiento de tu tema, haz clic en el archivo que quieras modificar, se abrirá en el editor a la derecha de la pantalla. <br> Además puedes crear nuevos archivos `.liquid`, `.css` y `.js` y añadirlos a tu tienda, haciendo clic en **'Agregar nueva'**. 


* **Archivos:** Puedes añadir archivos de imagen (JPG y PNG), PDF o archivos de programación como CSS o JS. <br> Al hacer clic en el archivo que hayas añadido puedes ver la ruta (url), la cual puedes agregar (copiar/pegar) en cualquier archivo de tu tienda. 


### Estructura Plantillas

Estas son las plantillas que vienen por defecto en los temas, puedes modificarlas o agregar nuevas. 

Plantilla | Descripción | Ruta
-------------- | -------------- | --------------
layout.liquid | Plantilla principal de cualquier tema. Encuentras el código del *header*, el *footer*, navegación (menús) y otras variables globales.  | 
home.liquid | Plantilla con código de la página de inicio. | `/`
products.liquid | Plantilla que muestra todos los productos visibles de la tienda. | `/products`
product.liquid | Plantilla que se utiliza para mostrar el contenido de cada producto creado. | `/products/product-slug` 
category.liquid | Plantilla que muestra los productos visibles de cada categoría o subcategoría. | `/categories/category-slug/subcategory-slug`
brand.liquid | Plantilla que muestra los productos de cada marca. | `/brands/brand-slug`
cart.liquid | Plantilla del carro de compras con productos agregados al carro y botón hacia el *checkout*. | `/cart`
page.liquid | Plantilla que se utiliza para mostrar cada página de la tienda. | `/pages/page-slug`
form.liquid | Plantilla que se utiliza para mostrar cada formulario de la tienda. | `/form/form-slug`
search.liquid | Plantilla que muestra los resultados de busqueda. | `/products/search`
_item.liquid | Este es un archivo llamado *partial* es un código que puedes insertar en la tienda y en este caso tiene el código para mostrar un producto del listado, esta incluido en `home.liquid`, `category.liquid`, `search.liquid`, `brand.liquid` y `products.liquid`. | 
_js_cart.liquid | Archivo *partial* para el carro de compras dinámico ajax | 
style.css | Archivo con el código CSS que personaliza el diseño de la tienda. |
script.js | Archivo que define funcionamientos específicos (ej.: galería de productos), esta escrito en lenguaje jQuery (Javascript)  | 


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
> Si estas en la página de inicio  {{ content }} se reemplazará por el contenido de esa plantilla.

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

La importancia de esta plantilla es que tiene un atributo dinámico que muestra el contenido de cada template (plantilla) `{{ content }}`. Es decir, si estás visitando la página de una producto el código `{{ content }}` se reemplazará por el que tengas en la plantilla `product.liquid`.

### home.liquid
Esta es la página de inicio de la tienda, y los contenidos se insertan donde este el atributo `{{ content }}` de la plantilla principal `layout.liquid`.

En esta plantilla puedes insertar textos, imágenes, contenidos destacados (que pueden usarse como banner, carrusel de imágenes o lo que prefieras), productos destacados, en oferta, nuevos o los que definas en la programación. 


### products.liquid

``` liquid
{% for product in products %}
	<a href="{{product.url}}" title="{{ product.name }}">{{product.name}}</a>
{% else %}
	<p> No hay productos en la tienda</p>
{% endfor %}
``` 

> Se muestran todos los productos pero se deviden por página (se define una cantidad de productos por página), se agrega páginación.

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

En esta plantilla usada para mostrar **todos los productos visibles** de tu tienda con la información que determines.


En el primer ejemplo se mostrará el nombre del producto y el link correspondiente, en el segundo ejemplo con paginación se muestra la primera imagen, además del precio (precio de comparación si existe), con nombre del producto y link al producto.

<aside class="notice">
Por defecto el listado de los productos se mostrarán por orden alfabético de la A a la Z. 
</aside>

### category.liquid
Plantilla para mostrar los **productos que están asignados en una categoría o subcategoria**. Permite agregar código para generar contenido que sólo se mostrará en las páginas de categorías, por ejemplo una imagen destacada (usando el campo de descripción de la categoría o contenidos destacados). 

En esta plantilla defines la estructura como quieres mostrar estos productos, ya sea 1, 2 o 3 columnas, entre otras características. 

<aside class="notice">
Por defecto el listado de los productos se mostrarán por orden alfabético de la A a la Z. 
</aside>

> Se muestran todos los productos de la categoría pero se deviden por página dependiendo de la cantidad definida, se agrega paginador.

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

### brand.liquid
Plantilla para mostrar **todos los productos que están asignados en una marca**. Permite agregar código para generar contenido que sólo se mostrará en las páginas de esa marca, por ejemplo una imagen destacada (usando contenidos destacados). En esta plantilla defines la estructura como quieres mostrar estos productos, ya sea 1, 2 o 3 columnas, entre otras características. 

<aside class="notice">
Por defecto los productos se mostrarán por orden alfabético de la A a la Z. 
</aside>

> Se muestran todos los productos de la marca asignada pero se deviden por página dependiendo de la cantidad definida, se agrega paginador.

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

Para mostrar las imágenes puedes hacerlo usando un bucle, que muestra todas las imágenes que se hayan agregado al producto desde el administrador de tu tienda. 

### page.liquid

Plantilla para mostrar la información de cada página de tu tienda. En esta plantilla puedes definir la estructura y como se mostrará la información que ingresaste en el administrador de tu tienda. 

``` liquid
	<h1>{{ page.title }}</h1>
	<div>{{ page.content }}</div>
```

### form.liquid

Plantilla para mostrar la información de cada formulario de tu tienda. En esta plantilla puedes definir la estructura y como se mostrará la información que ingresaste en el administrador de tu tienda. 

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

Liquid es un motor de templates que fue creado con requerimientos específicos, que tiene que tener un markup simple y resultados fácil de entender.

Un ejemplo de un código *liquid* de una tienda, que muestra el listado de los nombres de todos los productos creados y visibles de la tienda, además agregar un paginador, este código se encuentra en la plantilla `products.liquid`:

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
``` html
<div class="entry">
  {{ product.description }}
</div>
```
<br>
Se reemplazará por:

<div class="center-column"></div>
``` html
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

Lo **objetos en Liquid**, contienen atributos, que son contenidos dinámicos que se muestran en una página. Por ejemplo, el objeto producto tiene el atributo denominado `name` que se puede utilizar para generar el nombre del producto.

**Los objetos de liquid también se conocen a menudo como variables. Son expresiones que representan un valor, que pueden ser:**

- una cadena de texto, como el nombre de un producto o una URL
- un número, como el precio de un producto
- un conjunto de elementos, como un listado de productos en oferta
- un objeto que a su vez contiene otras variables, como `brand` (que contiene `brand.name` y `brand.url`).

Para mostrar el atributo de un objeto, se debe envolver el nombre del objeto usando `{{` para abrir y `}}` para cerrar, como se muestra a continuación:

<div class="center-column"></div>
``` liquid
{{ product.name }}
```
<br>
En el ejemplo se mostraría el nombre del producto, por ejemplo: 'Silla madera'.


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


