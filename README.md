# Saulala
Issue tracker for Saulala alpha

## Known issues:
Known (big) bugs:

- You need to explicitly allow storage access permissions on Android (Settings -> Apps (Applications) -> Select "Saulala" -> Allow Storage (& Music))
- App becomes unresponsive after switching tasks
- Main viewport becomes black after loading a new image, move a slider to refresh it

I recommend installing a logcat reader of sorts. Error reporting is still sparse, but I've got a bunch of print commands that should help when trying to swat bugs. 
I use "Logcat Reader Pro". Filter by "Python". 

## Alpha crash-course:

- The app doesn't connect to the internet, you can firewall it if you wish
- All photos are (for now) tagged with sRGB colour profile. Check if your Android display settings are set to "Natural" or "sRGB" to see what you're getting.
- Settings/Preset files are going to be stored in Documents/Saulala. Photos are saved to Pictures/Saulala
- "Info" buttons next to sliders do nothing for now
- There's a menu hidden in the top left Saulala icon.
- Menu buttons that work: "Sauces" (Where you can pick between AgX (default, no look applied) and Saulala (my personal flourish)
- Rest of the menu items are empty (not that crucial for now)
- Everything is rather slow, since we're running Python and a full-blown OCIO. Be patient while importing/exporting. Rest should be snappy.
- The -| and the |- icons next to the sliders indicate whether the operation takes place pre or post image formation. -| means "before" (power, slope, etc.), |- means after (Purity, Fade etc.)
- If your native Android Camera App does not support .DNG capture, use Open Camera form the Android Store.
- Some Android galleries allow "Open As". Select the .DNG, open as, Saulala. Otherwise, open via launching the app itself.
- B&W mode sometime soon.
- macOS version sometime soon
