**Resizely - Angular example**

```
import { Component, Input, OnInit } from '@angular/core';

const RESIZELY_API_KEY = 'your resizely api key';

@Component({
  selector: 'resizely-image[url]',
  template: `<img [src]="resizelyUrl" [alt]="url" />`
})
export class ResizelyImageComponent implements OnInit {

  @Input('url') url: string;
  @Input() width?: number;
  @Input() height?: number;
  @Input() crop?: boolean;

  resizelyUrl: string;

  constructor() { }

  ngOnInit(): void {
    if (!this.url) {
      throw new TypeError("'url' is required");
    }
    const resizelyBody = {
      key: RESIZELY_API_KEY,
      url: this.url,
      edits: {
        resize: {
          width: this.width,
          height: this.height
        },
        crop: this.crop
      }
    };
    const resizelyEncodedBody = btoa(JSON.stringify(resizelyBody));
    this.resizelyUrl = `https://api.resizely.net/${resizelyEncodedBody}`;
  }

}
```
