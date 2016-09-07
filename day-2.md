### **Content for the Workshop - [HERE](https://drive.google.com/drive/u/0/folders/0B9xlQg9XpugsNHhIWHFTbWhQTnM)**
## Day 2


### 09.00 am
### Today is all about
- Promises
- fetch()
- IndexedDB
- Service Workers: caching, live data

**Working with Promises**
- Why Promises?
    - Asynchronicity
    - Readability

### Promise Lab   
- cd into the promise-lab and then run
```
 python -m SimpleHTTPServer 8000
```
- or use Web Server for Chrome extension  
- Go to promise-lab README.md
- Open progressive-web-app-ilt-codelabs.pdf and follow along **1.5**
- Please use incognito from the beginning

**problem/solutions**
- `exercise02.js` line 61 needs to have a `return` in front of `getCountryInfo()` otherwise the function will return undefined.

### Fetch API
- modern replacement for XMLHTTPRequest
- works well with PWA
- Promise based
- can be used with service workers
- Supports Cross Origins Resource Sharing (CORS) OHH YEAHH!!!!

### Impromptu Talk - Performance Talk
**TIPS/HINTS**  
WebpageTest
addy osmani critical
https://csstriggers.com
https://github.com/GoogleChrome/flipjs
chrome://inspect/#devices - very useful port forwarding
**TIPS/HINTS**

### Fetch API Lab   
- cd into the fetch-api-lab and then run
```
 python -m SimpleHTTPServer 8000
```
- or use Web Server for Chrome extension  
- Go to fetch-api-lab README.md
- Open progressive-web-app-ilt-codelabs.pdf and follow along **1.6**
- Please use incognito from the beginning

**problem/solutions**
- **7 Head Request** add `console.log(response.headers.get('Content-Type'));` to `readResponseAsText` function to be able to view specifics within the header.
    - The reason `response.headers` does not return anything is because we are running on localhost and not sending any headers on here. duh..;.
