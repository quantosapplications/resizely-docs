
## How to use it

Suppose we need a resized version of an image, whose url is https://storage.googleapis.com/static.resizely.io/sample/sample_1.jpg

We then can have a resized version of the image in two ways.

### Using fit-in / crop-in

With this way we will need to construct a url like this:

https://api.resizely.io/API_KEY/fit-in/960x320/URL_OF_THE_IMAGE

where:
- API_KEY is the api key you can retrieve in the Resizely dashboard.
- fit-in/WIDTHxHEIGHT is the final size of the image you want.
- URL_OF_THE_IMAGE is the public url of the image

> You can call /fit-in/WIDTHx0 (zero) to have the image with the specified width and same aspect ratio of the original

### Using base64

Or else you can encode a json object in base 64

```
{
	"key": API_KEY,
	"url": URL_OF_THE_IMAGE,
	"edits": {
		"resize": {
			"width": WIDTH,
			"height": HEIGHT,
		},
		"crop": true
	}
}
```

where:
- API_KEY is the api key you can retrieve in the Resizely dashboard.
- URL_OF_THE_IMAGE is the public url of the image
- WIDTH and HEIGHT are the final sizes of the image you need
- CROP if you wish to apply a "contain" rule, or false if you wish to apply a "cover" rule

> You can pass only the width or only the height to have the image with the specified size and same aspect ratio of the original