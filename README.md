# AJAX File Uploader

Author: Matt Shaw

https://deliciousbrains.com/using-javascript-file-api-to-avoid-file-upload-limits/

## JavaScript
https://raw.githubusercontent.com/deliciousbrains/wp-dbi-file-uploader/master/dbi-file-uploader.js

## PHP
https://raw.githubusercontent.com/deliciousbrains/wp-dbi-file-uploader/master/dbi-file-uploader.php

# Other Resources
+ https://github.com/gtechsltn/HTML5-Drag-And-Drop
+ https://github.com/gtechsltn/wp-dbi-file-uploader
+ https://github.com/gtechsltn/AJAX-File-Uploader
+ https://github.com/gtechsltn/BlogPosts_WebForms
+ https://github.com/gtechsltn/my-chunk-uploader
+ https://github.com/gtechsltn/UploadLargeFileUsingJavascript

##  HTML
```
<input id="files" type="file" />
```

## JS
```
document.getElementById('files').addEventListener('change', function(e) {

    var file = this.files[0];

    var xhr = new XMLHttpRequest();

    (xhr.upload || xhr).addEventListener('progress', function(e) {
        var done = e.position || e.loaded
        var total = e.totalSize || e.total;
        console.log('xhr progress: ' + Math.round(done/total*100) + '%');
    });

    xhr.addEventListener('load', function(e) {
        console.log('xhr upload complete', e, this.responseText);
    });

    xhr.open('post', '/echo/json/', true);
	
    var data = new FormData;
    data.append('file', file);
    data.append('json', '{"foo":"bar"}'); // for jsFiddle
    xhr.send(data);

});
```
