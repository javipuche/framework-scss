# Framework SCSS

Framework de Sass escalable y sostenible.

## Instalación

Puedes instalar el framework con los siguientes gestores de paquetes:

### Bower

```bash
bower install framework-scss --save
```

### Npm

```Npm
npm install framework-scss --save
```

En el caso de npm si no tienes algún tipo de herramienta para instalar dependencias recursivamente tendrás que instalar también ```mediaqueries-sass-mixin``` y ```normalize.css```:

```Npm
npm install framework-scss mediaqueries-sass-mixin normalize.css --save
```

## Configuración

Una vez instalado lo primero que tienes que hacer es localizar los archivos que empiezan por ```example``` y copiarlos en tu directorio principal de scss manteniendo la estructura.

```
example.main.scss
settings/_example.settings.config.scss
settings/_example.settings.global.scss
```

### ```example.main.scss```

Este es el archivo principal del framework. Se encarga de hacer los ```@import``` de los demás archivos y será el archivo que tendrás que compilar para hacer el output del css.

Es importante fijarte en las rutas de los ```@import``` ya que dependiendo del gestor de paquetes que hayas usado tendrás que editarlas. Por defecto están puestas las de bower. Además tendrás que renombrarlo a ```main.scss```.

### ```_example.settings.config.scss```

Este es el archivo de configuración el framework. Principalmente se encarga de manejar el estado, la localización el entorno del proyecto, puede ser usado para manipular cosas pero no necesariamente tiene que afectar al CSS directamente. Un ejemplo muy básico de esto sería si queremos o no activar bordes redondeados en todo el proyecto:

```scss
// _settings.config.scss
$config-radius-enabled: true;

// _components.btn.scss
.c-btn {
    @if $config-radius-enabled {
        border-radius: $global-border-radius;
    }
}
```

Recuerda que también tienes que renombrarlo a: ```_settings.config.scss```.

### ```_example.settings.global.scss```

Este es el archivo global de variables del proyecto. Aquí puedes meter colores, familias de fuentes, tamaños de texto, etc. Recuerda que también tienes que renombrarlo a: ```_settings.global.scss```.

## Estructura de archivos

Esta estructura está basada en [inuitcss](https://github.com/inuitcss/inuitcss) de [Harry Roberts](https://csswizardry.com/) (sólo a nivel de directorios y nomenclatura).

Por lo tanto aunque yo la explique aquí es recomendable que os paséis por su repositorio y le echéis un vistazo.

- ```/settings```: Variables globales, opciones de ancho, configuraciones de estado, etc.
- ```/tools```: Principalmente mixins y funciones.
- ```/generic```: Estilos con una especificidad baja (ej. resets, box-sizing).
- ```/elements```: Elementos HTML sin clases (ej. body {}, p {}, a {}, address {}).
- ```/objects```: Objetos, abstracciones y patrones de diseño (ej. .o-layout {}, .o-box {}).
- ```/components```: Componentes UI del proyecto (ej. .c-slider {}, .c-btn {}, .c-heading {}).
- ```/utilities```: Clases con una especificidad alta, son clases que sobreescriben estilos y clases de ayuda (ej. .u-hidden {}, .u-text-center {}).

## Nomenclatura

### Archivos

- Cada archivo que vaya a ser importado tiene que empezar un un guión bajo ```_```.
- Cuando se crea un archivo tiene que empezar por lo que es (normalmente el nombre del directorio) seguido de un punto (ej. ```_settings.```).
- Siempre en minúsculas y los espacios separados por un guión medio ```-```.
- Los nombres tienen que ser descriptivos de lo que contienen. Es recomendable usar el nombre de la clase css, a menos que haya más de una (ej. ```_components.buttons.scss```).

### Clases

El proyecto usa un sistema de prefijos en las clases para poder saber que es ese elemento con un simple vistazo, así sabemos donde ir a buscar el archivo después.

- ```o-```: Objects
- ```c-```: Components
- ```u-```: Utilities

Por otro lado tenemos otros prefijos realmente útiles:

 - ```t-```: Se usa para aplicar un theme de estilos a un componente/s.
 - ```s-```: Se utiliza para dar estilos a un conjunto de elementos HTML, por ejemplo el código generado por un CMS. Hay que usarlo con cuidado ya que se nos puede ir de las manos el anidamiento.
 - ```is-```, ```has-```: Se utilizan para aplicar estilos concretos cuando se cumple un estado o una condición (ej. .is-active {}, .has-icon {}).
 - ```js-``` Significa que este elemento es afectado por el javascript. Nunca se tienen que dar estilos a estas clases, son solo para identificar los elementos en el JS.
 - ```_``` Prefijo de la vergüenza, se utiliza al principio de una clase cuando tienes que hacer alguna chapuza.

**Nota:** Puedes leer más sobre ello en ["More transparent UI code with Namespaces"](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/).

#### BEM

Todo lo anterior explicado se va a usar conjuntamente con la nomenclatura BEM (Bloque, Elemento, Modificador).

```css
.c-persona {} /* Seria el bloque */
.c-persona__mano {} /* Seria el elemento */
.c-persona__mano--derecha {} /* Seria el modificador */
```

Con este simple ejemplo queda claro que el bloque es la clase en si. El elemento se escribe con doble guión bajo ```__``` y el modificador se escribe con doble guión medio ```--```.

**Nota:** Para saber que se puede y que no se puede hacer es recomendable que leas la [documentación de BEM](https://en.bem.info/methodology/).

#### OOCSS

OOCSS es una metodología basada en objetos CSS. Resumiéndodolo mucho se trata de separar la estructura de los estilos visuales para poder reaprovechar lo máximo posible el código.

**Nota:** Puedes leer más sobre ello en ["Una introducción a Object Oriented CSS (OOCSS)"](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)

## Referencias

- [Documentación de SASS](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)
- [inuitcss](https://github.com/inuitcss/inuitcss)
- [Harry Roberts](https://csswizardry.com/)
- [CSS Guide Lines](http://cssguidelin.es/)
- [More transparent UI code with Namespaces](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
- [Documentación de BEM](https://en.bem.info/methodology/).