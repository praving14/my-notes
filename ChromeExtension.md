
# SUMMARY 
 
## Chrome Extensions:

#### Key points:

* ##### Chrome Extensions:
   *  They are just a package bundle of software written in web languages that enhances the chrome browser and the sites viewed on it.
* ##### When? : Anytime you want to do something that
   * Extend the browser's core functionality
   * Enhances the functionality of another websites
* ##### Why? 
   * Trigger push notifications
   * read/write cookings on any sites
   * add your own code into 3rd party sites
   * extend the functionality of browser or specific pages
   * and many more ..
* ##### How?

* ##### Main concepts you need to know first:
    * In addition to your normal HTML, CSS and JavaScript; understanding of HTML DOM APIs and jQuery helps

* ##### Manifest File:
    * Eveny extension has one manifest file <manifest.json> to install and run
    * Basically, a blue print for your extension
    * Your extension name, version, manifest_version you are using, permissions, icons for your extensions, and other informations are found here
    * You can see the list of supported manifest fields [here](https://developer.chrome.com/docs/extensions/mv2/manifest/)
    
* ##### Content Scripts:
    * Content scripts is a javascript file with codes to modify the webpage DOM
    * Works in isolation to the orginal webpage javascript
    * An extenion on webpage can run multiple content scripts that each would run in its own isolated world without conflicts. 
    * Gets executed only when the webpage (*matches) on which the scripts is to be executed loads.
    * You can inject this content script in two ways
         * Programatically: 
         * Declaratively: It basically means to declare your content scripts in the manifest file under the field name "content_scripts"
    * "content_scripts" takes an array of objects with following properties
         * matches: array of regrex strings that specifies the pages URLs when this scripts will be injected
         * js: (Array of strings)  List of js files that should be executed in the matching pages
         * css: (Array of strings) List of CSS files to be injected in the matching pages
         * match_about_blank
         
* ##### Background Scripts:
    * allows extentions to monitor events and then react with specified instruction when triggered
    * dormant until an event they are listening to, react, and then unload
    * registered in manifest file under "background" field
    * Unlike content scripts, it has a single instance for the browser instead of separate instances for each tabs or page
    * we can have multiple background scripts (as in multiple js files) for an extension
        * basically, it has scripts property that takes an array of scripts (js files)
        * "pesistent" is another important key - assign this to false in most cases
    * It gets executed as soon as the browser launches
    
    
 * ##### User Interface of Chrome Extension
    * Extension Popup: most common UI provided by the Chrome Extension 
        * It is bascially a special popup window that appears when you click on the extension
        * In terms of code, it is basically an HTMl file page
        * It can contanin links to stylesheets and scripts tage;
        * Does not allow inline JavaScript
        * The pop up is regietsed in the manifest file under browser_action or page_action field property
            * browser_action: extension can be used most of the time or most pages
            * page_action : extension can only be used on a few domain or URLS
        * The extension button is greyed out if it is not usable in that specific page
     * Other USER interfaces for extension also includes
        * Tooltip : as per the name
        * Omnibox: similar to traditional web browser address bar; can use it like search engine
        * Context menu: Allows us to add a menu option when right clicked 
        * Commands: Allows us to add a keyboard shortcuts that trigger the actions in the extensions
        * Badge: 
        * Override Pages:
        
 * ##### Message Passing
     * One of the most important topic
     * Message Passing is basically a way to communicate between the content script and the extension
     * For example: if you want to manipulate web pages based on some browser events, then you have bachkground scripts listening on browser events but cannot modify the webpage, and content scripts that can modify the page but cannot listen on browser events. Then, you need a way to make them communicate. 
     * A message is simple a valid JSON object
     * two main message passing APIS; but there are others too
        * Simple one time request:
           * send a single message to another part of your extension (and optionally get a response back)
           * runtime.sendMessage or tabs.sendMessage 
           * If multiple pages are listening for onMessage events, only the first to call sendResponse() for a particular event will succeed in sending the response. the other esponse are ignored.
     
        * long-lived connection:
             * lasts longer than a single request and response
             * runtime.connect or tabs.connect to start a connecttion channel 
             * runtime.onConnect to handle incoming connection
             * Port is created when connection channel  is created
             * The shared connection allows the extension to keep shared state linking the several messages coming from the content script
             * each end is given a runtime.Port object => used for sending and receiving messages through that connection.
        * Cross-estension messaging
        * Sending messages from web pages
        * Native messaging
        * You can read all about them [here](https://developer.chrome.com/docs/extensions/mv2/messaging/#simple) 
