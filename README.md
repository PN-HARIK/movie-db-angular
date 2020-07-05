# :zap: Angular Movie Database

* App using Angular 10, to create a movie database. The home screen displays a list of movie images. Each image redirects to a movie detail page with movie details listed using data-binding.

**\* Note: to open web links in a new window use: _ctrl+click on link_**

## :page_facing_up: Table of contents

* [:zap: Angular Movie Database](#zap-angular-movie-database)
  * [:page_facing_up: Table of contents](#pagefacingup-table-of-contents)
  * [:books: General info](#books-general-info)
  * [:camera: Screenshots](#camera-screenshots)
  * [:signal_strength: Technologies](#signalstrength-technologies)
  * [:floppy_disk: Setup](#floppydisk-setup)
  * [:computer: Code Examples](#computer-code-examples)
  * [:cool: Features](#cool-features)
  * [:clipboard: Status & To-Do List](#clipboard-status--to-do-list)
  * [:clap: Inspiration](#clap-inspiration)
  * [:envelope: Contact](#envelope-contact)

## :books: General info

* App routing module to load movie home screen. Differential loading used with 2nd routing module - see below:
* Movie-routing module for: list of movies (MovieListComponent), form to add movie (AddMovieComponent) and a movie detail page (MovieDetailComponent).
* Dummy backend used to store json movie data.

## :camera: Screenshots

![Example screenshot](./img/movie-list.png).
![Example screenshot](./img/json-data.png).
![Example screenshot](./img/detail-page.png).

## :signal_strength: Technologies

* [Angular v10](https://angular.io/)
* [RxJS Library v6](https://angular.io/guide/rx-library) used to [subscribe](http://reactivex.io/documentation/operators/subscribe.html) to the API data [observable](http://reactivex.io/documentation/observable.html).
* [json-server v0.16.1](https://www.npmjs.com/package/json-server) used with the `db.json` file to get a fake API.

## :floppy_disk: Setup

* Install dependencies using `npm i` then run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app does automatically reload if you change any of the source files.
* Open a second terminal and run `npm run api` for a local json server. Navigate to `http://localhost:3000/`. The json file will update if a movie is added from the front-end 'add movie' page.

## :computer: Code Examples

* `movie-list.component.html` extract showing html to load movies asynchronously with a loading image until they are shown.

```html
<!--if there are movies then show them in the DOM-->
<ul *ngIf="movies$ | async as movies; else loading" [@listAnimation]="movies">
  <li *ngFor="let movie of movies">
    <a [routerLink]="movie.id">
      <img [src]="movie.image" />
    </a>
  </li>
</ul>

<ng-template #loading>
  <ul [@listAnimation]="loadingMovies.length">
    <li
      *ngFor="let movie of loadingMovies"
      [@listAnimation]="loadingMovies.length"
    >
      <img src="/assets/movie.png" />
    </li>
  </ul>
</ng-template>
```

## :cool: Features

* [Angular Reactive Forms](https://angular.io/guide/reactive-forms) (model-driven forms) are used instead of the html template-driven method.
* BrowserAnimations used to add some animation to the movie details loading.
* Working backend on port 3000 was very easy to setup and run.

## :clipboard: Status & To-Do List

* Status: Working. Frontend updated to Angular 10 and all dependencies updated.
* To-Do: Add a nav back button on detail page.

## :clap: Inspiration

* [Paul Halliday Youtube video: FREE Angular 8 Course - Learn Angular 8, RxJS, HttpClient, Smart/Presentational Components](https://www.youtube.com/watch?v=OcwwahqeASw)

## :envelope: Contact

* Repo created by [ABateman](https://www.andrewbateman.org) - you are welcome to [send me a message](https://andrewbateman.org/contact)
