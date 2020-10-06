# How to use, customize and extend bootstrap

## About terms

> **Customization** - The action of modifying something to suit a particular individual or task.

> **Extensibility** - The quality of being designed to allow the addition of new capabilities or functionality.

\- [Oxford Dictionary](https://www.lexico.com/)

## Content
1. [Bootstrap usage](#bootstrap-usage)
   1. [Source code](#source-code)
   2. [Javascript](#javascript)
   3. [How to use](#how-to-use)
2. [Bootstrap customization](#bootstrap-customization)
   1. [Theme Builder and other utilities](#theme-builder-and-other-utilities)
   2. [Shared variables](#shared-variables)
   3. [Component style variables](#component-style-variables)
   4. [Feature switches](#feature-switches)
3. [Bootstrap extensibility](#bootstrap-extensibility)
   1. [Maps and loops](#maps-and-loops)
   2. [Mixins](#mixins)
   3. [Modifiers](#modifiers)
   4. [Encapsulation](#encapsulation)

## Bootstrap usage

### Source code

Bootstrap [provide](https://getbootstrap.com/docs/4.5/getting-started/download/) different ways to include it into your project: use pre-compiled bundle from CDN, use package manager like npm or yarn or compile it from source code.
* For fast startup, it's better to include [full bundle](https://getbootstrap.com/docs/4.5/getting-started/contents/#precompiled-bootstrap) and just use any of available features.
* For performance, it's better to [leave only code you needed](https://getbootstrap.com/docs/4.5/getting-started/contents/#bootstrap-source-code): just include variables, utilities and only needed components in same order as in `bootstrap.scss`

### Javascript

By default, bootstrap (v3, v4) shipped with javascript components based on jquery. If you use React, angular.js, Angular or Vue.js, use one of the following replacements or find better one:
* [React Bootstrap](https://react-bootstrap.github.io/)
* [Angular UI Bootstrap](https://angular-ui.github.io/bootstrap/)
* [ng-bootstrap](https://ng-bootstrap.github.io/) or [ngx-bootstrap](https://valor-software.com/ngx-bootstrap/)
* [BootstrapVue](https://bootstrap-vue.org/)

### How to use

Just read Bootstrap documentation:
* [v3](https://getbootstrap.com/docs/3.4/)
* [v4](https://getbootstrap.com/docs/4.5/getting-started/introduction/)
* [v5](https://v5.getbootstrap.com/)

Bootstrap 5 documentation is much better than v3 and v4. While it's newer and include v5-specific things, most of content are still applicable for older versions of bootstrap.

## Bootstrap customization

A little note about difference between Bootstrap 4 and 3 from authors of Bootstrap:

> In Bootstrap 3, theming was largely driven by variable overrides in LESS, custom CSS, and a separate theme stylesheet that we included in our dist files. With some effort, one could completely redesign the look of Bootstrap 3 without touching the core files. Bootstrap 4 provides a familiar, but slightly different approach.
>
> Now, theming is accomplished by Sass variables, Sass maps, and custom CSS. There's no more dedicated theme stylesheet; instead, you can enable the built-in theme to add gradients, shadows, and more.

### Theme builder and other utilities

[Bootstrap Build](https://bootstrap.build/) allows you quickly & easy customize Bootstrap (make theme) with real time preview for all Bootstrap controls.

You also may read about [other useful utilities](https://habr.com/ru/post/520788/) (Russian).

### Shared variables

The primary customization way for Bootstrap is to override Bootstrap variable values.

If you need to change backgrounds, borders, sizes, margins & paddings and other common parts of HTML elements and Bootstrap components for *all their instances across the site*, then you need to override Bootstrap variable values.

#### Default values

> Every Sass variable in Bootstrap 4 includes the !default flag allowing you to override the variable's default value in your own Sass without modifying Bootstrap's source code. Copy and paste variables as needed, modify their values, and remove the !default flag. If a variable has already been assigned, then it won't be re-assigned by the default values in Bootstrap.

##### Links

https://getbootstrap.com/docs/3.4/css/#less-variables  
https://getbootstrap.com/docs/4.5/getting-started/theming/#variable-defaults

#### Do

Use bootstrap variables to change color palette:

##### Default
```scss
// v3
$brand-primary: darken(#428bca, 6.5%) !default;
// v4
$primary: $blue !default;
```
![](assets/bootstrap/variables-primary-default.png)
##### Customized
```scss
// v3
$brand-primary: #e51400;
// v4
$primary: #e51400;
```
![](assets/bootstrap/variables-primary-custom.png)

##### Why?

This is built-in functionality to customize Bootstrap. You probably always will have primary and some additional colors (like for errors, warnings) in your color palette, so why don't use something already exists?

##### Links

https://getbootstrap.com/docs/3.4/css/#less-variables-colors  
https://getbootstrap.com/docs/4.5/getting-started/theming/#theme-colors

#### Do

Use bootstrap variables to change global colors of primary HTML elements such as `body` or links, set primary font family or change font sizes:

##### Default
```scss
// v3
$body-bg: #fff !default;
$link-color: $brand-primary !default;
$font-family-sans-serif: "Helvetica Neue", Helvetica, Arial, sans-serif !default;
$font-size-base: 14px !default;
// v4
$body-bg: $white !default;
$link-color: theme-color("primary") !default;
$font-family-sans-serif: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji" !default;
$font-size-base: 1rem !default;
```
![](assets/bootstrap/variables-bg-links-default.png)
##### Customized
```scss
// v3
$body-bg: #000;
$link-color: $brand-warning;
$font-family-sans-serif: "Comic Sans MS", "Helvetica Neue", Helvetica, Arial, sans-serif;
$font-size-base: 21px;
// v4
$body-bg: $black;
$link-color: theme-color("warning");
$font-family-sans-serif: "Comic Sans MS", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
$font-size-base: 1.5rem;
```
![](assets/bootstrap/variables-bg-links-custom.png)

##### Why?

These colors often used in Bootstrap classes, so if you want to change body background or link colors, then you want to also change all places in code which base their styles in these colors.

##### Links

https://getbootstrap.com/docs/3.4/css/#less-variables-scaffolding  
https://getbootstrap.com/docs/4.5/content/reboot/#page-defaults  
https://getbootstrap.com/docs/4.5/content/typography/#global-settings

#### Do

Use Bootstrap variables to configure default margins & paddings (spaces in Bootstrap v4)

#### Don't

Use "random" - not stored in existing variables or extended maps [see below] - spacing. // TODO: Add link

##### Default
```scss
// v3
$padding-base-vertical: 6px !default;
$padding-base-horizontal: 12px !default;
// v4
$spacer: 1rem !default;
```
##### Customized
```scss
// v3
$padding-base-vertical: 10px;
$padding-base-horizontal: 20px;
// v4
$spacer: 1.25rem;
```

##### Why?

Bootstrap SCSS contains calculations based on these variables, for example:
```scss
// v3
//** Default `.form-control` height
$input-height-base: ($line-height-computed + ($padding-base-vertical * 2) + 2) !default;
//v4
$input-height: add($input-line-height * 1em, add($input-padding-y * 2, $input-height-border, false)) !default;
```
These calculations allow to correctly position elements on layout and prevent it breaking.

###### Layout with control sizes based on variables
![](assets/bootstrap/layout-calculated.png)

###### Layout with random control sizes
![](assets/bootstrap/layout-random-spacing.png)


##### Links

https://getbootstrap.com/docs/3.4/css/#less-variables-components  
https://getbootstrap.com/docs/4.5/utilities/spacing/

## Bootstrap extensibility

### Mixins

Reuse Bootstrap mixins or write yourself.

#### Do

If you add styles similar to already existing in Bootstrap, then first try to find mixin for that. Probably it exists and will allow you to make your work in single line.

Bootstrap provide some mixins to allow you automate some style generation, for example:
1. Add new color variants for buttons, alerts, background helper
2. Add new sizes for buttons, pagination or set width & height for any element
3. Set border radiuses, add shadow or gradients
4. Add grid implicitly to custom classes
5. Add helpers to custom classes

```scss
@include media-breakpoint-up(sm) {
  // write here styles which will be visible at small and larger screen sizes
}
```

#### Do

If you have multiple similar places in your scss, then probably you may reuse this code, may be with some parameters.

```scss
@mixin vc-flying-placeholder-size($input-class, $padding-horizontal, $padding-vertical) {
    input[vc-flying-placeholder],
    textarea[vc-flying-placeholder],
    select[vc-flying-placeholder] {
      &#{$input-class} ~ label.vc-flying-placeholder-class {
        left: $padding-horizontal - $padding-xs-horizontal + 1px; // 1px = border width
        top: $padding-vertical + 1px; // 1px = border
      }
    }
  }

@mixin vc-labeled-input-size($input-class, $padding-horizontal, $padding-vertical) {
  vc-labeled-input input {
    &#{$input-class} ~ label {
      left: $padding-horizontal - $padding-xs-horizontal + 1px; // 1px = border width
      top: $padding-vertical + 1px; // 1px = border
    }
  }
}
```

#### Don't

Don't use [deprecated vendor mixins](https://getbootstrap.com/docs/4.5/migration/#vendor-prefix-mixins) or write vendor prefixes. Instead, use [Autoprefixer](https://github.com/postcss/autoprefixer).

#### Why?

1. Code reuse. You don't need to reinvent the wheel. If something already exist - use that.
2. Forgotten features. Mixin for new button color variant already include all needed styles, including styles hover, pressing or focus states. `color-yiq` mixin will always set color contrast to used background, so you never will forgot to make text visible on bright element.
3. Single place to change. If you will always use same mixing to set, for example, specific spacing & size to some elements, then modification

#### Citations

> Utility mixins are mixins that combine otherwise unrelated CSS properties to achieve a specific goal or task.

#### Programming principles

[Code reuse](https://en.wikipedia.org/wiki/Code_reuse)  
[Open-closed principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)  
[Dependency inversion principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle)  

#### Links

https://getbootstrap.com/docs/3.4/css/#less-mixins-utility  
https://getbootstrap.com/docs/4.5/utilities/float/#mixins 
https://getbootstrap.com/docs/4.5/layout/grid/#sass-mixins  
https://www.sass-lang.com/documentation/at-rules/mixin

### Modifiers

Use modifiers to extend existing component styles.

#### Do

If you need to add *yet another variant* of existing component, like button, then use modifiers (suach as built-in `.btn-primary`) to do that.

#### Do

Use modifiers when you need to do multiple changes or use custom values, such as change both background, border and color or change set padding values specific to this component.

The following code will add provide `.btn-white` modifier (with white background) for buttons:
```scss
// v3
.btn-white {
  @include button-variant($btn-white-color, $btn-white-bg, $btn-white-border);
}
```

#### Don't

Don't use modifiers for providing simple, not reused changes, such as background only change of specific button. Use encapsulation instead.

#### Don't

Don't use modifiers for providing simple, but reused changes, such as new variation of background available to be used in any component.

#### Why?

If you will change existing variant directly, then:
1. You may loose existing style, i.e. if you will set white colors to `.btn-primary` class, then you will not be able to use button with primary background in HTML
2. This change may break layout, i.e. if yor primary color is red and page background is white, then set white background to `.btn-primary` class will make this button invisible.

#### How problem solved in frameworks?

There are existing frameworks, approaches and tools which implement these approach, such as popular [BEM methodology](http://getbem.com/). Unfortunately, they are incompatible with Bootstrap without singnificant relaxing of their rules. Bootstrap use some parts of these approaches.

#### Citations

> As such, components should be built with a base class that houses common, not-to-be overridden property-value pairs. For example, .btn and .btn-primary. We use .btn for all the common styles like display, padding, and border-width. We then use modifiers like .btn-primary to add the color, background-color, border-color, etc.
> 
> Modifier classes should only be used when there are multiple properties or values to be changed across multiple variants. Modifiers are not always necessary, so be sure you-re actually saving lines of code and preventing unnecessary overrides when creating them. Good examples of modifiers are our theme color classes and size variants.

#### Links

https://getbootstrap.com/docs/4.5/extend/approach/#classes
http://getbem.com/introduction/
// TODO: add links to upcoming sections of helpers and encapsulation

### Encapsulation

Encapsulate component-specific code into special classes or use framework possibilities.

#### Do

If you need to changes styles specific for some components or situations, like adding spacing before icon, then always encapsulate these changes into specific classes, i.e.:
```scss
.category-page {
  .btn .fa {
    margin-left: $icon-space;
  }
}
```

#### Why?

If you will use global styles for this without encapsulation, these styles will be implemented across all applicable elements on site:

```scss
.btn .fa {
  margin-left: 5px;
}
```

#### How problem solved in frameworks?

Frameworks like Angular use [Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM) to [encapsulate](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)) styles, i.e. isolate styles from component to prevent their affection of global styles or another component styles.

#### Citations

> Components should be built with a base class and extended via modifier classes

> An important aspect of web components is encapsulation - being able to keep the markup structure, style, and behavior hidden and separate from other code on the page so that different parts do not clash, and the code can be kept nice and clean.

#### Programming principles

[Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming))  
[Single-responsibility principle](https://en.wikipedia.org/wiki/Single-responsibility_principle)  
[Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)  
[Interface segregation principle](https://en.wikipedia.org/wiki/Interface_segregation_principle)  

#### Links

* https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#Specificity
* https://getbootstrap.com/docs/4.5/extend/approach/#classes
* https://angular.io/guide/component-styles#view-encapsulation