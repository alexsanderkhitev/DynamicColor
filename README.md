<p align="center">
  <img src="http://yannickloriot.com/resources/dynamiccolor-header.png">
</p>

<p align="center">
  <a href="https://cocoapod-badges.herokuapp.com/l/DynamicColor/badge.svg"><img alt="License" src="https://cocoapod-badges.herokuapp.com/l/DynamicColor/badge.svg"/></a>
  <a href="http://cocoadocs.org/docsets/DynamicColor/"><img alt="Supported Plateforms" src="https://cocoapod-badges.herokuapp.com/p/DynamicColor/badge.svg"/></a>
  <a href="http://cocoadocs.org/docsets/DynamicColor/"><img alt="Version" src="https://cocoapod-badges.herokuapp.com/v/DynamicColor/badge.svg"/></a>
  <a href="https://github.com/Carthage/Carthage"><img alt="Carthage compatible" src="https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat"/></a>
  <a href="https://travis-ci.org/yannickl/DynamicColor"><img alt="Build status" src="https://travis-ci.org/yannickl/DynamicColor.svg?branch=master"/></a>
  <a href="http://codecov.io/github/yannickl/DynamicColor"><img alt="Code coverage status" src="http://codecov.io/github/yannickl/DynamicColor/coverage.svg?branch=master"/></a>
</p>

**DynamicColor** provides powerful methods to manipulate colours in an easy way in Swift (iOS/macOS/WatchOS/tvOS).

<p align="center">
    <a href="#usage">Usage</a> • <a href="#installation">Installation</a> • <a href="#contact">Contact</a> • <a href="#license-mit">License</a>
</p>

<p align="center">
  <img src="http://yannickloriot.com/resources/dynamiccolor-sample-screenshot.png" alt="example screenshot" width="300" />
</p>

