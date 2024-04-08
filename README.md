This is [Setupad's](https://setupad.com/?utm_source=npmjs&utm_medium=link&utm_campaign=stpd-ad-component) banner component designed for React applications. It is compatible with React version 16 and above, as well as with the Next.js framework. Below you'll find instructions on how to correctly implement it.

## Getting Started

First of all, you need to install the package by running command:

`npm install stpd-ad-component`

Link to package: [stpd-ad-component](https://www.npmjs.com/package/stpd-ad-component)

## Usage

The package contains one component which is used to display ads. The component takes several props, some are required and some are optional:

### Required props

1. adUnitPath - a string containing ad unit path. Example: `'/147246189/example.com_300x600_sidebar_1'`
2. size - array of sizes for the corresponding ad unit. Example: `[[300, 600], [300, 300], [160, 600]]`
3. divId - a string containing id of the div where the ad will be displayed. Example: `'sidebar_1'`

### Optional props

1. className - a string containing class name for the container where the ad will be displayed.
2. threshold - a number which determines pixel offset before the banner is displayed. Since the component has a built-in lazy loading, the banner will be displayed only when it is close to the viewport. **The default value is 400px.**
3. refreshOnUrlChange - a boolean which determines whether the banner should be refreshed when the url changes. **The default value is false.**
4. lazy - a boolean which determines whether the banner should be lazy loaded. **The default value is true.**

## Example

Example below will show you how to import and use our component.

Lets say you'd like to add a sidebar banner to your website and after receiving our configuration, your ad unit looks like this: `googletag.defineSlot('/147246189/example.com_300x600_sidebar_1', [[300, 600], [300, 300]], 'example_com_sidebar_1').addService(googletag.pubads());`

### 1. Head configuration

Before working with component, make sure that your app has the required scripts inserted in `<head>` section of your application. Example:

```html
<script src="https://securepubads.g.doubleclick.net/tag/js/gpt.js" async></script>
<script>
    window.googletag = window.googletag || {cmd: []};
    stpd = window.stpd || {que: []};
    googletag.cmd.push(function () {
        googletag.pubads().enableSingleRequest();
        googletag.pubads().disableInitialLoad();
        googletag.enableServices();
        googletag.display(interstitialSlot);
    });
</script>
<script src="https://stpd.cloud/assets/hb/example.js" async></script>
```



### 2. Import the component

After installing our package, first thing you'll need to do is import our component:

```jsx
import StpdBannerComponent from 'stpd-ad-component';
```


### 3. Add the component to your code

After importing the component, you can add it to your code in the specific place where jsx is rendered.

Example of how to use it:

```jsx
<StpdBannerComponent
    adUnitPath={'/147246189/example.com_300x600_sidebar_1'}
    size={[[300, 600], [300, 300]]}
    divId={'example_com_sidebar_1'}
    className={'sidebar_banner_style'}
    threshold={200}
    refreshOnUrlChange={true}
/>
```

As you can see from the above example, we've taken parts of the `googletag.defineSlot('/147246189/example.com_300x600_sidebar_1', [[300, 600], [300, 300]], 'example_com_sidebar_1').addService(googletag.pubads());` code and used them as props in the component.

From the required props, adUnitPath and size should match the ones that were given in the initial config, meanwhile divId can be anything you'd like.

