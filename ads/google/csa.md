<!---
Copyright 2015 The AMP HTML Authors. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->
# Custom Search Ads

## AdSense For Search (AFS)

To request AdSense for Search ads on the Custom Search Ads protocol, use the
**data-afs-page-options** and **data-afs-adblock-options** attributes in the
amp-ad tag. The values you pass should be set to a stringified version of the
Javascript object you would pass in the ad request of a standard CSA request.

```html
<amp-ad width=auto height=300
    type='csa'
    layout='fixed-height'
    data-afs-page-options='{"pubId": "partner-pub-id", "query": "flowers"}'
    data-afs-adblock-options='{"width": "auto", "number": 2}'>
</amp-ad>
```

Please see documentation for [AdSense for Search](https://developers.google.com/custom-search-ads/docs/implementation-guide)
for more information.

## AdSense For Shopping (AFSh)

To request AdSense for Shopping ads on the Custom Search Ads protocol, use the
**data-afsh-page-options** and **data-afsh-adblock-options** attributes in the
amp-ad tag.  The values you pass should be set to a stringified version of the
Javascript object you would pass in the ad request of a standard CSA request.

```html
<amp-ad width=auto height=300
    type='csa'
    layout='fixed-height'
    data-afsh-page-options='{"pubId": "partner-vert-pla-pubid-pdp",
    "query": "flowers"}'
    data-afsh-adblock-options='{"width": "auto", "height": 300}'>
</amp-ad>
```

To request an AFSh ad with a width equal to the screen width, use "auto" for
the CSA width parameter. Please note that "auto" width is not supported in
non-AMP implementations.

Please see documentation for [AdSense for Shopping](https://developers.google.com/adsense-for-shopping/docs/implementation-guide)
for more information.

### AFSh with AFS Backfill

To request AFS ads when AFSh does not return any ads, include both the
**data-afs-*** and **data-afsh-*** attributes in the amp-ad tag.  If AFSh does
not return ads, AMP will request AFS ads with the values from the **data-afs-***
attributes.

```html
<amp-ad width=auto height=400
    type='csa'
    layout='fixed-height'
    data-afsh-page-options='{"pubId": "partner-vert-pla-pubid-pdp",
    "query": "flowers"}'
    data-afsh-adblock-options='{"width": "auto", "height": 400}'
    data-afs-page-options='{"pubId": "partner-pub-id", "query": "flowers",
    "channel": "backfill"}'
    data-afs-adblock-options='{"width": "auto"}'>
</amp-ad>
```

## Requirements

- Each amp-ad tag contains one adblock.  Only one **data-afs-adblock-options**
and/or one **data-afsh-adblock-options** attribute can be specified in the tag.
- Above the fold ads are required to have a minimum height of 300 pixels.