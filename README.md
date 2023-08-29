# Setupad banner implementation guide for next.js app

Here you'll find an example code of how to implement setupad banner script to your next.js application and run these banners on your website.

## Content:

1. [Setupad config implementation](#setupad-config-implementation)
2. [Importing our config](#importing-our-config)
3. [Creating banner components](#creating-banner-components)

## Setupad config implementation

First of all, you'll need to implement our banner configuration to the head part of your application.
This configuration is usually sent by us and it looks like this:

```
    <!-- HEAD -->
<!--    Start of scripts for lazy loading-->
<script src="https://cdn.jsdelivr.net/npm/in-view@0.6.1/dist/in-view.min.js"></script>
<script>inView.offset(-200);</script>
<!--    End of scripts for lazy loading-->

<script src="https://securepubads.g.doubleclick.net/tag/js/gpt.js"></script>
<script>
    window.googletag = window.googletag || {cmd: []};
    googletag.cmd.push (function () {
        if(window.innerWidth >= 1600) {
          googletag.defineSlot('/21886670345/eltiempo.pe_300x600_side_rail_left', [[300,600],[160,600],[300,250],[300,300]], 'eltiempo_pe_side_rail_left').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_300x600_side_rail_right', [[300,600],[160,600],[300,250],[300,300]], 'eltiempo_pe_side_rail_right').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_1000x100_anchor_bottom', [[1000,100],[970,90],[728,90],[990,90],[970,50],[960,90],[950,90],[980,90]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_980×250_billboard_1', [[970,250],[980,250],[980,240],[980,120],[970,90],[728,90],[970,200],[970,120],[950,90],[728,100],[728,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
	} else if(window.innerWidth >= 1320) { 
          googletag.defineSlot('/21886670345/eltiempo.pe_160x600_side_rail_left', [[160,600],[120,600]], 'eltiempo_pe_side_rail_left').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_160x600_side_rail_right', [[160,600],[120,600]], 'eltiempo_pe_side_rail_right').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_1000x100_anchor_bottom', [[1000,100],[970,90],[728,90],[990,90],[970,50],[960,90],[950,90],[980,90]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_980×250_billboard_1', [[970,250],[980,250],[980,240],[980,120],[970,90],[728,90],[970,200],[970,120],[950,90],[728,100],[728,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
        } else if(window.innerWidth >= 1000) { 
          googletag.defineSlot('/21886670345/eltiempo.pe_1000x100_anchor_bottom', [[1000,100],[970,90],[728,90],[990,90],[970,50],[960,90],[950,90],[980,90]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_980×250_billboard_1', [[970,250],[980,250],[980,240],[980,120],[970,90],[728,90],[970,200],[970,120],[950,90],[728,100],[728,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
	} else if(window.innerWidth >= 768) {
          googletag.defineSlot('/21886670345/eltiempo.pe_728x90_anchor_bottom_tablet', [[728,90],[468,60]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_728x90_top_tablet', [[728,90],[468,60]], 'eltiempo_pe_top').addService(googletag.pubads());            
	  googletag.defineSlot('/21886670345/eltiempo.pe_336x336_billboard_1_tablet', [[336,336],[336,320],[320,336],[320,320],[300,300],[336,280],[320,250],[300,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
	} else {	
          googletag.defineSlot('/21886670345/eltiempo.pe_320x100_anchor_bottom_mobile', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_320x100_anchor_top_mobile', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_anchor_top_mobile').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_320x100_top_moblie', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_336x336_billboard_1_mobile', [[336,336],[336,320],[320,336],[320,320],[300,300],[336,280],[320,250],[300,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
        }
				
           var interstitialSlot = googletag.defineOutOfPageSlot('/21886670345/eltiempo.pe_Interstitial', googletag.enums.OutOfPageFormat.INTERSTITIAL);
           if (interstitialSlot) interstitialSlot.addService(googletag.pubads());

        googletag.pubads().enableSingleRequest();
        googletag.pubads().disableInitialLoad();
        googletag.pubads().collapseEmptyDivs();
        googletag.enableServices();
        googletag.display(interstitialSlot);
	window.stpd = window.stpd || {que: []};
         stpd.que.push((function() {
             stpd.initialize();
         }));    
    });
</script>
<script async src="https://stpd.cloud/saas/5747"></script>
```

Lets break this code down to further understand why we need this part in your head section:

### 1.1. Inview.js 3rd party library

```
<script src="https://cdn.jsdelivr.net/npm/in-view@0.6.1/dist/in-view.min.js"></script>
<script>inView.offset(-200);</script>
```

The first line is the script that will be used to lazy-load the banners. For that we use 3rd party library called inview.js.
The second line is the offset that will be used to load the banners.
The offset is the distance from the bottom of the screen to the top of the banner.
In this case, the offset is 200 pixels. This means that the banner will be loaded when the user scrolls to 200 pixels from the bottom of the screen.
The pixel value can be adjusted to personal preference.

### 1.2. Google Publisher Tag (GPT) script

```
<script src="https://securepubads.g.doubleclick.net/tag/js/gpt.js"></script>
```

The Google Publisher Tag (GPT) is an ad tagging library for Google Ad Manager which is used to dynamically build ad requests (https://developers.google.com/publisher-tag/guides/get-started).

### 1.3. Defining ad slots

Here you'll have to define the ad slots of banners which you want to show on your website:

```
<script>
    window.googletag = window.googletag || {cmd: []};
    googletag.cmd.push (function () {
        if(window.innerWidth >= 1600) {
          googletag.defineSlot('/21886670345/eltiempo.pe_300x600_side_rail_left', [[300,600],[160,600],[300,250],[300,300]], 'eltiempo_pe_side_rail_left').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_300x600_side_rail_right', [[300,600],[160,600],[300,250],[300,300]], 'eltiempo_pe_side_rail_right').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_1000x100_anchor_bottom', [[1000,100],[970,90],[728,90],[990,90],[970,50],[960,90],[950,90],[980,90]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_980×250_billboard_1', [[970,250],[980,250],[980,240],[980,120],[970,90],[728,90],[970,200],[970,120],[950,90],[728,100],[728,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
	} else if(window.innerWidth >= 1320) { 
          googletag.defineSlot('/21886670345/eltiempo.pe_160x600_side_rail_left', [[160,600],[120,600]], 'eltiempo_pe_side_rail_left').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_160x600_side_rail_right', [[160,600],[120,600]], 'eltiempo_pe_side_rail_right').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_1000x100_anchor_bottom', [[1000,100],[970,90],[728,90],[990,90],[970,50],[960,90],[950,90],[980,90]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_980×250_billboard_1', [[970,250],[980,250],[980,240],[980,120],[970,90],[728,90],[970,200],[970,120],[950,90],[728,100],[728,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
        } else if(window.innerWidth >= 1000) { 
          googletag.defineSlot('/21886670345/eltiempo.pe_1000x100_anchor_bottom', [[1000,100],[970,90],[728,90],[990,90],[970,50],[960,90],[950,90],[980,90]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_980×250_billboard_1', [[970,250],[980,250],[980,240],[980,120],[970,90],[728,90],[970,200],[970,120],[950,90],[728,100],[728,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
	} else if(window.innerWidth >= 768) {
          googletag.defineSlot('/21886670345/eltiempo.pe_728x90_anchor_bottom_tablet', [[728,90],[468,60]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_728x90_top_tablet', [[728,90],[468,60]], 'eltiempo_pe_top').addService(googletag.pubads());            
	  googletag.defineSlot('/21886670345/eltiempo.pe_336x336_billboard_1_tablet', [[336,336],[336,320],[320,336],[320,320],[300,300],[336,280],[320,250],[300,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
	} else {	
          googletag.defineSlot('/21886670345/eltiempo.pe_320x100_anchor_bottom_mobile', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_anchor_bottom').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_320x100_anchor_top_mobile', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_anchor_top_mobile').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_320x100_top_moblie', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_top').addService(googletag.pubads());            
          googletag.defineSlot('/21886670345/eltiempo.pe_336x336_billboard_1_mobile', [[336,336],[336,320],[320,336],[320,320],[300,300],[336,280],[320,250],[300,250]], 'eltiempo_pe_billboard_1').addService(googletag.pubads());            
        }
				
           var interstitialSlot = googletag.defineOutOfPageSlot('/21886670345/eltiempo.pe_Interstitial', googletag.enums.OutOfPageFormat.INTERSTITIAL);
           if (interstitialSlot) interstitialSlot.addService(googletag.pubads());

        googletag.pubads().enableSingleRequest();
        googletag.pubads().disableInitialLoad();
        googletag.pubads().collapseEmptyDivs();
        googletag.enableServices();
        googletag.display(interstitialSlot);
	    window.stpd = window.stpd || {que: []};
         stpd.que.push((function() {
             stpd.initialize();
         }));    
    });
</script>
```

In this example you can see all ad units are defined within specific window width range. This is because we want to show different ad units depending on the screen size.
For example, if the screen size is below 768px, we want to show the mobile ad units, but if the screen size is 768px or above, we want to show the tablet ad units.
Everything above that is for desktop. This sizes may vary depending on Your personal needs.

### 1.4. Our header bidding code

```
<script async src="https://stpd.cloud/saas/5747"></script>
```

This code adds our SSP's for header bidding to work.

## Importing our config

### 2.1 Creating config file

Under components directory, I've created a file called "HeadConfig.js" with the following content:

```
'use client'

import React from 'react';
import Script from 'next/script'

const HeadConfig = () => {

    return(

    <>

    <Script src="https://cdn.jsdelivr.net/npm/in-view@0.6.1/dist/in-view.min.js"
            strategy="beforeInteractive"
    />

    <Script src="https://securepubads.g.doubleclick.net/tag/js/gpt.js"
            strategy="beforeInteractive"
    />

    <Script strategy="beforeInteractive">
        {` 
            inView.offset(-200);
            window.googletag = window.googletag || {cmd: []};
        
            googletag.cmd.push (function () {
                if(window.innerWidth >= 1600) {                                                           
                    googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());                   
                } else if(window.innerWidth >= 1320) { 
                    googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads()); 
                } else if(window.innerWidth >= 1000) {
                    googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads()); 
                } else if(window.innerWidth >= 768) {
                    googletag.defineSlot('/21886670345/eltiempo.pe_728x90_top_tablet', [[728,90],[468,60]], 'eltiempo_pe_top').addService(googletag.pubads());
                } else {
                    googletag.defineSlot('/21886670345/eltiempo.pe_320x100_top_moblie', [[320,100],[320,50],[300,100],[300,50]], 'eltiempo_pe_top').addService(googletag.pubads());
                }
        
                var interstitialSlot = googletag.defineOutOfPageSlot('/21886670345/eltiempo.pe_Interstitial', googletag.enums.OutOfPageFormat.INTERSTITIAL);
                if (interstitialSlot) interstitialSlot.addService(googletag.pubads());
                
                googletag.pubads().set('page_url', 'eltiempo.pe');
                googletag.pubads().enableSingleRequest();
                googletag.pubads().disableInitialLoad();
                googletag.pubads().collapseEmptyDivs();
                googletag.enableServices();
                googletag.display(interstitialSlot);
                window.stpd = window.stpd || {que: []};
                stpd.que.push((function() {
                    stpd.initialize();
                }));
            });            
         `}
    </Script>

    <Script src="https://stpd.cloud/saas/5747"
            strategy="beforeInteractive"
    />

    </>

);
}

export default HeadConfig;

```

This is a shorter version of the code for example reasons.

### 2.2 Importing config file to head section

Since this next.js app is using App Router, in the layout.js file I've imported the config file like this:

```
import { Inter } from 'next/font/google'
import HeadConfig from './components/HeadConfig';
import React from "react";

const inter = Inter({ subsets: ['latin'] })

export const metadata = {
  title: 'Setupad banner test',
  description: 'Setupad banner test',
}

export default function RootLayout({ children }) {
  return (
    <html lang="en">
    <head>
      <HeadConfig />
    </head>
      <body>{children}</body>
    </html>
  )
}

```

As we can see in the code above, we've imported the config file in the head section of the layout.js file. This way, the config file will be loaded before the page content.
If we'd open source of our page, you'd see that inside the head section, this code is present.

## Creating banner components

Now that the config is implemented in the head section, it's time to create banner components.

In this example we'll create only 2 banners, one standart and one lazy-loaded banner using inview.js library.

### 3.1 Standart banner:

First of all, we need to create a simple banner component called "TopPosition.js" under "components" folder. This component will be used to display the banner in the top position of the page.

```
import Script from 'next/script';

const TopPosition = () => {
    return(
        <div id="eltiempo_pe_top">
            <Script>
                {`        
                  googletag.cmd.push(function() {
                    googletag.display('eltiempo_pe_top');
                  });
                `}
            </Script>
        </div>
    );
}

export default TopPosition;
```

Since this banner does not need to be lazy-loaded, because it's always at the top of the page, we only need to create a simple <div> container and add the ad unit id to it.
The ID in the <div> container should match the one defined in the head slot. In this case it's "eltiempo_pe_top".

```
googletag.defineSlot('/21886670345/eltiempo.pe_970x90_top', [[970,90],[728,90],[970,50],[960,90],[950,90]], 'eltiempo_pe_top').addService(googletag.pubads());
```

We can see the ID after the defined sizes ``` 'eltiempo_pe_top' ```, this ID in defineSlot should match the corresponding ID in the <div> container.

### 3.2 Lazy-loaded banner:

Since the banner is lazy-loaded, we don't need to define it at the head section, because in this case, we want the banner to load only when the user scrolls to it.
So here, the defineSlot line will be placed directly in the <div> container. Here's how it looks for a sidebar banner:

```
import Script from 'next/script';

const SidebarRight = () => {
    return (
        <div id="eltiempo_pe_side_rail_right">
            <Script>
                {`
              if(window.innerWidth >= 1600) { 
                  inView('#eltiempo_pe_side_rail_right').on('enter', (function() {        
                    googletag.cmd.push(function() {
                      googletag.defineSlot('/21886670345/eltiempo.pe_300x600_side_rail_right', [[300,600],[160,600],[300,250],[300,300]], 'eltiempo_pe_side_rail_right').addService(googletag.pubads());
                      googletag.display('eltiempo_pe_side_rail_right');
                      stpd.initializeAdUnit('eltiempo_pe_side_rail_right');
                    });
                  }));
              } else if(window.innerWidth >= 1320) {
                    inView('#eltiempo_pe_side_rail_right').on('enter', (function() {        
                        googletag.cmd.push(function() {
                          googletag.defineSlot('/21886670345/eltiempo.pe_160x600_side_rail_right', [[160,600],[120,600]], 'eltiempo_pe_side_rail_right').addService(googletag.pubads());
                          googletag.display('eltiempo_pe_side_rail_right');
                          stpd.initializeAdUnit('eltiempo_pe_side_rail_right');
                        });
                      }));
              }
              `}
            </Script>
        </div>
    );
}

export default SidebarRight;
```

As we can see here, we create a <div> component with matching ID in the defineSlot line. In this case it's "eltiempo_pe_side_rail_right".
Since this is a sidebar banner, we don't want it to show on mobile devices, so we add a condition to check the screen size. If the screen size is 1600px or above, we want to show the 300x600 banner, but if the screen size is 1320px or above, we want to show the 160x600 banner.
Then, the inView function is called to handle the lazy-load of the banner. This function is provided by the inview.js library. It's a simple function that checks if the banner is in the viewport and if it is, it loads the banner.
After that, we call the defineSlot line and immediatly display the adunit with defining the ID of it.

### 3.3 Importing the banner components

Now that we have our banner components created, we need to import them to the page where we want to display them.
It's as simple as importing any other component. I've placed them in a empty page, here's how it looks:

```
import TopPosition from './components/banners/TopPosition';
import SidebarRight from './components/banners/SidebarRight';

export default function Home() {
  return (
      <>
          <TopPosition />
          <SidebarRight />
      </>
  )
}

```

If everything's done correctly, you should see the banners on the page in their corresponding positions.
