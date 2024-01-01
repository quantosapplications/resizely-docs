## How to use it

Suppose we need a resized version of an image, whose url is https://storage.googleapis.com/static.resizely.net/sample/sample_1.jpg

We then can have a resized version of the image in two ways.

### Using key value pairs

With this way we will need to construct a url like this:

https://api.resizely.net/API_KEY/EDITS/URL_OF_THE_IMAGE

where:

- API_KEY is the api key you can retrieve in the Resizely dashboard.
- EDITS are the manipulation you want to apply to image. They are key value pairs separated by colon. eg `w=960:crop=true:out=webb`
- URL_OF_THE_IMAGE is the public url of the image

#### Edits

| Edit   | Param | Type                 | Default value           |
| ------ | ----- | -------------------- | ----------------------- |
| Width  | w     | numeric              | 0                       |
| Height | h     | numeric              | 0                       |
| Crop   | crop  | boolean              | false                   |
| Output | out   | 'jpg', 'png', 'webp' | The same of input image |

> You can pass only the width or only the height to have the image with the specified size and same aspect ratio of the original

> If you wish to apply a "contain" rule you can add `crop=true`. Otherwise a fit rule will be applied.

### Using base64

Or else you can encode a json object in base 64.
This is useful when you work with long urls and you could have final urls longer than 2048 characters.

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
