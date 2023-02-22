# Calculadora
Ejemplo de una calculadora.

## Entorno:
- Windows 10
- QT Creator 9.0.1
- win_flex 2.6.1
- win_bison 3.8.2

## Paso 1 - crear un proyecto en QT
- Qt Widget Application.
- Colocar un nombre al proyecto.
- Build system: qmake.
- Colocar el nombre de la clase del formulario (*.ui).
- Translation file, elegir el idioma de preferencia.
- Elegir el kit: Qt 6.4.2 MinGW 64 bits (pueden elegirse más depende de la plataforma en la que se quiera ejecutar).
- Si se quiere se puede elegir un control de versiones.

## Construir la interfaz
Agregar los siguientes controles.
- QlineEdit: Para la entrada de texto.
- QpushBotton: Para ejecutar las acciones.
- QLabel: agregar 2 para mostrar los resultados.

## Agregar los archivos de flex y bison
Colocar estos archivos en la misma carpeta que todos los demás archivos.
- parser.y
- scanner.l

## Instalar flex y bison

- [Descargar winflexbison para windows](https://github.com/lexxmark/winflexbison/releases)
- Descomprimirlo y colocarlo dentro de archivos de programas los archivos descargados.
- Registrar la ruta en variables de entorno.
- Comprobar si estan registrados correctamente (deben mostrar la versión al ejecutarse en el cmd)
```
win_flex --version
win_bison --version
```

## codigo para compilar
Para compilar es necesario estar en la misma ruta en la que se guardaron los archivos "parser.y" y "scanner.l"
```
win_bison -o parser.cpp --defines=parser.h parser.y
win_flex -o scanner.cpp --header-file=scanner.h scanner.l
```
## Agregar los archivos generados en el proyecto en QT
Es necesario agregar los archivos para estos se agregara a los: 
- Headers
    - parser.h
    - scanner.h

- Source
    - parser.cpp
    - scanner.cpp