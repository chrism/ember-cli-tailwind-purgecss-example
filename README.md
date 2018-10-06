# Ember CLI Tailwind Purgecss Example

A simple Ember application to understand how to add [purgecss](https://www.purgecss.com/) to a project using [ember-cli-tailwind](https://github.com/embermap/ember-cli-tailwind/).

Uses

- Ember 3.4.4
- Ember Postcss 4.0.0
- Ember CLI Tailwind 0.6.2

Tailwind works perfectly prior to installing

- [@fullhuman/postcss-purgecss](https://github.com/FullHuman/postcss-purgecss)
- [ember-cli-postcss](https://github.com/jeffjewiss/ember-cli-postcss)

and adding this code to `ember-cli-build.js`

```js
module.exports = function(defaults) {
  let app = new EmberApp(defaults, {
    postcssOptions: {
      compile: {
        enabled: false
      },
      filter: {
        enabled: true,
        plugins: [
          {
            module: purgecss,
            options: {
              content: ['./app/**/*.hbs', './app/**/.js']
            }
          }
        ]
      }
    }
  });
  return app.toTree();
};
```

Doing this results with no styling being kept and this error message in the console.

```
Refused to apply style from 'http://localhost:4200/assets/ember-cli-tailwind-purgecss-example.css' because its MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.
```

It doesn't seem like that file gets generated.

Something else—I've noticed is if I `ember build --environment=production` then all the JS files are generated separately, rather than compiled.

Any help/suggestions much appreciated.
