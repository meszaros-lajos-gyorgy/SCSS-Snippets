# SCSS-Snippets

SCSS codes/snippets to help your work.

**g.scss**

This function creates a grey color. It requires one hexadecimal number as a parameter and it will triple it over R, G and B channels. It will make a grey color stand out a bit more in your css

    p{
      color : g(3f); // color : #3f3f3f
    }

    a{
      background : url("test.png") no-repeat g(7); // background : url("test.png") no-repeat #777777;
    }

**gradient.scss**

This code allows you to generate gradients.

    // Simple 2 color gradient in all browsers
    .gradient-bg{
      @each $prefix in $vendor_prefixes{
        background : gradient($prefix, top, #2e2e2e, #9a47b2);
      }
    }

    // Gradient for IE
    body.ie .gradient-bg{
      zoom : 1;
      filter : gradient-ie(top, #2e2e2e, #9a47b2);
    }

    // Complex gradient with multiple specified steps and with more css background elements
    .gradient-bg-with-color{
      @each $prefix in $vendor_prefixes{
        $color : #00f;
        background : gradient($prefix, top, rgba($color, .75) 0%, rgba($color, .35) 50%, rgba($color, 0) 100%), green;
      }
    }

**selector.scss**

Helps interpolating a list of selector strings

    $sel : "i" "em";

    // no append : body i, body em{  }
    body{
      #{selector($sel)}{ // will return "i, em"
        font-style : normal;
      }
    }

    // append before : p>i, p>em{ }
    p{
      #{selector($sel, "&>")}{ // will return "&>i, &>em"
        font-style : italic;
      }
    }

    // append after : i span, em span{ }
    span{
      #{selector($sel, "", " &")}{ // will return "i &, em &"
        color : blue;
      }
    }

**strip-units.scss**

This code strips the units of a number. [Origin](http://stackoverflow.com/questions/12328259/how-do-you-strip-the-unit-from-any-number-in-sass/12335841#12335841)

**user-select.scss**

This mixin makes an element unselectable.

    h1.dont-highlight{
      @include unselectable;
    }
