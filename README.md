# Taller de Angular

![Resultado](/images/result.png)

Autor: Eduardo Oviedo Blanco

Para usar este taller efectivamente, clone el código en su ambiente local.
```
git clone https://github.com/edWAR6/angular-properties-workshop.git
```
Si desea subir el taller en su repositorio personal.
Cree un repositorio en su perfil, luego:
```
git remote set-url origin https://github.com/<su usuario>/angular-properties-workshop.git
```

> El nombre del repositorio puede cambiar. Siga las instrucciones y guarde sus cambios.

## Propósito

Este taller demuestra el uso de Angular properties.

## Instrucciones

1. Ejecute el proyecto desde el inicio para que vea los cambios según avanza.

```bash
ng serve
```

2. Agregue (en la línea 25) una elemento imágen.
```html
<div class="media">
    <img class="mr-3 rounded align-self-center img-fluid" style="width:70px" src="" alt="">
    <div class="media-body align-self-center">
```

3. Haciendo uso de una expresión, agregue un src a la imágen.
```html
<img class="mr-3 rounded align-self-center img-fluid" style="width:70px" 
    src="{{ './assets/images/' + artist.shortname + '_tn.jpg' }}" alt=""
>
```

4. Ahora agregue una expresión, para el alt de la imágen.
```html
<img class="mr-3 rounded align-self-center img-fluid" style="width:70px" 
    src="{{ './assets/images/' + artist.shortname + '_tn.jpg' }}"
    alt="{{ 'Photo of ' + artist.name }}"
>
```

> La expresión sin embargo puede ser interpretada antes de que la imagen esté cargada, lo cual genera muchos problemas.

5. Cambie las expresiones por propiedades.
```html
<img class="mr-3 rounded align-self-center img-fluid" style="width:70px" 
    [src]="'./assets/images/' + artist.shortname + '_tn.jpg'"
    [alt]="'Photo of ' + artist.name"
>
```

6. Para lograr mostrar cuales items de la lista fueron seleccionados, cambie la propiedad del color de fondo al anchor.
```html
<a href="#" class="list-group-item list-group-item-action flex-column align-items-start"
    *ngFor="let artist of artists"
    (click)="showArtist(artist)"
    [style.background]="artist.highlight ? '#eee' : '#fff'">
```

7. Note como tenemos un error debido al tipo, según la interfaz de artist. Arregle la interfaz para corregir este problema.

```typescript
interface IArtist {
  name: string,
  shortname: string,
  reknown: string,
  bio: string,
  highlight?: boolean,
}
```

8. Cambie la función del evento click para cambiar este valor.
```typescript
showArtist(artist: IArtist) {
    this.query = artist.name;
    artist.highlight = !artist.highlight;
}  
```

# AngularProperties

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 12.1.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
