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
v0.7.0.6 - 2024/06/14
 - Big performance pass
 - Fixed a missing button icon here and there
 - Fixed a bug where 'Sat.vs.sat' was applying at '1' (no effect, but a hit to performance)
 - Added a version tag to the string-preset
   
v0.7.0.3 - 2024/06/09
 - Added a workaround for SONY .ARW not loading Camera Matrix
 - Added Exif support. Saved files will now include Artist (if entered in settings), Saulala version + Sauce name, and most of th phone-provided Exif information (minus location)
 - Reworked Jungle Honey and Azure Cream sauces from scratch (Jungle Honey now includes a bit of post-formation tint in the darker areas; Azure Cream tidied up and less purplish). The overall feel should be the same.
 - Reworked file naming. Now, if the file exists, it will just add a _1 increment to the date, instead of adding HHMMSS. Filenames fe really inflated and difficult to track.
 - Exposure and Power is once again done outside OCIO, to accommodate potential pipeline additions
 - Target Luminance slider now has a bit of overhead: if required, target luminance can now be gently increased.
 - "Presets" button will now open a popup that will allow you to generate a development string that you can share with others. The string includes all slider settings, sauce and grain choices. Presets are still available by clicking 'PRESETS' in the popup.
 - Reworked "Target Black". It is no longer a part of the Sigmoid.
 - Reworked "Jungle Honey" & "Azure Cream" sauces
 - Reworked how grain is displayed in the viewfinder. Should be much closer to what's exported.
 - Slight performance improvements
 - Updated "About" page
 - Buttons no longer disappear when clicked
 - Added a "Sharpen" toggle in Settings. ON by default.
 - Fixed couple of bugs where saved presets could load values that are slightly off
 - config.ocio will include the AgX_Default_Contrast curve for each sauce (unless specified otherwise)

v0.5.1.1 - 2024/05/09
 - Hopefully improved "Purity". It's once again a post-formation-only process.
 - Added PowerPToe curve to deal with negatives after applying a camera matrix
 - Added PowerPToe curve after Purity adjustment to deal with negative values introduced by the Purity adjustment
 - Slightly inset the blue primary at the beginning of the pipeline to deal with the aggressive blues
 - Once again reworked 'Saulala' sauce (this is a continuos process)
 - Fixed a bug where cropping UI would break after rotating the photo 90 degrees

v0.5.0.5 - 2024/03/22
 - Added Jungle Honey sauce
 - Added Azure Cream sauce
 - Added rudimentary perspective correction controls
 - Fixed a bug where rotating the image by 90 degrees would crash the app
 - Added 'Dynamic Scaling':
     Once the app is done receiving input, it will display the preview at 2x density (2x size). 
     The preview image will automatically be replaced by a lower resolution one if any of the sliders are actively receiving input.
 - Added 'Resampling' after cropping:
     The preview image will get scaled properly after going through cropping.
 - Added pinch-to-zoom:
     Pinch-to-zoom will enlarge the image over the UI. This is the 2x preview density 'stretched out'.
     Releasing repositions and returns the image to its original size. No pixel peeping!
 - Overhauled Cropping UI:
     Out with the crosshairs, in with the circles.
     It is now a slightly more efficient process (fewer drawn UI objects)
 - Overhauled 'Sauces' Selection
 - Moved the 2x update to a different thread to prevent micro-stutters after moving a slider and immediately moving a different slider
 - Fixed a weird bug where resetting the Power slider after resetting the Purity slider would reset the Power slider, but not update the view
 - Sauce selection window is a bit more snappy
 - Added basic OpenEXR support. Android users will have to add ".dng" to their exr file's filename for it to appear in the selector. So the filename should look like "filename.exr.dng". Make sure your files have REC.709 primaries.
 - Fixed a bug where loading a new image would retain old image's Tilt settings
 - Added a method of dealing with negative values (offset + gain), instead of just clipping them

v0.4.2.2 - 2024/02/24
- In addition to "Open With" you can now "Edit" with Saulala. Basically any "Edit" button should suggest Saulala.
- Triple-tapping any slider should reset all sliders to their default positions 
- Using the Android "Back" button, gesturing "Back" or hitting ESC on desktop will bring you to "Develop" window, or ask you whether you want to quit the app (if already in "Develop" window)
- If the app was launched via "Edit", it will close (and return you to the gallery app) once you hit "Export" and the export has finished.

v0.4.1.1 - 2024/02/21
- Fixed a bug where accidental decrease in luminance of yellows in "Saulala" Sauce's LUT caused a darkening of very light areas.
- Added a "Tint" slider, which controls the tint of areas that went through "highlight reconstruction".
- "Sliders" are replaced by "Scrollers"
- "Scrollers" have haptic feedback (vibrations). However, each phone might treat this differently.
- Finally fixed double-tap-to-reset (on the scroller).
- Minor tweaks to Saulala Sauce
- Increased the gap between the edge of the screen and the end of the slider to try avoid triggering the 'back' gesture
- Viewport image preview size is now based on the viewport size
- Added "Haptic Feedback" option in Settings
- Small optimisations that resulted in ~25% increase in preview update speed
- Added "Tint" info box
- Fixed a bug where the clipping indicator would light up after exporting an image.
- Increased the sensitivity of the scrollers
  
v0.3.0.0 - 2024/01/25
- Fixed a rather elusive bug where the module that parses raw files failed to hand off the image array with rec.709 primaries, instead just used camera primaries. This resulted in a slightly weird starting point image. This only affected Android devices.
  
v0.2.10.0 - 2024/01/12
- Fixed a bug where opening the "Presets" screen would crash the app.
- Slight tweak to the 'smoothening' curve, slight reduction of the lustre effect.

v0.2.9.0 - 2024/01/05
- Fixed a bug where toggling the "Frame" toggle on the export popup the first time didn't actually changed the setting
  
v0.2.8 - 2023/12/06

- "Sauce" is now taken into account when saving/loading presets. (Does not change the sauce choice; the sauce that is manually selected will be loaded when a new photo is loaded) (Potential bugs here) (thanks Joegen!)
- Presets tidied up. No longer crashes if a setting is no longer present (I.e. 'fade')
- "About" page tidied up. Now if you click on version/date, it will take you to Github.
- "Highlight" mode set back to "Blend", and base exposure lowered (in order to minimise clipped data)
- Now a curve is applied before formation, in order to smoothen out the upper-upper values.
- Fixed a bug where using "Open With" and using a frame with meta-text, the 'capture date' returned 'file not found'
- Export popup now remembers the "Frame" setting
- Fixed a bug where clipping indicator would not reset after resetting the slider
- Fixed a problem where reducing "Purity" would break the picture

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
