# Progressive-Web-App-Workshop
### 3 Day Workshop run at CodeNode. We'll be hoping to note down everything they teach us. All the materials will be made available to the public. (open sourced)

**If you are unable to make it, but have any Questions put them on the `questtions.md` and i'll try to get them answered**


###### Sarah Clark: Program Manager @Google
- sarahclark@google.com had a chat with her and she makes it to london quite often and is willing to do a talk about PWA or even a day workshop depending on her timing. YAY!!!!  

###### Sam Dutton: Developer Advocate @Google  
- dutton@google.com

###### Halima Koundi
- Twitter handle @hkoundi, she is an apprentice at a consultancy, would love to do a talk about code craftmanship and her apprenticeship.

### **Content for the Workshop - [HERE](https://drive.google.com/drive/u/0/folders/0B9xlQg9XpugsNHhIWHFTbWhQTnM)**
## Day 1
### 11.00 am


**What do you want to work on after the workshop?**
- LBGT Hack
- Future Projects
- Convincing Clients about why PWA  

**What do you want to learn during the workshop?**
- Offline
- Accessibility


### Why Build Progressive Web Apps.
- Capability vs Reach (greater reach than Capability at the moment, but capability is improving without letting go of the reach)
    - The Washington Post PWA is a great example
- PWA removes friction

### What was missing on the web?
- Reliable Performance - Service Workers ( caching, offline and improve performance )
    - amp-install-serviceworker
    - [lighthouse (tool for helping you build PWA)](github.com/googlechrome/lighthouse)
- Push Notifications
- Homescreen icon metadata
- Web Payment API (coming soon)
- Credential API (coming soon)

### Why is this important?
- Reach
    - 1 Billion Chrome Users
    - More monthly unique visitors on Web, but less engagement compared to native apps at the moment
- Acquisition
    - user Acquisition cost is lower £0.20p vs £3.00 for native
- Conversion
    - AliExpress - 2x more page views, 74% increase in time spent on pages etc.

### How do we get started?
- Start from the ground up
    - Konga.com is a great example. another one...
