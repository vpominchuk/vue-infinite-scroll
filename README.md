![](https://banners.beyondco.de/Infinite%20Scroll%20for%20Vue3.png?theme=light&packageManager=npm+install&packageName=%40vpominchuk%2Fvue-infinite-scroll&pattern=texture&style=style_1&description=vue-infinite-scroll+is+an+infinite+scroll+component+for+Vue3&md=1&showWatermark=0&fontSize=100px&images=search)

# Infinite Scroll for Vue3

A super simple and lightweight package allowing you to implement infinite scroll on your project in a seconds.

## Installation

`npm i @vpominchuk/vue-infinite-scroll`

## Example

To try an example, create a new folder out of your project.
Install vue-infinite-scroll package and run `npm run serve` command

```
mkdir vue-infinite-scroll-exampe
cd vue-infinite-scroll-exampe
npm i @vpominchuk/vue-infinite-scroll
cd node_modules/@vpominchuk/vue-infinite-scroll/
npm i
npm run serve
```

If you are using Windows platform try 
`npm run serve-win`

Open http://localhost:8080/ in your favorite browser

Remove `node_modules` inside `@vpominchuk/vue-infinite-scroll/` after tests.

## Usage

To use the component, simply add

`<infinite-scroll :active="true" distance="50px" auto-load="true" @process="load" />`

to the bottom of your page.

### Properties
`active`: Boolean

`distance`: String - distance from the bottom side of the page when component fires @process event to load the content.
"200px" is a good enough, but you can choose any other value.

`auto-load`: Boolean - fire @process event on component mount

### Event

`@process`: Callback function - fires when user scrolls to the bottom side of the page. Load a new portion of your content here.

## Sample

Please check `dev/` folder for simple usage sample.


