
#TESTING. STILL NOT WORKING.

# DTGoogleStaticMaps
An Objective-C wrapper around the Google Static Maps API v2. Fully documented.


## Installation with CocoaPods

[CocoaPods](http://cocoapods.org) is a dependency manager for Objective-C, which automates and simplifies the process of using 3rd-party libraries like DTGoogleStaticMaps in your projects. See the ["Getting Started" guide for more information](https://github.com/AFNetworking/AFNetworking/wiki/Getting-Started-with-AFNetworking).

#### Podfile

```ruby
pod "DTGoogleStaticMaps", "~> 0.0"
```

## Quick Example

Here is a simple example of how to download a static map image:

```objective-c
#import <DTGoogleStaticMaps/DTGoogleStaticMaps.h>

...

DTLocation *location = [[DTLocation alloc] initWithAddress:@"Brooklyn Bridge,New York,NY"];
DTStaticMapRequest *request = [[DTStaticMapRequest alloc] initWithApiKey:@"API_KEY"
                                                                  center:location
                                                                    zoom:12
                                                                    size:CGSizeMake(200, 200)];
[DTStaticMapDownloader downloadMapWithRequest:request completion:^(UIImage *mapImage, NSError *error) {
    if (error) {
        //we received an error
    } else if (mapImage) {
        //use image
    }
}];
```

You can use `DTStaticMapDownloader` to download the image, or — use the `endpoint` method in the `DTStaticMapRequest` class to get the request's URL object. You can then download the image with a preferred library. For Example (using [SDWebImage](https://github.com/rs/SDWebImage/)):
```objective-c
[imageView sd_setImageWithURL:[request endpoint]];
```

## Usage

In order to download a static map image we need to create a 
