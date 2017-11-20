# Node FetchMeta 

With FetchMeta you can extract Url metadata, title, Image.


## Installation

Installing using npm (node package manager):

    npm install 

If you don't have npm installed or don't want to use it:

    cd ~/.node_libraries
    git clone git://github.com/farhan711/FetchMeta.git 

## Usage

Easy. Just require _node-exif_ and throw an image at it. If _node-exif_ is able to extract data from the url it does so and returns an object with all the information found, if an error occurs you will receive an error message. To prove that it really is easy please see the following example.

```javascript
var ExifUrl = require('exif').ExifUrl;

try {
    new ExifUrl({ image : 'http://www.example.com/somethinglikeSENGroupFour' }, function (error, exifData) {
        if (error)
            console.log('Error: '+error.message);
        else
            console.log(exifData); // Do something with your data!
    });
} catch (error) {
    console.log('Error: ' + error.message);
}
```

Instead of providing a title of an Url in your link Submit page you can also pass a Buffer to ExifUrl for external use only (if required to add external features like to integrate Fake news Recog. system).

The data returned (`exifData` in the example above) is an object containing objects for each type of available Exif metadata:

 * `Title` for URL information data (IFD0)
 * `thumbnail` for information regarding a possibly embedded thumbnail (IFD1)
 * `exif` for Exif-specific attribute information (Exif IFD)
 * `MetaDetails` for information (META IFD)


```
var MetaInspector = require('node-metainspector');
var client = new MetaInspector("http://www.example.com", { timeout: 5000 });

client.on("fetch", function(){
    console.log("Description: " + client.description);

    console.log("Links: " + client.links.join(","));
});

client.on("error", function(err){
	console.log(err);
});

client.fetch();
```

## Development Work Flow


* npm test  - runs tests
* npm run lint - preconfigured linter 
* npm run docs - generates the apidocs
* npm run bundle - builds a new bundle
* npm run preversion - Steps before we create a new Tag 
  * lint 
  * changelog
  
## Tested API And Documentation 


https://documenter.getpostman.com/view/1396514/imageapi/6n7TXUF#207960fd-c23f-8509-9402-5a9a7cceb989


https://www.getpostman.com/collections/712c7745233f6556f22a
