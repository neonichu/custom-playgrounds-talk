# 💥 Custom Playgrounds 🎯

## NSLondon, June 2014

### Boris Bügling - @NeoNacho

![](images/playground.jpg)

![20%, original, inline](images/contentful.png)

---

![](images/yo.jpg)

---

### CocoaPods

### -

### Contentful

![](images/contentfulpods.png)

---

# Swift?

![](images/taylor-swift.jpg)

---

# Swift!

![](images/swift-slide.png)

---

# REPL

![](images/swift-bg.jpg)

---

    $ swift
    Welcome to Swift!  Type :help for assistance.
      1> import ContentfulDeliveryAPI
    <REPL>:1:8: error: no such module 'ContentfulDeliveryAPI'
    import ContentfulDeliveryAPI
           ^

![](images/swift-bg.jpg)

---

Copy your framework over to **/Applications/Xcode6-Beta2.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.10.sdk/System/Library/Frameworks**

![](images/copied-framework.png)

---

    1> import ContentfulDeliveryAPI
    2> var client = CDAClient()
    client: CDAClient = <extracting data from value failed>

    error: Couldn't lookup symbols:
      _OBJC_CLASS_$_CDAClient

![](images/swift-bg.jpg)

---

### Load the dynamic library from your framework using `dlopen()`

![](images/swift-bg.jpg)

---

    3> var handle = dlopen("/Applications/.../Versions/A/ContentfulDeliveryAPI", 2)
    handle: COpaquePointer = Builtin.RawPointer = 
    0x0000000102e2b6e0 -> 0x00007fff5fc37e50 
    vtable for ImageLoaderMachOCompressed + 16
    4> var client = CDAClient()
    client: CDAClient = {}

![](images/swift-bg.jpg)

---

# Success

![](images/gloves-cheer2.gif)

---

    // Playground - noun: a place where people can play

![](images/playgrounds-slide.jpg)

---

![](images/contentful-js-docs.png)

---

![original, 180%](images/import-afnetworking.png)

---

    24/06/14 01:00:00,780 Xcode[84816]: 
    IDEPlaygroundExecutionSessionThread(pid=85188) 
    IDEPlaygroundExecution: [PlaygroundSession <0x7fff12750c70>] 
    Received error from expr: error: error: Couldn't lookup symbols:
     _OBJC_CLASS_$_CDAClient

---

![original, 300%](images/no-idea.jpg)

---

# Sam Marshall

![](images/sam-twitter.png)

---

![](images/sam-blog.png)

---

# Xcode plugin?

![100%](images/Xcode.png)

---

![](images/playgrounds-headers.png)

---

    #import <IDELanguageSupportUI/IDEPlaygroundExecutionDeviceService.h>

    @interface IDELocalComputerPlaygroundExecutionDeviceService : 
    IDEPlaygroundExecutionDeviceService

    + (id)capability;
    - (id)sessionForExecutingPlaygroundWithParameters:(id)arg1;
    - (id)defaultStubPathForSDK:(id)arg1;

    @end

![](images/swift-bg.jpg)

---

# DVTPlaygroundCommunication.framework

	@interface DVTPlaygroundCommunicationListener

	@interface DVTPlaygroundCommunicationSender

Uses TCP/IP on the local machine to communicate between Xcode and Stub

![](images/swift-bg.jpg)

---

![](images/wat.jpg)

---

![](images/cloud-playgrounds.jpg)

---

![](images/playground-crash.png)

---

![](images/contentful-playground-fail.png)

---

![](images/contentful-playground.png)

---

# Demo

![](images/swift-bg.jpg)

---

![original, 100%](images/playground-builder.png)

---

# Xcode plugin!

![100%](images/Xcode.png)

---

# Relevant WWDC 2014 sessions

- Session 408: Swift Playgrounds
- Session 409: Introduction to LLDB and the Swift REPL

![](images/swift-bg.jpg)

---

# Links

- <http://samdmarshall.com/blog/custom_frameworks_and_swift.html>
- <https://github.com/jas/swift-playground-builder>
- <http://stackoverflow.com/questions/24058336/how-do-i-run-asynchronous-callbacks-in-playground>

![](images/swift-bg.jpg)

---

# Thank you!

![](images/yes-yes.gif)

---

### <http://vu0.org/playgrounds>

![](images/swift-bg.jpg)
