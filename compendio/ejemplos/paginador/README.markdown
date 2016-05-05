Paginador JPages
-------

[1]: <https://github.com/neobenjax/compendio>

_Paginador en Javascript_

#### Demo

<http://neobenjax.github.io/compendio/ejemplos/paginador/>

### Implementación y Uso

Incluir la(s) librería(s) necesaria(s) antes de la etiqueta `</body>`:

```html
<script src="jPages_custom.min.js"></script>
```

Declaración de la función (La función se declarará una vez a fines de solo utilizar una línea de declaración durante todo un proyecto)

```javascript
function paginadorInit(startPage,perPage,containerID,paginadorClass){
			minHeight = false;
	        $(paginadorClass).jPages({
	            containerID  : containerID,
	            perPage      : perPage,
	            startPage    : startPage,
	            startRange   : 1,
	            midRange     : 5,
	            endRange     : 1,
	            first        : '',
	            previous     : 'anterior',
	            next         : 'siguiente',
	            last         : '',
	            minHeight    : minHeight,
	            callback     : function(pages,items){
	                           }
	        });    
		}
```

Implementación de UNA línea
<br><br>
<b>listadoPaginado</b> : el ID del contenedor del Paginador
<br>
<b>#paginador div.paginador</b> : Es el contenedor de la paginación

```javascript
paginadorInit(1,6,'listadoPaginado','#paginador div.paginador');
```
Opcionalmente se puede colocar un efecto de SCROLL TOP, para los casos en los que la lista es muy grande y el paginador 
esta posicionado en el fondo y es necesario ir a la parte superio de la página <b>listadoPaginado</b> sería el punto donde irá el scroll una vez se cambie de página;
pudiendo cambiar ese nombre por un ID diferente que actue de ancla <b>"#anclaDiferente"</b>

```javascript
$(document).on('click','#paginador .paginador a',function(){
	$('html, body').animate({
	  scrollTop:  $('#listadoPaginado').offset().top
	}, 100);
});
```
Para la parte de HTML el markup utilizado puede ser como:
```html
  <ul id="listadoPaginado">
  	<li class="item">Contenido de cada ITEM</li>
  	<li class="item">Contenido de cada ITEM</li>
  	<li class="item">Contenido de cada ITEM</li>
  </ul>
```
Donde cada <b>LI (hijo de UL#listadoPaginado)</b> será lo que se pagine siempre que tengan las mismas clases

Adicionalmente los estilso por DEFAULT serían:
```css
.paginador {
    margin: 0;
    padding: 0;
    width: 50%;
    display: inline-block;
    font-size:16px;
    color: #fff;
}
.paginador a.jp-current,
a.jp-current:hover {
    background: #848484;
    color:#fff;
    font-weight: bold;
}

.paginador a {
    font-size: 14px;
    cursor: pointer;
    margin: 0 5px;
    color: #000;
    padding: 3px 8px;
    display: inline-block;
    vertical-align: middle;
    text-decoration: none;
    font-weight: bold;
}

.paginador a:hover {
    background-color: #000;
    color: #FFF;
    opacity: 0.5;
}

.paginador a.jp-previous { margin-right: 15px;border: 1px solid #fff;padding: 6px 29px;}
.paginador a.jp-next { margin-left: 15px;border: 1px solid #fff;padding: 3px 8px;}

.paginador a.jp-current,
a.jp-current:hover {
    color: #fff;
    background: #000!important;
}

.paginador a.jp-disabled,
a.jp-disabled:hover {
    color: rgba(255, 255, 255, 0.74);
    display: none;
}

.paginador a.jp-current,
a.jp-current:hover,
.paginador a.jp-disabled,
a.jp-disabled:hover {
    cursor: default;
    background: none;
}

.paginador span { margin: 0 5px; }

a.jp-first,a.jp-last {
    display: none;
}
```