*This branch is Swift 3 compatible, use the [v2 version](https://github.com/yannickl/DynamicColor/tree/2.4.0) for Swift 2.*

## Usage

#### Creation (Hex String)

Firstly, DynamicColor provides useful initializers to create colors using hex strings or values:

```swift
let color = UIColor(hexString: "#3498db")
// equivalent to
// color = UIColor(hex: 0x3498db)
```

To be platform independent, the typealias `DynamicColor` can also be used:

```swift
let color = DynamicColor(hex: 0x3498db)
// On iOS, WatchOS or tvOS, equivalent to
// color = UIColor(hex: 0x3498db)
// On OSX, equivalent to
// color = NSColor(hex: 0x3498db)
```

#### Darken & Lighten

These two create a new color by adjusting the lightness of the receiver. You have to use a value between 0 and 1.

<p align="center">
  <img src="http://yannickloriot.com/resources/dynamiccolor-darkenlighten.png" alt="lighten and darken color" width="280"/>
</p>

```swift
let originalColor = DynamicColor(hexString: "#c0392b")

let lighterColor = originalColor.lighter()
// equivalent to
// lighterColor = originalColor.lighter(amount: 0.2)

let darkerColor = originalColor.darkened()
// equivalent to
// darkerColor = originalColor.darkened(amount: 0.2)
```

#### Saturate, Desaturate & Grayscale

These will adjust the saturation of the color object, much like `darkened` and `lighter` adjusted the lightness. Again, you need to use a value between 0 and 1.

<p align="center">
  <img src="http://yannickloriot.com/resources/dynamiccolor-saturateddesaturatedgrayscale.png" alt="saturate, desaturate and grayscale color" width="373"/>
</p>

```swift
let originalColor = DynamicColor(hexString: "#c0392b")

let saturatedColor = originalColor.saturated()
// equivalent to
// saturatedColor = originalColor.saturated(amount: 0.2)

let desaturatedColor = originalColor.desaturated()
// equivalent to
// desaturatedColor = originalColor.desaturated(amount: 0.2)

let grayscaledColor = originalColor.grayscaled()
```

#### Adjust-hue & Complement

These adjust the hue value of the color in the same way like the others do. Again, it takes a value between 0 and 1 to update the value.

<p align="center">
  <img src="http://yannickloriot.com/resources/dynamiccolor-adjustedhuecomplement.png" alt="ajusted-hue and complement color" width="280"/>
</p>

```swift
let originalColor = DynamicColor(hexString: "#c0392b")

// Hue values are in degrees
let adjustHueColor = originalColor.adjustedHue(amount: 45)

let complementedColor = originalColor.complemented()
````

#### Tint & Shade

A tint is the mixture of a color with white and a shade is the mixture of a color with black. Again, it takes a value between 0 and 1 to update the value.

<p align="center">
<img src="http://yannickloriot.com/resources/dynamiccolor-tintshadecolor.png" alt="tint and shade color" width="280"/>
</p>

```swift
let originalColor = DynamicColor(hexString: "#c0392b")

let tintedColor = originalColor.tinted()
// equivalent to
// tintedColor = originalColor.tinted(amount: 0.2)

let shadedColor = originalColor.shaded()
// equivalent to
// shadedColor = originalColor.shaded(amount: 0.2)
```

#### Invert

This can invert the color object. The red, green, and blue values are inverted, while the opacity is left alone.

<p align="center">
  <img src="http://yannickloriot.com/resources/dynamiccolor-invert.png" alt="invert color" width="187"/>
</p>

```swift
let originalColor = DynamicColor(hexString: "#c0392b")

let invertedColor = originalColor.inverted()
```

#### Mix

This can mix a given color with the receiver. It takes the average of each of the RGB components, optionally weighted by the given percentage (value between 0 and 1).

<p align="center">
<img src="http://yannickloriot.com/resources/dynamiccolor-mixcolor.png" alt="mix color" width="373"/>
</p>

```swift
let originalColor = DynamicColor(hexString: "#c0392b")

let mixedColor = originalColor.mixed(color: .blueColor())
// equivalent to
// mixedColor = originalColor.mixed(color: .blueColor(), weight: 0.5)
```

#### And many more...

`DynamicColor` also provides many another useful methods to manipulate the colors like hex strings, color components, etc. To go further, take a look at the example project.

## Installation

#### CocoaPods

Install CocoaPods if not already available:

``` bash
$ [sudo] gem install cocoapods
$ pod setup
```
Go to the directory of your Xcode project, and Create and Edit your *Podfile* and add _DynamicColor_:

``` bash
$ cd /path/to/MyProject
$ touch Podfile
$ edit Podfile
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'

use_frameworks!
pod 'DynamicColor', '~> 3.0.0'
```

Install into your project:

``` bash
$ pod install
```

Open your project in Xcode from the .xcworkspace file (not the usual project file):

``` bash
$ open MyProject.xcworkspace
```

You can now `import DynamicColor` framework into your files.

#### Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that automates the process of adding frameworks to your Cocoa application.

You can install Carthage with [Homebrew](http://brew.sh/) using the following command:

```bash
$ brew update
$ brew install carthage
```

To integrate `DynamicColor` into your Xcode project using Carthage, specify it in your `Cartfile` file:

```ogdl
github "yannickl/DynamicColor" >= 3.0.0
```

#### Swift Package Manager
You can use [The Swift Package Manager](https://swift.org/package-manager) to install `DynamicColor` by adding the proper description to your `Package.swift` file:
```swift
import PackageDescription

let package = Package(
    name: "YOUR_PROJECT_NAME",
    targets: [],
    dependencies: [
        .Package(url: "https://github.com/yannickl/DynamicColor.git", versions: "3.0.0" ..< Version.max)
    ]
)
```

Note that the [Swift Package Manager](https://swift.org/package-manager) is still in early design and development, for more infomation checkout its [GitHub Page](https://github.com/apple/swift-package-manager)

#### Manually

[Download](https://github.com/YannickL/DynamicColor/archive/master.zip) the project and copy the `DynamicColor` folder into your project to use it in.

## Contact

Yannick Loriot
 - [https://twitter.com/yannickloriot](https://twitter.com/yannickloriot)
 - [contact@yannickloriot.com](mailto:contact@yannickloriot.com)


## License (MIT)

Copyright (c) 2015-present - Yannick Loriot

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
