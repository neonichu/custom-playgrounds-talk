# 💥 Custom Playgrounds 🎯

## swift.berlin #2, July 2014

### Boris Bügling - @NeoNacho

![](images/playground.jpg)

![20%, original, inline](images/contentful.png)

---

![](images/yo.jpg)

---

### CocoaPods

### -

### Contentful

![](images/contentfulpods-2.0.png)

---

# Swift

![](images/taylor-swift.jpg)

---

# REPL

![](images/swift-bg-2.0.jpg)

---

    $ swift
    Welcome to Swift!  Type :help for assistance.
      1> import ContentfulDeliveryAPI
    <REPL>:1:8: error: no such module 'ContentfulDeliveryAPI'
    import ContentfulDeliveryAPI
           ^

![](images/swift-bg-2.0.jpg)

---

Copy your framework over to **/Applications/Xcode6-Beta2.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.10.sdk/System/Library/Frameworks**

![](images/copied-framework.png)

---

    1> import ContentfulDeliveryAPI
    2> var client = CDAClient()
    client: CDAClient = <extracting data from value failed>

    error: Couldn't lookup symbols:
      _OBJC_CLASS_$_CDAClient

![](images/swift-bg-2.0.jpg)

---

### Load the dynamic library from your framework using `dlopen()`

![](images/swift-bg-2.0.jpg)

---

    3> var handle = dlopen("/Applications/.../Versions/A/ContentfulDeliveryAPI", 2)
    handle: COpaquePointer = Builtin.RawPointer = 
    0x0000000102e2b6e0 -> 0x00007fff5fc37e50 
    vtable for ImageLoaderMachOCompressed + 16
    4> var client = CDAClient()
    client: CDAClient = {}

![](images/swift-bg-2.0.jpg)

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

# DVTPlaygroundCommunication.framework

    @interface DVTPlaygroundCommunicationListener {
        NSString *_socketPath;
    }

    @interface DVTPlaygroundCommunicationSender

- Uses TCP/IP on the local machine to communicate between Stub and Xcode
- But apparently uses Unix domain sockets for the other direction (?)

![](images/swift-bg-2.0.jpg)

---

# ¯\\\_(ツ)\_/¯ 

![](images/swift-bg-2.0.jpg)

---

![](images/cloud-playgrounds.jpg)

---

![](images/playground-crash.png)

---

# ➡️ Xcode plugin

![100%](images/Xcode.png)

---

### libPlaygroundInjector.dylib

![](images/swift-bg-2.0.jpg)

---

    #import <IDELanguageSupportUI/IDEPlaygroundExecutionDeviceService.h>

    @interface IDELocalComputerPlaygroundExecutionDeviceService : 
    IDEPlaygroundExecutionDeviceService

    + (id)capability;
    - (id)sessionForExecutingPlaygroundWithParameters:(id)arg1;
    - (id)defaultStubPathForSDK:(id)arg1;

    @end

![](images/swift-bg-2.0.jpg)

---

## DYLD\_INSERT\_LIBRARIES

![](images/swift-bg-2.0.jpg)

---

    @interface IDEPlaygroundExecutionSession : NSOperation

    [...]

    - (void)cleanupExecutable;
    - (void)destroyDebugger;
    - (void)_stopListeningForPlaygroundInput;
    - (void)_interruptExecutingPlaygroundSource;
    - (void)cancel;
    - (BOOL)canFinishExecution;

    [...]

    @end

![](images/swift-bg-2.0.jpg)

---

    @interface IDEPlaygroundExecutionParameters : NSObject

    [...]

    - (id)initWithSourceCodeToExecute:(id)arg1 
                      documentFileURL:(id)arg2
                      documentContentTimestamp:(id)arg3 
                      autoTerminationDelay:(unsigned long long)arg4 
                      executionPreparationParameters:(id)arg5 
                      playgroundReportResultBlock:(id)arg6 
                      playgroundExecutionWillFinishBlock:(void)arg7
                      playgroundExpressionCompleteBlock:(id)arg8 
                      errorHandlerBlock:(void)arg9;

    @end

![](images/swift-bg-2.0.jpg)

---

![original, 180%](images/import-afnetworking.png)

---

# SourceKit

![](images/swift-bg-2.0.jpg)

---

    @interface IDESourceLanguageServiceSwift : DVTSourceLanguageService

    [...]

    - (void)_applyChangesFromSourceLanguageServiceContext:(id)arg1;

    [...]

    @end

![](images/swift-bg-2.0.jpg)

---

    05/07/14 09:43:08,109 Xcode[9202]: toy-unboxing -- Fixed context: {
        DVTSourceLanguageServiceContextFormatOptionsKey =     { ... };
        DVTSourceLanguageServiceContextTextStorage = ...;
        IDESourceLangaugeServiceContextBuildSettings =     {
            swiftASTCommandArguments =         (
                "-module-name",
                Playground,
                "-target",
                "x86_64-apple-macosx10.10",
                "-sdk",
                "/Applications/Xcode6-Beta2.app/.../MacOSX10.10.sdk",
                "-F",
                "/Applications/Xcode6-Beta2.app/.../Frameworks",
                "-F",
                "/Applications/Xcode6-Beta2.app/.../PrivateFrameworks",
                "-Xfrontend",
                "-debugger-support",
                "-c",
                "/Users/boris/Desktop/MyPlayground.playground"
            );
        };
        IDESourceLanguageServiceContextDocument = ...;
        IDESourceLanguageServiceContextDocumentURL = ...;
    }

![](images/swift-bg-2.0.jpg)

---

IDESource**Langauge**ServiceContextBuildSettings

![](images/swift-bg-2.0.jpg)

---

IDESourceLang**au**geServiceContextBuildSettings

![](images/swift-bg-2.0.jpg)

---

### (╯°□°）╯︵ ┻━┻

![](images/swift-bg-2.0.jpg)

---

    [...]

    "-F",
    "/Users/boris/Library/Developer/Playground Frameworks",

    [...]

![](images/swift-bg-2.0.jpg)

---

![](images/contentful-playground-fail.png)

---

    import XCPlayground

    XCPSetExecutionShouldContinueIndefinitely()

![](images/swift-bg-2.0.jpg)

---

![](images/contentful-playground.png)

---

# Demo

![](images/swift-bg-2.0.jpg)

---

![original, 100%](images/playground-builder.png)

---

# Relevant WWDC 2014 sessions

- Session 408: Swift Playgrounds
- Session 409: Introduction to LLDB and the Swift REPL

![](images/swift-bg-2.0.jpg)

---

# Links

- <http://samdmarshall.com/blog/custom_frameworks_and_swift.html>
- <https://github.com/jas/swift-playground-builder>
- <http://stackoverflow.com/questions/24058336/how-do-i-run-asynchronous-callbacks-in-playground>

![](images/swift-bg-2.0.jpg)

---

# Thank you!

![](images/yes-yes.gif)

---

### <http://vu0.org/playgrounds>
### <http://vu0.org/alt14>
### @NeoNacho

![](images/swift-bg-2.0.jpg)

---

### It's a zero!

![](images/Playstation2_slim_front.jpg)
