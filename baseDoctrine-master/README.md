MiW: base Doctrine
======================================

[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)
[![Minimum PHP Version](https://img.shields.io/badge/php-%5E8.0-blue.svg)](http://php.net/)
[![Scrutinizer analysis results](https://scrutinizer-ci.com/g/FJavierGil/baseDoctrine/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/FJavierGil/baseDoctrine/?branch=master)
> 馃幆 Proyecto b谩sico con ORM Doctrine y Dotenv

Este proyecto pretende servir como base para hacer m谩s sencilla la gesti贸n de datos en PHP.
En concreto, se ha utilizado el ORM [Doctrine][doctrine], que es un Object-Relational
Mapper que proporciona persistencia transparente para objetos PHP. Emplea el patr贸n [Data Mapper][dataMapper]
con el objetivo de obtener un desacoplamiento completo entre la l贸gica de negocio y la
persistencia de los datos en los sistemas de gesti贸n de bases de datos (SGBD).

Adicionalmente, este proyecto se apoya en el componente [Dotenv][dotenv] para facilitar
su configuraci贸n a trav茅s de variables de entorno. Esto permite que cualquier configuraci贸n
que pueda variar entre diferentes entornos pueda ser establecida en variables de entorno,
tal como se aconseja en la metodolog铆a [鈥淭he twelve-factor app鈥漖[12factor].

## 馃洜锔? Instalaci贸n de la aplicaci贸n

Para realizar la instalaci贸n de la aplicaci贸n crear谩n un usuario, contrase帽a y base de datos
en el SGBD. A continuaci贸n se debe crear una copia del fichero `./.env` y renombrarla
como `./.env.local` (si se ejecuta en entornos basados en contenedores Docker, el fichero
se deber谩 llamar `./.env.docker`). A continuaci贸n se editar谩 este fichero para asignar
los par谩metros:

* (opcional) Configuraci贸n del servidor de bases de datos
* Nombre de la base de datos
* Configuraci贸n del acceso a la base de datos (usuario y contrase帽a)

Una vez editado el anterior fichero, desde el directorio ra铆z del proyecto se ejecutar谩n los comandos:
```
$> composer update
$> bin/doctrine orm:schema-tool:update --dump-sql --force
```

Para comprobar la validez de la informaci贸n de mapeo y la sincronizaci贸n con la base de datos:
```
$> bin/doctrine orm:validate-schema
```

## 馃梽锔? Estructura del proyecto:

A continuaci贸n se describe el contenido y estructura del proyecto:

* Directorio `bin`:
    - Ejecutables (*doctrine*)
* Directorio `config`:
    - `cli-config.php`: configuraci贸n de la consola de comandos de Doctrine CLI
* Directorio `src`:
    - Subdirectorio `src/Entity`: entidades PHP (incluyen anotaciones de mapeo del ORM)
    - Subdirectorio `src/scripts`: scripts de ejemplo
    - Subdirectorio `src/Utility`: clases DoctrineConnector y Utils (proporcionan el gestor de entidades)
* Directorio `vendor`:
    - Componentes desarrollados por terceros (Doctrine, Dotenv, etc.)

[dataMapper]: http://martinfowler.com/eaaCatalog/dataMapper.html
[doctrine]: http://docs.doctrine-project.org/projects/doctrine-orm/en/latest/
[dotenv]: https://packagist.org/packages/vlucas/phpdotenv
[12factor]: https://www.12factor.net/es/