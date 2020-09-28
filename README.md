<p align="center">
<h1>The Mysterious Garden: CSS Only</h1>
<img src="https://thumbs.gfycat.com/NeglectedMetallicAmericanbittern-size_restricted.gif" alt="Bulbasaur's Mysterious Garden">
</p>

## 🌱 Summary

> People have always disagreed whether Bulbasaur is a plant or an animal. Bulbasaur might be a symbol that all life on Earth is connected. -[Bulbapedia](https://bulbapedia.bulbagarden.net/wiki/EP051)

Who could forget one of most [beautifully animated](https://twitter.com/BulbaGanda/status/1182289324752158720) episodes of _Pokémon_ during its time, featuring the coolest Pokemon ever? I've marathoned _Pokémon_ in Japanese as a supplement for my Japanese studies during quarantine. It added some much needed merriment and euphoria to my days.

I felt compelled to recreate a scene from _The Mysterious Garden_ episode to practice composition, and performant paradigms to minimize CPU usage and jank, especially on machines without a discrete graphics card (such as the Macbook Pro I used to create this). The beauty of this animation is its propensity to test the limits of CSS and the [graphics pipeline](https://en.wikipedia.org/wiki/Graphics_pipeline#Scan_conversion_or_rasterization) for the web.

> If you can't experiment in your own personal projects, how are we ever going to get progress in our real production commercial projects? It takes a community willing to explore. -[Shawn Wang at "JAMStack - The Total Victory of JavaScript"](https://youtu.be/WVayQ66AGa4?t=1410)

## ✨ Additional Links

- [Watch the speed coding video with mockups, explanations, resources, and soothing background music](https://youtu.be/WKuM7kIAhNU)
- [Checkout the result on CodePen](https://codepen.io/cybercountess/pen/xxwKRx)

## 💻 Featured Snippets

The following snippets are Sass mixins and functions used throughout the animation for development ease.

#### Linear Gradient Mixin:

```scss
@mixin linear-gradient($gradient-args...) {
  $fallback: nth($gradient-args, 2);
  background-color: $fallback;
  background-image: -webkit-linear-gradient($gradient-args);
  background-image: linear-gradient($gradient-args);
}
```

- Receives a list of gradient arguments, including the direction.
- Uses the first color argument as a fallback for unsupported browsers.
- Adheres to DRY Principles (Don't Repeat Yourself) and abstracts the gradient property across the stylesheet.
- Adheres to the [Single-responsibility Principle](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html) coined by [Robert C. Martin](https://en.wikipedia.org/wiki/Robert_C._Martin), which states that every class, module, or function in a program should be responsible over a single part of a program's functionality. In this case, this mixin is responsible for the background images across the stylesheet.
- **NOTE:** Does not support multiple gradients yet.

#### Random Number Generator:

```scss
@function randomNum($min, $max) {
  $rand: random();
  @return ($min + floor($rand * (($max - $min) + 1)));
}
```

- Outputs a random number with an approximate uniform distribution.
- Works with any CSS unit of measure.
- Used for randomly selecting list elements, or animation durations.
