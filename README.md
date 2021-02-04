# Fluid Slider

[![npm version](https://badge.fury.io/js/fluid-slider.svg)](https://badge.fury.io/js/fluid-slider)
[![DragsterJS gzip size](http://img.badgesize.io/https://raw.githubusercontent.com/fluidweb-co/fluid-slider/master/dist/fluid-slider.min.js?compression=gzip
)](https://raw.githubusercontent.com/fluidweb-co/fluid-slider/master/dist/fluid-slider.min.js)

Provide functions to handle animations and transitions gracefully. Execute a function before or after playing a css animation on an element.



## Installation

Setting up is pretty straight-forward. Just download the script from __dist__ folder and include it in your HTML:

```html
<script type="text/javascript" src="path/to/dist/fluid-slider.min.js"></script>
```

### NPM

Fluid Slider is also available on NPM:

```sh
$ npm install fluid-slider
```



## Initialization

Once the Fluid Slider script is loaded all functions will be available through the global variable `window.FluidSlider`, however to enable the slider components you need to call the function `init`:

Call the function `FluidSlider.init( options );` passing the `options` parameter as an object.



## Options Available

The `options` parameter accept any of the available options from the default settings by passing the new values as an object. You can simply ommit the options you don't want to change the default values of.

These are the currently accepted options with their default values, if in doubt check the source code:

```js
	var _defaults = {
		sliderWrapperSelector: '.slider-wrapper',
		sliderViewportSelector: '.slider-viewport',
		sliderContainerSelector: '.slider-container',
		sliderItemSelector: '.slider-item',
		isActivatedClass: 'is-activated',
		isDisabledClass: 'is-disabled',
		isResizingClass: 'is-resizing',
		isAnimatingClass: 'is-animating',
		isCurrentClass: 'is-current',
		
		slideSpacing: 0, // px
		slideSensitivity: 30, // % of slide item width
		touchEventsSensitivity: 25, // px
		
		slidesPerViewAttribute: 'data-slider-per-view',
		slidesPerView: {
			xs: { breakpointInitial: 0, breakpointFinal: 749, itemsPerView: 1 },
			md: { breakpointInitial: 750, breakpointFinal: 999, itemsPerView: 3 },
			ml: { breakpointInitial: 1000, breakpointFinal: 1199, itemsPerView: 4 },
			lg: { breakpointInitial: 1200, breakpointFinal: 1499, itemsPerView: 4 },
			xl: { breakpointInitial: 1500, breakpointFinal: 100000, itemsPerView: 4 }, // breakpointFinal can be any very high number
		},
		
		createNavigationButtons: false,
		createNavigationButtonsAttribute: 'data-slider-navigation-buttons',
		navigationButtonsSelector: '.slider-navigation',
		navigationPrevSelector: '.slider-navigation__prev',
		navigationNextSelector: '.slider-navigation__next',
		hasNavigationButtonsClass: 'has-navigation-buttons',
		navigationButtonsTemplate: '<div class="slider-navigation"><button class="slider-navigation__prev">Previous</button></div><button class="slider-navigation__next">Next</button></div>',
		
		createNavigationBullets: false,
		createNavigationBulletsAttribute: 'data-slider-navigation-bullets',
		navigationBulletsSelector: '.slider-navigation-bullets',
		navigationBulletItemSelector: '.slider-navigation-bullets__item',
		hasNavigationBulletsClass: 'has-navigation-bullets',
		navigationBulletsWrapperTemplate: '<div class="slider-navigation-bullets"></div>',
		navigationBulletItemTemplate: '<span class="slider-navigation-bullets__item"></span>',
	};
```

For example, if you want to enable the creation of navigation _buttons_ and _bullets_ for every Slider in your page (setting the default options for your project), initialize the component with the options below:

```js
var options = {
    createNavigationButtons: true,
    createNavigationBullets: true,
}
FluidSlider.init( options );
```

Everything else will use the default values.



## Basic Usage

### 1. Required HTML elements structure

The slider component requires the following HTML elements structure:

```html
<div class="slider-wrapper">
    <div class="slider-viewport">
        <div class="slider-container">
            <div class="slider-item"> Slider 1 </div>
            <div class="slider-item"> Slider 2 </div>
            <div class="slider-item"> Slider 3 </div>
            <div class="slider-item"> Slider 4 </div>
            <div class="slider-item"> Slider 5 </div>
            <div class="slider-item"> Slider 6 </div>
        </div>
    </div>
</div>
```

The elements for the navigation buttons and bullets are added during runtime. You can specify the HTML template to be used for these elements by changing the related options:

```js
var options = {
    navigationButtonsTemplate: '<your_navigation_buttons__html_template>',

    navigationBulletsWrapperTemplate: '<your_navigation_bullet__html_template>',
	navigationBulletItemTemplate: '<your_navigation_bullet_item__html_template>',
}
FluidSlider.init( options );
```

The HTML templates are useful to change not only the markup of the elements, for instance to add a specific class used in your project, but also to change the labels of these buttons to a translated text.

### 2. Using `data` attributes to change slider properties

Another way to change the behavior of a slider component is to add data attributes to specific elements, this is useful if you want to change the properties of one instance of the slider component but keep the other instances with the default options.

Again, to enable the creation of navigation buttons and bullets, but this time for only one instance of the slider component, supposing Fluid Slider was initialized with its default options:

```html
<div class="slider-wrapper" data-slider-navigation-buttons="true" data-slider-navigation-bullets="true">
    <div class="slider-viewport">
        <div class="slider-container">
            <div class="slider-item"> Slider 1 </div>
            <div class="slider-item"> Slider 2 </div>
            <div class="slider-item"> Slider 3 </div>
            <div class="slider-item"> Slider 4 </div>
            <div class="slider-item"> Slider 5 </div>
            <div class="slider-item"> Slider 6 </div>
        </div>
    </div>
</div>
```

Not all options can be set with `data` attributes, these are the available properties that can be set with `data` attributes:

- `data-slider-per-view`: used to set the value of the option `slidesPerView`, an JSON string is expected with the structure similar to the option default value.

- `data-slider-navigation-buttons`: used to set the value of the option `createNavigationButtons`, valid values are `true` or `false`.

- `data-slider-navigation-bullets`: used to set the value of the option `createNavigationBullets`, valid values are `true` or `false`.




## Contributing to Development

This isn't a large project by any means, but you are definitely welcome to contribute.

### Development environment

Clone the repo and run [npm](http://npmjs.org/) install:

```
$ cd path/to/fluid-slider
$ npm install
```

Run the build command:

```
$ gulp build
```

Build on file save:

```
$ gulp
$ gulp watch
```


## License

Licensed under MIT.
