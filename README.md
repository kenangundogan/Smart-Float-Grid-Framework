# Smart Grid Framework (Sass/Scss/Css)
Simple grid layouts to get you familiar with building within the "SASS/SCSS GRID FRAMEWORK" grid system.


## Variable (SCSS)
```javascript
  $grid-name: "grid";

  $grid-columns:               12 !default;
  $grid-margin-width:          20px !default;

  $screen-xs:                  424px !default;
  $screen-sm:                  768px !default;
  $screen-md:                  1024px !default;
  $screen-lg:                  1279px !default;
  $screen-xl:                  1366px !default;
```

## Grid Wrapper (SCSS)
Creates a wrapper for a series of grid
```javascript
  @mixin make-row($margin: $grid-margin-width) {
    margin-left: ceil(($margin / -2));
    margin-right: floor(($margin / -2));
    position: relative;
    &:after,
    &:before {
        content: " ";
        display: table;
    }
    &:after {
        clear: both;
    }
  }

  .grid-row{
      @include make-row;
  }
```

## Make Grid (SCSS)

```javascript
// grid property
%grid-property {
    position: relative;
    padding-left: 10px;
    padding-right: 10px;
}


// grid array (type,size) list
$grid-type-list: (xs, $screen-xs),(sm, $screen-sm),(md, $screen-md),(lg, $screen-lg),(xl, $screen-xl);


// make grid all-size (default attribute)
@each $item, $grid-type in $grid-type-list {
    @for $i from 1 through $grid-columns {
        .#{$grid-name}-#{$item}-#{$i} { @extend %grid-property; }
    }
}


// make grid function
@mixin make-grid($item){
    @for $i from 1 through $grid-columns {
        .#{$grid-name}-#{$item}-#{$i} {
            width: (100% / $grid-columns) * $i;
            float: left;
        }
    }
}


// make scren-size grid
@each $item, $screen-size in $grid-type-list {
    @if ($item!="xs") {
        @media (min-width: $screen-size) {
            @include make-grid($item);
        }
    }
    @else{
        @include make-grid($item);
    }
}

```



## Grid Media Screen Size (-xs-sm-md-lg-xl)

| Media Screen Size  | < 424px          | < 768px         | < 1024px        | < 1279px        | < 1366px        |
| :----------------- |:----------------:|----------------:|----------------:|----------------:|----------------:|
| 100% / 12 * 1      | grid-xs-1        | grid-sm-1       | grid-md-1       | grid-lg-1       | grid-xl-1       |
| 100% / 12 * 2      | grid-xs-2        | grid-sm-2       | grid-md-2       | grid-lg-2       | grid-xl-2       |
| 100% / 12 * 3      | grid-xs-3        | grid-sm-3       | grid-md-3       | grid-lg-3       | grid-xl-3       |
| 100% / 12 * 4      | grid-xs-4        | grid-sm-4       | grid-md-4       | grid-lg-4       | grid-xl-4       |
| 100% / 12 * 5      | grid-xs-5        | grid-sm-5       | grid-md-5       | grid-lg-5       | grid-xl-5       |
| 100% / 12 * 6      | grid-xs-6        | grid-sm-6       | grid-md-6       | grid-lg-6       | grid-xl-6       |
| 100% / 12 * 7      | grid-xs-7        | grid-sm-7       | grid-md-7       | grid-lg-7       | grid-xl-7       |
| 100% / 12 * 8      | grid-xs-8        | grid-sm-8       | grid-md-8       | grid-lg-8       | grid-xl-8       |
| 100% / 12 * 9      | grid-xs-9        | grid-sm-9       | grid-md-9       | grid-lg-9       | grid-xl-9       |
| 100% / 12 * 10     | grid-xs-10       | grid-sm-10      | grid-md-10      | grid-lg-10      | grid-xl-10      |
| 100% / 12 * 11     | grid-xs-11       | grid-sm-11      | grid-md-11      | grid-lg-11      | grid-xl-11      |
| 100% / 12 * 12     | grid-xs-12       | grid-sm-12      | grid-md-12      | grid-lg-12      | grid-xl-12      |


## Example 1 (Simple)

```javascript
  <div class="grid-row">
    <div class="grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-sm-8 mb-20">.grid-sm-8</div>
    <div class="grid-sm-3 mb-20">.grid-sm-3</div>
    <div class="grid-sm-3 mb-20">.grid-sm-3</div>
    <div class="grid-sm-3 mb-20">.grid-sm-3</div>
    <div class="grid-sm-3 mb-20">.grid-sm-3</div>
  </div>
```


## Example 2

```javascript
  <div class="grid-row">
    <div class="grid-xs-12 grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-xs-12 grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-xs-12 grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-xs-12 grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-xs-12 grid-sm-4 mb-20">.grid-sm-4</div>
    <div class="grid-xs-12 grid-sm-4 mb-20">.grid-sm-4</div>
  </div>
```

## Example 3 (complex)

```javascript
  <div class="grid-row">
      <div class="grid-xs-12 grid-sm-4 two">
          <div class="grid-row">
              <div class="grid-xs-12 mb-20">.grid-sm-12</div>
              <div class="grid-xs-12">.grid-sm-12</div>
          </div>
      </div>

      <div class="grid-xs-12 grid-sm-8">
          <div class="grid-row">
          
              <div class="grid-xs-12 grid-sm-5 mb-20">.grid-sm-5</div>
              <div class="grid-xs-12 grid-sm-7 mb-20">.grid-sm-7</div>
              <div class="grid-xs-12 grid-sm-5 mb-20">.grid-sm-5</div>
              <div class="grid-xs-12 grid-sm-7">.grid-sm-7</div>

              <div class="grid-xs-12 grid-sm-12 two">
                  <div class="grid-row">
                      <div class="grid-xs-12 grid-sm-5">.grid-sm-5</div>
                      <div class="grid-xs-12 grid-sm-7">
                          <div class="grid-row">
                              <div class="grid-xs-12 grid-sm-6">.grid-sm-6</div>
                              <div class="grid-xs-12 grid-sm-6">.grid-sm-6</div>
                          </div>
                      </div>
                  </div>
              </div>

          </div>
      </div>
  </div>
```


## Browser support
- Google Chrome (latest)
- Opera (latest)
- Firefox (latest)
- Safari 6.2+
- Internet Explorer 8+
- iOS 7+
- Android 4.4+
- Windows Phone 8.1+
