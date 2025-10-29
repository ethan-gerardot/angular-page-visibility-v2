# Angular Page Visibility

## Angular support

Supports Angular 20

## Getting started

First, install it.

```bash
npm install --save angular-page-visibility-v2@latest
```

Then, import it into your `@NgModule` :

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { AngularPageVisibilityModule } from 'angular-page-visibility-v2';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, AngularPageVisibilityModule],
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

Finally, decorate your component :

```ts
import { Component, OnInit, OnDestroy } from '@angular/core';
import {
  OnPageVisible, OnPageHidden,
  OnPageVisibilityChange,
  AngularPageVisibilityStateEnum,
  OnPagePrerender, OnPageUnloaded} from 'angular-page-visibility-v2';
import { Subscription } from 'rxjs';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.less']
})
export class AppComponent implements OnInit, OnDestroy {
  ...
  @OnPageVisible()
  logWhenPageVisible (): void {
    console.log( 'OnPageVisible => visible' );
  }

  @OnPageHidden()
  logWhenPageHidden (): void {
    console.log( 'OnPageHidden => hidden' );
  }

  @OnPagePrerender()
  logWhenPagePrerender (): void {
    console.log( 'OnPagePrerender => prerender' );
  }

  @OnPageUnloaded()
  logWhenPageUnloaded (): void {
    console.log( 'OnPageUnloaded => unloaded' );
  }

  @OnPageVisibilityChange()
  logWhenPageVisibilityChange ( visibilityState: AngularPageVisibilityStateEnum ): void {
    if ( AngularPageVisibilityStateEnum[visibilityState]
      === AngularPageVisibilityStateEnum[AngularPageVisibilityStateEnum.VISIBLE]) {
      console.log( 'OnPageVisibilityChange => visible' );
    } else if (AngularPageVisibilityStateEnum[visibilityState]
      === AngularPageVisibilityStateEnum[AngularPageVisibilityStateEnum.HIDDEN]) {
      console.log( 'OnPageVisibilityChange => hidden' );
    } else if (AngularPageVisibilityStateEnum[visibilityState]
      === AngularPageVisibilityStateEnum[AngularPageVisibilityStateEnum.PRERENDER]) {
      console.log( 'OnPageVisibilityChange => prerender' );
    } else if (AngularPageVisibilityStateEnum[visibilityState]
      === AngularPageVisibilityStateEnum[AngularPageVisibilityStateEnum.UNLOADED]) {
      console.log( 'OnPageVisibilityChange => unloaded' );
    }
  }
  ...
}
```

## Publishing

1. Update version number in package.json and projects/angular-page-visibility-v2-lib/package.json
2. `npm run build:lib`
3. `cd dist/angular-page-visibility-v2`
4. `npm publish`

## Features and API

- [@OnPageVisible](./wiki/on-page-visible.decorator.md)
- [@OnPageHidden](./wiki/on-page-hidden.decorator.md)
- [@OnPagePrerender](./wiki/on-page-prerender.decorator.md)
- [@OnPageUnloaded](./wiki/on-page-unloaded.decorator.md)
- [@OnPageVisibilityChange](./wiki/on-page-visibility-change.decorator.md)
- [AngularPageVisibilityService](./wiki/page-visibility.service.md)

## For any questions, suggestions, or feature requests

[Please file an issue](https://github.com/ethan-gerardot/angular-page-visibility-v2/issues)!

## License

License under the MIT License (MIT)

Copyright © 2017-2020 [Olivier LIN-SI-CHENG](https://www.olivierlinsicheng.com)
Copyright © 2022 Ethan Gerardot

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.

IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
