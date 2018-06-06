# wwdc2018

W to repo wrzucamy wszystko co chcielibyście byśmy omówili z inżynierami Apple na WWDC. Kawałki kodu, problemy jakie napotkaliście, tickety z błędami (to ważne!), ew. omówienia tego co zobaczymy na keynote / a state of the union.

## HealthLogger
*mmynarski*

- dopytać o nowości w HK,
- przedstawić kontekst appki,
- zapytać o ew. problemy w implementacji. 

## General Questions

*kzietek*

###Sprite Kit

- Is Render-to-texture available?
	- I want to render a scene, apply a shader to every pixel on screen and display untouched GUI on the top. Is this posible with reasonable performance?
- I want to render the game scene in low resolution, upscale it and display GUI in native resolution. Is this possible?

###UIKit

- I want to apply blur in the same fashion as UIVisualEffectView but without changing the color and with a radius of 6pt. Contents underneath the view are moving. Is there a solution with decent performance? Currently I'm using private API and it's a shame that this isn't welcomed on the App Store:

```
    private static func createBlur(radius:CGFloat) -> UIBlurEffect {
        let customBlurClass: AnyObject.Type = NSClassFromString("_UICustomBlurEffect")!
        let customBlurObject: NSObject.Type = customBlurClass as! NSObject.Type
        let blurEffect = customBlurObject.init() as! UIBlurEffect
        blurEffect.setValue(1.0, forKeyPath: "scale")
        blurEffect.setValue(radius, forKeyPath: "blurRadius")
        return blurEffect
    }
```