- Build a simple version
    - [AirBerlin](Airberlin.com) (loadtime is < 1s)
    - [Washington Post](https://www.washingtonpost.com/) (loadtime is <80ms)
- Focus on a single feature at a time
    - Weather Channel brought in push notifications
    - [Booking.com](booking.com)
    - **they are just showing off all the apps built using PWA now...**

### Where to Start?
- Understand your users
    - Who?
    - What Platforms?
    - What kind of connectivity?
    - How data cost affects users? (mainly for emerging market or roaming market)?
        - Data budgets, data size and data cost (again for emerging markets)
    - target/current audience?
    - Browsers/OS/Harware?  
- Connectivity
    - Cell, Wifi, Broadband?
    - unreliable, low-bandwidth, capped..?
    - offline?  
- Context is everything
- Understanding requirements
    - Performance
    - Content
    - Functionality

### Exercise time  
**For your App idea**
- Who are your users?
- What are your platforms?
- What connectivities will your users have?
- What data costs will your users have to worry about?
- Speeds?
    - Most people will abandon the page if it doesn't load within 3 seconds.
    - if it takes more than 1 second to do something, it breaks the users train of thoughts
    - under 100ms - our brain reads it as instantaneous

**Content Design**
- How to write for the Web
- How people read
- Text, images and media for the Web
- prioritise Content
- Think app!

**Data Desgign**
- Reduce data costs
- Reducer resource request
- why do these matter?
- What can I do about it?
- Text, images and media

**Code Design**
- Structure is a must
- Use HTML - then CSS and then Javascript only if required.
- HTML Structure
- Validation of you code at every step

**Responsive Design**
- Responsiveness is a core feature of the web!
- Think about layout, responsive content, delivering images in different sizes
- UI/UX for buttons and contents
- Design for infinite viewports

**TIPS/HINTS**  
Surma - HTTP2 UDACITY COURSE Client server communication  
**TIPS/HINTS**

### 11.00 am

**Responsive Design**
- quick tour on reponsive design.
- Do as little as possible
- Treat layout as an enhancement  

**Size Matters :wink:**
- GOLDEN RULE: Never make users scroll horizontally. (everyone at FAC should already know this...)
- Use
```html
<meta name="viewport"  content="width=device-width, initial-scale=1">
```
 (everyone at FAC should already know this too...)
- Use
```css
 img {
     max-width: 100%
 }
 img.foo {
     width: 300px;
 }
```
- use media queries  (everyone at FAC should already know this three...)
    - although not great to have multiple queries for each individual device as samsung might have a phone with a width of 600px, but then HTC might have one for 609px.
    - use grid system.
    - Start small (Mobile First - seriously we do this at FAC too :heart:)
        - add major breakpoint
        - optimise for reading: 70-80 characters per line
        - this can be done in Javascript
        - don't forget your old friend `calc();`
        - avoid images if you can. use CSS, SVG and if you do decide to use images then go for lowest possible resolutions for the images and correct image types (PNG, JPEG)
    - these elements have good adoption rate
        ```html
        <picture>
            <source src="..." srcset="...">
        </picture>
        <source>
        </source>
        .......................................
            <src="wallaby">
            <srcset="wallaby_1x 1x, wallaby_2x 2x">
            <srcset="small.jpg 500w, medium 1000w">
        ```
        - `srcset` auto selects the image depending on the display density, and falls back to source on browser that don't support `srcset`
        - `w` tells the browser the image width, so if your browser window is 500px wide on a 2x display it will show the 1000w image. Great way to optimise data cost and reduce the number of data request.
        - All of this can be achieved in the picture element, and browsers that don't support picture, it will fallback to image element.
            - you can achieve a lot with just these elements in terms of responsiveness
            - you don't have to manually input these, use build tools for creating the different sized images  
        - Flexbox getting the :heart:
        - CSS grid (THE NEXT BIG THING not supported at all on canweuse though :cry:)
- Think of your content as a stream of stuff, and then manipulate the content for the needs of the layout


**TIPS/HINTS**  
 modern way to do responsive videos - Dash  
**TIPS/HINTS**

### 13.00 pm

### Introduction to Service Workers.

**What is a Service Worker?**
- Client side proxy server written in Javascript
- required **https**
- Application makes a request, it then goes through the service worker, which then takes it to the server. (or if offline then fetches data from offline cache)
- it can respond to Push events, alongside background syncing
- Service Worker Lifecycle **>>> FIND AN IMAGE TO PUT BELOW. <<<<<**
    - Install (event in SW)
    - Activate (event in SW)
- Registration of a service worker
```js
if(!service worker) {
    continue
} else {    
    serviceworker.register(/service-worker.js)
    .then(() => {
        do some service work
    })
    .catch((error) =>{
        whoops! it broke....
    })
}
```

**TIPS/HINTS**  
Dev Tools Application section.
Setup a local webserver - Web Server for Chrome
Lets Encrypt - for free HTTPS certificate
**TIPS/HINTS**


### Service Worker Lab  

- cd into the service-worker-lab and then run
```
 python -m SimpleHTTPServer 8000
```
- or use Web Server for Chrome extension  
- Go to Servicer-Worker-lab README.md
- Open progressive-web-app-ilt-codelabs.pdf and follow along **1.2**
- Please use incognito from the beginning

**Problem/Solution**
- **1.2** Section 4
    - it should show 3 console logs (activate, register and install)
    - but if you are only seeing 2.
    - Go to Application in Dev tools
    - Server Workers
    - unregister the app.
    - Refresh and you should see 3 console logs!! :tada:

### 14:30 pm
### Instant loading with service workers and app shell  

**Architecture of the app**
- App shell should be cached.
    - app navigation bar
- Server Side Rendering (SSR)
- Client Side Rendering (CSR)
    - huge time gap with this.

**Recommended pattern for PWA**
- Application shell (SSR both shell + content for entry page). Use JavaScript to fetch content for any further routes and do a "take over"
- Appilcation shell (SSR) + use JavaScript to fetch content once the app shell is loaded
- SSR
- CSR ( full page caching, potential for JSON Payload bootstraping via server)

**How to Build an app shell**
- Move to https
- cache static only

**Use a web app manifest file**
- manifest.json

**Push Notification**


### 15.20 pm

**Test against requirements**
- Device emulation: Chrome DevTools ...
    - Throtling tool
- Network emulation: WebpageTest, Link Conditioner...
- Setup a Device Lab
    - Google Mini Mobile Device Lab: Test on any Device
    - OpenSTF: simple app to test websites on Android devices
    - Look into impaired Network

- Validation Tools: eslint
- Lighthouse
- PageSpeed Insights
- Webpage Test

**Lighthouse - Test your PWA**
- Testing Web Apps, with PWA in mind
- Run it in Chrome extension or CLI
- [Link](https://github.com/GoogleChrome/lighthouse)

### Lighthouse Lab   
- cd into the lighthouse-lab and then run
```
 python -m SimpleHTTPServer 8000
```
- or use Web Server for Chrome extension  
- Go to lighthouse-lab README.md
- Open progressive-web-app-ilt-codelabs.pdf and follow along **1.3**
- Please use incognito from the beginning

**Offline Support**
### Offline Quickstart Lab   
- cd into the offline-quickstart-lab and then run
```
 python -m SimpleHTTPServer 8000
```
- or use Web Server for Chrome extension  
- Go to offline-quickstart-lab README.md
- Open progressive-web-app-ilt-codelabs.pdf and follow along **1.4**
- Please use incognito from the beginning

**Problem/Solution**
- **1.4**
    - the install service worker helper needs to look like this:
    ```js
    self.addEventListener('install', function(event) {
      event.waitUntil(
          caches.open('static-cache-v1')
            .then(function(cache) {
              return cache.addAll([
                '/',
                'index.html',
                'js/main.js',
                'css/main.css'
              ]);
            })
        );
    });
    ```
    - missing `'/'`

**TIPS/HINTS**  
Network Link Conditioner in system preferences MacOS  
**TIPS/HINTS**
