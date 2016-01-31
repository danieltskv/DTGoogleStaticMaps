
#In Development.


# DTGoogleStaticMaps
An Objective-C wrapper around the [Google Static Maps API v2](https://developers.google.com/maps/documentation/static-maps/). Fully documented.

## Getting Started

### Installation with CocoaPods

[CocoaPods](http://cocoapods.org) is a dependency manager for Swift and Objective-C Cocoa projects, which automates and simplifies the process of using 3rd-party libraries like DTGoogleStaticMaps in your projects.

Add the following to your Podfile:

```ruby
pod 'DTGoogleStaticMaps', '~> 0.0'
```

### Quick Example

Here is a simple example of how to download a static map image:

#### Import
```objective-c
#import <DTGoogleStaticMaps/DTGoogleStaticMaps.h>
```

#### Download
```objective-c
DTLocation *location = [[DTLocation alloc] initWithAddress:@"Brooklyn Bridge,New York,NY"];
DTStaticMapRequest *request = [[DTStaticMapRequest alloc] initWithApiKey:@"API_KEY" center:location zoom:12 size:CGSizeMake(200, 200)];
[DTStaticMapDownloader downloadMapWithRequest:request completion:^(UIImage *mapImage, NSError *error) {
    if (error) {
        //we received an error
    } else if (mapImage) {
        //use image
    }
}];
```

You can use `DTStaticMapDownloader` to download the image, or — use the `url` method in the `DTStaticMapRequest` class to get the request's URL object. You can then download the image with a preferred library. For Example, using [SDWebImage](https://github.com/rs/SDWebImage/):
```objective-c
[imageView sd_setImageWithURL:[request URL]];
```

## License
DTGoogleStaticMaps is released under the MIT license. See LICENSE for details.
