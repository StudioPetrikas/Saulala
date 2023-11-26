# Saulala
Issue tracker for Saulala beta - A free camera-native file (raw) developer, that uses AgX as its backbone. 

<a href='https://play.google.com/store/apps/details?id=com.saulala.saulala&hl=en_GB&gl=US&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img width="200px" height="auto" alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png'/></a>

www.saulala.com

## Usage instructions:
https://youtu.be/1JoZ9NqBmjs?t=315

I recommend installing a logcat reader of sorts. Error reporting is still sparse, but I've got a bunch of print commands that should help when trying to swat bugs. 
I use "Logcat Reader Pro". Filter by "Python". 

## Crash-course:

- The app doesn't connect to the internet, you can firewall it if you wish
- All photos are tagged with sRGB colour profile. Check if your Android display settings are set to "Natural" or "sRGB" to see what you're getting.
- Photos are saved to Pictures/Saulala
- There's a menu hidden in the top left Saulala icon.
- Everything is rather slow, since we're running Python and a full-blown OCIO. Be patient while importing/exporting. Rest should be snappy.
- If your native Android Camera App does not support .DNG capture, use Open Camera form the Android Store.
- Some Android galleries allow "Open As". Select the .DNG, open as, Saulala. Otherwise, open via launching the app itself.
- Settings / Presets are deleted on app Uninstall

## Changelog:
v0.2.5 - 2023/11/19
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
