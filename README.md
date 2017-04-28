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

## Referencias

- [inuitcss](https://github.com/inuitcss/inuitcss)
- [Harry Roberts](https://csswizardry.com/)