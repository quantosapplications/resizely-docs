**Resizely - Flutter example**

```
import  'dart:convert';
import  'package:flutter/material.dart';

const  RESIZELY_KEY = 'your resizely api key';

/// Helper class to create a Resizely url
class  ResizelyImageUrl {

	final  String apikey;
	final  String url;
	final  int? width;
	final  int? height;
	final  bool? crop;

	const  ResizelyImageUrl({required  this.apikey, required  this.url, this.width = 0, this.height = 0, this.crop });

	Map<String, dynamic> _toJson() => {
		'url': url,
		'key': apikey,
		'edits': {
			'resize': {
				'width': width,
				'height': height
			},
			'crop': crop ?? width == height // we suggest to crop square images :)
		}
	};

	String  _toBase64() => base64.encode(utf8.encode( jsonEncode(_toJson()) ));

	String  toUrl() => 'https://api.resizely.net/${_toBase64()}';
}

/// Widget that display the image
class  ResizelyImage  extends  StatelessWidget {

	final  String url;
	final  int? width;
	final  int? height;

	const  ResizelyImage({ required  this.url, this.width, this.height, Key? key}) : super(key: key);

	@override
	Widget  build(BuildContext context) {
		// We suggest to use [CachedNetworkImage] from cached_network_image package instead of Image.network to cache also on client side
		return  Image.network(
			ResizelyImageUrl(
				apikey: RESIZELY_KEY,
				url: url,
				width: width,
				height: height
			).toUrl()
		);
	}
}
```
