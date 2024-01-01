**Resizely - Vanilla Javascript example**

```
<!DOCTYPE html>
<html>
<body>

    <img src="https://storage.googleapis.com/static.resizely.net/sample/sample_1.jpg" onload="this.onload=null; this.src=getResizelyImage('https://storage.googleapis.com/static.resizely.net/sample/sample_1.jpg');" />

<script>
    const RESIZELY_API_KEY = 'your resizely api key';
    function getResizelyImage(url, width = null, height = null, crop = null) {
        const requestyBody = {
            key: RESIZELY_API_KEY,
            url: url,
            edits: {
                resize: {
                    width: width,
                    height: height
                },
                crop: crop
            }
        };
        const requestBodyEncoded = btoa(JSON.stringify(requestyBody));
        return `https://api.resizely.net/${requestBodyEncoded}`;
    }
</script>

</body>
</html>
```
