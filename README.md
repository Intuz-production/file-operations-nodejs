<h1>Introduction</h1>

This component is used to perform file operations such as file upload, file delete, get file, check file not found and generate thumbnail image.
 
1. You need to create "uploads" folder in your project. Files would be saved or deleted into "uploads" folder.
2. The ratio of thumbnail is minimum. You don't need to worry about the ratio given in function. That function generates thumbnail as its own.

<br/><br/>
<h1>Example Usage</h1>

```

// Upload multiple files
var fileOperations  = require('fileOpearations');

var multerUpload = multer({storage: fileOperations.filesop().file_storage()});
var fields = [{'name':'post_field_name_1'},{'name':'post_field_name_2'}];

router.post('/your-action', multerUpload.fields(fields), function(req, res, next) {
	 console.log(req.files)
});

/*
Output : 
{ 
    post_field_name_1: [ 
    { 
        fieldname: 'post_field_name_1',
        originalname: '5NumberFiveInCircle.png',
        encoding: '7bit',
        mimetype: 'image/png',
        destination: 'uploads/post_field_name_1',
        filename: '950846605296754800.png',
        path: 'uploads/post_field_name_1/950846605296754800.png',
        size: 16394 
    }],
    post_field_name_2: [ 
    { 
        fieldname: 'post_field_name_2',
        originalname: '283px-Marque_number_4_black.svg.png',
        encoding: '7bit',
        mimetype: 'image/png',
        destination: 'uploads/post_field_name_2',
        filename: '78813962318053630.png',
        path: 'uploads/post_field_name_2/78813962318053630.png',
        size: 2261 
    }] 
}
*/

// Generate thumbnail image
var source_image = "/var/www/html/.../foldername/image.jpg",
    destination_path = "/var/www/html/.../foldername/thumb";

fileOperations.filesop().thumbnailc(source_image, destination_path, function(res) {
    console.log(res);
});

// Get file path if exists
fileOperations.filesop().file_not_found_api('folder_name', 'IMG_NAME.png', req.headers.host);

// Delete files
fileOperations.filesop().delete_files([{'name':'IMG_NAME1.png', 'dir':'folder1'}, {'name':'IMG_NAME2.png', 'dir':'folder2'}]);

```
<br/><br/>
<h1>Bugs and Feedback</h1>
For bugs, questions and discussions please use the Github Issues.

<br/><br/>

<h1>Acknowledgments</h1>

<br/>
 <a href="https://www.npmjs.com/package/multer" target="_blank">Multer</a>
 
 <a href="https://www.npmjs.com/package/node-thumbnail" target="_blank">Thumbnail</a>

<br/><br/>
<h1>License</h1>
The MIT License (MIT)
<br/><br/>
Copyright (c) 2018 INTUZ
<br/><br/>
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: 
<br/><br/>
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

<br/>
<h1></h1>
<a href="https://www.intuz.com/" target="_blank"><img src="Screenshots/logo.jpg"></a>
