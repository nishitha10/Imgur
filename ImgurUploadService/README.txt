*************** 

 Code Work flow :
1. 	The package com.leadiq.imgur.resources has contains the class ImgurProjectResource.java which has all end points.
2. 	The class ImgurProjectResource.java passes control to the package com.leadiq.imgur.handler package to handle and process the request.
3.	The method processUploadImage in UploadImageHandler class calls another method getBase64encodedImage in the same class to encode image in base 64 format.
4. 	The method getBase64encodedImage checks if url starts with "http:", if yes, it uses inputStream and URLConnection to download the image and convert it into Base64 Format. Else , it reads the image file from desktop url and converts it into Base64 format.
4. 	The handler class finally calls the class UploadImageService.java in the package com.leadiq.imgur.webservice to make imgur Rest API calls using the encoded image format as the input.

***************

How to test using Postman:

Note: To upload image we can provide either a desktop url or an http url.

Step 1. Use the POST  method in Postman to post images to imgur
  
  		url: http://localhost:8080/ImgurUploadService/v1/images/upload
    
  		body:
 
			>>>Desktop File (Sample format: /Users/nishitha.reddy/Desktop/IMG_6646.jpg)
			 {
			"urls": [
			"<insert url>"
			]
			}

			>>>> HTTP File (Sample format: https://i2.wp.com/nguyenvanchuong.com/wp-content/uploads/2017/11/Lead-IQ.jpg )
			{
			"urls": [
			"<insert url>"
			]
			}

You will see an output as below:
	Output- Async Response
	
	{
	    "Job Status": "Image Upload processing in background!"
	}


Step 2.  Use the GET  method in Postman to get uploaded image urls.

 		url=http://localhost:8080/ImgurUploadService/v1/images

	Output(Sample Response)- 
			{
	    "uploaded": [
	        "<Link 1>",
	        "<Link 2>",
	        	.
	        	.
	        	.
	        "<Link n>"
	    ]
	}
