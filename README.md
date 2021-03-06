# react-parallax [![NPM version][npm-image]][npm-url]

## Install

```sh
yarn add react-parallax
```

### [Demo on codesandbox](https://codesandbox.io/embed/r0yEkozrw?view=preview)

## Contribute

If you find any bug or have problems and/or ideas regarding this library feel free to open an issue or pull request. Either way please create a working example so I can reproduce it. Link to a repository or even easier - fork the demo codesandbox project. This would help a lot.

This project is maintained during evenings and weekends. If you like it, please consider to buy me a coffee ;-) ...or contribute in other ways.

<a href="https://www.buymeacoffee.com/rrutsche" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Donate" style="height: auto !important;width: auto !important;" ></a>

## Usage

```javascript
import React from 'react';
import { Parallax, Background } from 'react-parallax';

const MyComponent = () => (
    <div>
        {/* -----basic config-----*/}
        <Parallax
            blur={10}
            bgImage={require('path/to/image.jpg')}
            bgImageAlt="the cat"
            strength={200}
        >
            Put some text content here - even an empty div with fixed dimensions to have a height
            for the parallax.
            <div style={{ height: '200px' }} />
        </Parallax>

        {/* -----dynamic blur-----*/}
        <Parallax
            blur={{ min: -15, max: 15 }}
            bgImage={require('path/to/another/image.jpg')}
            bgImageAlt="the dog"
            strength={-200}
        >
            Blur transition from min to max
            <div style={{ height: '200px' }} />
        </Parallax>

        {/* -----custom background element-----*/}
        <Parallax strength={300}>
            <div>Use the background component for custom elements</div>
            <Background className="custom-bg">
                <img src="http://www.fillmurray.com/500/320" alt="fill murray" />
            </Background>
        </Parallax>

        {/* -----renderProp: "renderLayer"-----*/}
        <Parallax
            bgImage={'/path/to/another/image'}
            strength={400}
            renderLayer={percentage => (
                <div
                    style={{
                        position: 'absolute',
                        background: `rgba(255, 125, 0, ${percentage * 1})`,
                        left: '50%',
                        top: '50%',
                        width: percentage * 500,
                        height: percentage * 500,
                    }}
                />
            )}
        >
            <p>... Content</p>
        </Parallax>
    </div>
);
export default MyComponent;
```

## Background Component

For more flexibility and styling purposes you can add a `<Background></Background>` section to your Parallax Container. Child nodes inside this Background will be positioned like the bgImage behind the other children. Compared to the bgImage there is no automatic scaling (see above).
## Props

| Name                  |   Type        | Default                   | Description                                                                                                                                                           | example                                                                                                |
| --------------------- | :-----------: | :-----------------------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------------------------------------------------------------------------------------------------ |
| **bgImage**           | `String`      |                           | path to the background image that makes parallax effect                                                                                                               |                                                                                                        |
| **bgImageAlt**        | `String`      |                           | alt text for bgImage.                                                                                                                                                 |                                                                                                        |
| **bgImageSize**       | `String`      |                           | img `sizes` attribute.                                                                                                                                                |                                                                                                        |
| **bgImageSrcSet**     | `String`      |                           | img `srcset` attribute                                                                                                                                                |                                                                                                        |
| **style**             | `Object`      |                           | style object for the component itself                                                                                                                                 |                                                                                                        |
| **bgStyle**           | `Object`      |                           | additional style object for the bg image/children  [Valid style attributes](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference)                |                                                                                                        |
| **bgClassName**       | `String`      |                           | custom classname for image                                                                                                                                            |                                                                                                        |
| **contentClassName**  | `String`      | `react-parallax-content`  | custom classname for parallax inner                                                                                                                                   |                                                                                                        |
| **bgImageStyle**      | `Object`      |                           | set background image styling                                                                                                                                          | `{height: '50px', maxWidth: '75px', opacity: '.5'}`                                                    |
| **strength**          | `Number`      | `100`                     | parallax effect strength (in pixel). this will define the amount of pixels the background image is translated                                                         |                                                                                                        |
| **blur**              | `Number`      | `0` or  `{min:0, max:5}`  | number value for background image blur or object in format `{min:0, max:5}` for dynamic blur depending on scroll position                                             |                                                                                                        |
| **renderLayer**       | `Function`    |                           | Function that gets a percentage value of the current position as parameter for custom calculationa. It renders a layer above the actual background, below `children`. | `renderLayer={percentage => (<div style={{ background:｀rgba(255, 125, 0, ${percentage * 1})｀}}/> )}`  |
| **disabled**          | `Booleam`     | `false`                   | turns off parallax effect if set to true                                                                                                                              | `{height: '50px', maxWidth: '75px', opacity: '.5'}`                                                    |
| **className**         | `String`      |                           | set an additional className                                                                                                                                           |                                                                                                        |
| **parents**           | `Node`        | `document`                | set optional parent for nested scrolling                                                                                                                              |                                                                                                        |
| **children**          |               |                           | used to display any content inside the react-parallax component                                                                                                       |                                                                                                        |

## Development

Initial set up, run:

```sh
npm install / yarn
```

Development, live reload, JSX transpiling, run:

```sh
npm run dev
```

Port 3000 on all OS by default. Can be set with option -port=8080

# License

MIT

[npm-image]: https://img.shields.io/npm/v/react-parallax.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/react-parallax
