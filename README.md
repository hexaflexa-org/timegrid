# HexaFlexa Timegrid

**⚠️ This project is used to track any [Issues](https://github.com/hexaflexa-org/timegrid/issues) with the HexaFlexa Timegrid component. ⚠️**

[HexaFlexa Timegrid](https://www.npmjs.com/package/@hexaflexa/timegrid) is a [Web Component](https://developer.mozilla.org/en-US/docs/Web/API/Web_components) that can be used in any web application.  
Can be used in vanilla JavaScript, Angular, React and Vue.  
It is highly configurable and designed for mobile first.  
Supports multiple resources, can show only active days and business hours.  
The events can be dragged and resized.  
Has swiping and zooming capabilities.

## Documentation

- Demos and documentation can be found on the [HexaFlexa Timegrid](https://hexaflexa.com) page.

- API documentation for the `hf-timegrid` custom element can be found in the [hf-timegrid documentation page](https://hexaflexa.com/docs/api/v1/docs/components/hf-timegrid).

## Custom connectors

Connectors for Angular, React and Vue are provided.

- Angular connector: [@hexaflexa/timegrid-angular](https://www.npmjs.com/package/@hexaflexa/timegrid-angular)
- React connector: [@hexaflexa/timegrid-react](https://www.npmjs.com/package/@hexaflexa/timegrid-react)
- Vue connector: [@hexaflexa/timegrid-vue](https://www.npmjs.com/package/@hexaflexa/timegrid-vue)

# Install

## Install and register Swiper (optional):

Swiper is a dependency used to handle swiping.
The component works fine without Swiper, using the toolbar buttons, but will have no swiping ability.
Install Swiper in different ways:

### Script tag

- Put a script tag similar to this in the head of your *index.html*

```html
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-element-bundle.min.js"></script>
```

### Node Modules

- Install the package

```shell
npm install --save swiper
```

- Put a script tag similar to this in the head of your *index.html*

```html 
<script type='module' src='node_modules/swiper/timegrid/swiper-element-bundle.min.js'></script>
```

### In an app

- Install the package

```shell
npm install --save swiper
```

- Register Swiper in your app (in *main.ts*)

```typescript
import { register } from 'swiper/element/bundle';
register();
```

## Install this component:

Install the HexaFlexa Timegrid component in different ways:

### Script tag
- Put a script tag similar to this in the head of your *index.html*

```html
<script type='module' src='https://unpkg.com/@hexaflexa/timegrid@1/dist/timegrid/timegrid.esm.js'></script>
```

- Then you can use the element anywhere in your template, JSX, html etc

### Node Modules
- Install the package

```shell
npm install --save @hexaflexa/timegrid
```

- Put a script tag similar to this in the head of your *index.html*

```html 
<script type='module' src='node_modules/@hexaflexa/timegrid/dist/timegrid/timegrid.esm.js'></script>
```

- Use the `hf-timegrid` custom element anywhere in your template, JSX, html etc

### In an app
- Install the package

```shell
npm install --save @hexaflexa/timegrid
```

- Add an import to the npm packages

``` javascript
import { defineCustomElements } from '@hexaflexa/timegrid/loader';
defineCustomElements(window);
```

- Use the `hf-timegrid` custom element anywhere in your template, JSX, html etc

## Example - usage in an Angular app

This example assumes that the Angular app uses this web component directly, not the Angular connector.

- Install Swiper and Timegrid component

```shell
npm install --save swiper
npm install --save @hexaflexa/timegrid
```

- Add CUSTOM_ELEMENTS_SCHEMA to the modules that use the components (in *app.module.ts*)

```typescript
import { ..., CUSTOM_ELEMENTS_SCHEMA } from '@angular/core';
@NgModule({
    ...,
    schemas: [CUSTOM_ELEMENTS_SCHEMA],
})
```

- Register swiper and define the custom elements in your app (in *main.ts*)

```typescript
import { register } from 'swiper/element/bundle';
register();

import { defineCustomElements } from '@hexaflexa/timegrid/loader';
defineCustomElements(window);
```

- Declare the timegrid configuration and the start date, according to your needs (in your component, i.e. *app.component.ts*)

```typescript
import { TimegridConfig } from '@hexaflexa/timegrid';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrl: './app.component.css'
})
export class AppComponent {
    startDate: string;
    timegridConfig: TimegridConfig;
    
    constructor() {
        this.startDate = '2024-02-15';
        this.timegridConfig = {
            daysConfig: {
                daysCount: 3,
            },
            resources: [
                { id: '1', title: 'Resource 1' },
                { id: '2', title: 'Resource 2' },
            ],
            events: [
                {
                    id: '1',
                    resources: ['1'],
                    title: 'Event 1',
                    start: '2024-02-15 09:00',
                    end: '2024-02-15 10:00',
                },
                {
                    id: '2',
                    resources: ['2'],
                    title: 'Event 2',
                    start: '2024-02-15 10:00',
                    end: '2024-02-15 11:00',
                },
            ],
        };
    }
}
```

- Style the timegrid component (in your component, i.e. *app.component.css*)

```css
hf-timegrid {
    display: block;
    width: 100%;
    height: 100%;
    border: 2px solid #ddd;
    border-radius: 10px;
}
```

- Use the custom `hf-timegrid` element anywhere in your template:

```html
<hf-timegrid [startDate]="startDate" [config]="timegridConfig"></hf-timegrid>
```

## License (see [LICENSE](https://hexaflexa.com/docs/LICENSE))

Non-Commercial Use Only License

Free for Non-Commercial Use: Non-exclusive, worldwide, royalty-free license to use the Component for non-commercial purposes only. You must ensure that the "Powered by HexaFlexa" mention is prominently displayed in the bottom-right corner of the Timegrid. If you wish to hide this mention, you must obtain a paid license for non-commercial use.

Commercial Use Restricted: You may not use the Component for any commercial purposes without obtaining a separate commercial license.

© 2024 HexaFlexa. All rights reserved.
