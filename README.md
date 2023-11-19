# Saulala
Issue tracker for Saulala alpha

## Known issues:
Known (big) bugs:

- App becomes unresponsive after switching tasks

I recommend installing a logcat reader of sorts. Error reporting is still sparse, but I've got a bunch of print commands that should help when trying to swat bugs. 
I use "Logcat Reader Pro". Filter by "Python". 

## Alpha crash-course:

- The app doesn't connect to the internet, you can firewall it if you wish
- All photos are (for now) tagged with sRGB colour profile. Check if your Android display settings are set to "Natural" or "sRGB" to see what you're getting.
- Photos are saved to Pictures/Saulala
- "Info" buttons next to sliders do nothing for now
- There's a menu hidden in the top left Saulala icon.
- Rest of the menu items are empty (not that crucial for now)
- Everything is rather slow, since we're running Python and a full-blown OCIO. Be patient while importing/exporting. Rest should be snappy.
- The -| and the |- icons next to the sliders indicate whether the operation takes place pre or post image formation. -| means "before" (power, slope, etc.), |- means after (Purity, Fade etc.)
- If your native Android Camera App does not support .DNG capture, use Open Camera form the Android Store.
- Some Android galleries allow "Open As". Select the .DNG, open as, Saulala. Otherwise, open via launching the app itself.
- Settings / Presets are deleted on app Uninstall

## Changelog:
Global changes:

- Fixed a cropping issue where the cropping tool became unstable when cropping Landscape images with 16:9 ratio
- Added the ability to add a frame to the exported image (not previewed, can be turned on in export pup-up)
- Added frame settings (in the Settings screen): Black or White frame, Rounded or sharp corners, "Meta Text" (Captured, Developed, Author)
- "Fade" has been removed
- "Target Luminance" has been added
- "Target Black" has been added
- Fixed an issue where keyboard could overlay the "Author" text input box
- Fixed another crop bug that allowed crosshairs move outside the boundary of the image
- Added 'Green / Peach' sauce based on Troy Sobotka's 'Golden Appearance'
- Added '2399' sauce by Juan Pablo Zambrano
- Added a "Bad file" error to the Development screen
- Purity is now slightly pre and slightly post operation
- Added a clipping (at the end of pipeline) indicator.
- Fixed some more Cropping bugs, too many to mention all.
- A bit of code clean-up
- Slope is now Exposure and has a range from -5 to 5
- Restructured and tidied up the pipeline (Saving up to 2GB of RAM on very large files)
- Got rid of the "Pre" and "Post" pipeline indicators on the main Develop screen
- Updated info boxes
