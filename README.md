# Saulala
Issue tracker for Saulala beta - A free camera-native file (raw) developer, that uses AgX as its backbone. 

<a href='https://play.google.com/store/apps/details?id=com.saulala.saulala&hl=en_GB&gl=US&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img width="200px" height="auto" alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png'/></a>

Website:
www.saulala.com

Discourse:
https://saulala.discourse.group

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
- Double-click to reset a single slider, tripple-click to reset them all.
- Settings / Presets are deleted on app Uninstall

## Changelog:
**v0.9.2.1 - 2025/02/28**

Global Changes:

- Fixed a bug that caused 'handles' in the Cropping UI to get detached from the cursor, when the cursor left the circle of the handle.
- Added EXIF 'sRGB' tag (Different from Colour Profile tag). Lack of this 'sRGB' tag may cause certain Windows applications to display the output JPG incorrectly
- Added centre crosshair and 'thirds' cropping guides when any of the cropping handles are being moved
- Slightly modified the approach to sauces + re-tweaked all the sauces. Pictures will appear more colourful on load and should exhibit less noise
- Switched the de-mosaicing algorithm to DHT
- Reduced the impact of the 'Purity+' slider
  
**v0.9.1.8 - 2025/02/08**

Global Changes:

- Undid a regression where "Target Luminance" was placed before the picture formation
- Tweaked the AgX-like_Increased_Shoulder curve to better match AgX_Default_Contrast (previously matched the wrong curve)
- Code cleanup / slight performance gains
- Added a custom matrix for Fuji RAF files
- Reduced the effect of "Target Black" slider
- Small tweaks to Saulala, Azure Cream and Gilded Mint sauces
- Double-clicking "Default / None (AgX)" Sauce will switch to AgX Kraken (full sRGB pipeline with no rotations). For debugging purposes. This setting does not "stick".
- Moved 'Purity+' process to tiled processing (performance boost)

Desktop-only changes:

- Fixed a bug where the 'back' arrow of the 'Export' modal could become misplaced after exporting once and then changing the window size
- Reduced info text size that's displayed on the viewport

**v0.9.1.6 - 2025/01/31**

Global changes:
- Fixed a bug introduced in v0.9.1.5 where adding a frame would crash the app on image export

**v0.9.1.5 - 2025/01/30**

Global changes:
- New 'highlight recovery' method (more akin to 'desaturation' than 'reconstruction')
- 'Classic saturation' formula has been replaced with a Sat vs. Sat formula (for the 'Purity+' slider).
- Added more tiled processing here and there, reducing RAM usage and increasing processing speed
- Export size selection rework - a 50% option will appear if the original dimensions are large enough
- Added new 'Gilded Mint' sauce
- Adjusted 'Atlantic Tomato' sauce to be slightly more versatile and slightly less brown-feeling.
- 'Gilded Mint' and 'Azure Cream" will use an AgX-like curve with a slightly increased shoulder
- Disabled the shadow under the viewport
- Image will now be automatically reloaded if 'Gainmap' switch was toggled
- Removed Green / Peach sauce
- Increased overlap between the image and the frame by a few pixels to hopefully fix a problem where a black edge my appear when adding a frame
- Re-added basic X3F file support

Desktop-only changes:
- Added the ability to change background colour (temporary solution - small bubble in the corner)

**v0.9.0.4 - 2024/12/11**

Global changes: 
- Added tiled file loading. Larger files should load about twice as fast, depending on file size and processor threads. (And uses a lot less RAM)
- Slight Saulala sauce tweak
- .cube file for AgX sauce has been replaced by an inset + rotation matrices and now more closely match the Resolve DCTL
- Fixed a bug where using 'Grain' with an image that is smaller than 1000px by 1000px could cause issues with the pipeline
- Fixed a bug where files that had an Opcode in EXIF Opcode3 that was not WarpRectilinear would not load.
- Fixed a bug where the development string would not get added to the exported .jpg, unless the 'Presets' button was clicked.
- Implemented 'clipped-at-the-sensor' area improvement. (Commonly referred to a s 'highlight recovery')
- Added a temporary (hopefully) fix for files with As Shot White XY.

Desktop-only changes:
- Fixed a UI bug where the exported path was shown under the viewport after a successful export.

**v0.8.9.8 - 2024/11/26**

Global changes:

- Added an option to gently chroma-denoise the picture. The option is found in the Settings, and resets every time a new image is loaded.
- Tidied up the "Settings" window
- More improvements to DNG Gainmap (added dithering and improved on the pink-ish cast in the clipped areas)
- Fixed a bug where enabling noise reduction could mess with the clipping indicator
- Added process log display (tells you what is happening currently when loading an image)
- Added a confirmation after a successful export
- Removed the ability to add frame to certain file types
- Added DNG 'WarpRectilinear' support (automatic lens distortion correction)
- Reworked and improved EXIF data support - now copies ALL EXIF data from the camera-native file. Including Fuji.
- Fixed a bug where reducing the Exposure would also perform a slight subtraction operation
- 'Rotate' and 'Crop' screens' viewports were updated to match 'Develop' viewport
- Fixed a bug introduced in v0.8.9.0 where DNGs with faulty / weird gainmap instructions will not load
- Fixed a bug where 'Loading' text remains red after the error has been cleared

Desktop-specific changes:

- Fixed a bug where using the scroll-wheel on the development sliders would zoom the picture in and out.
- Cleaned up the interface by removing the unnecessary black bar at the top
- Fixed a bug where drag-and-dropping an image would not refresh the 'captured' date
- Sidebar is now fixed-width
- 'Slide-out' window animation has been changed to 'Fade-out', to reduce unnecessary motion.

Android-specific changes:

- Fixed a bug where going to Settings window and back did not clear the shadow under the viewport
- Fixed a bug where using "open with" would not load some of the animations
- Fixed a bug where the shadow under the viewport would not clear when leaving / entering 'Develop' window

**v0.8.9.2 - 2024/11/13**

Global changes:

- Hopefully fixed the 'None' capture date in the frame's meta information
- Added .DNG Gainmap support (For lens corrections)
- Added .DNG Gainmap switch in the settings (ON by default)
- "Target black" is now a post-formation operation, that takes place after "Purity". Which means the picture will be less likely to exhibit the 'hole' or 'punch-through' error.
- Further tweaks to most of the sauces
- Increased the image size by ~1px when frame is ON (create a bit of overlap)
- Fixed a bug where using "Target Luminance" with "Sharpen" setting set to ON would break the pipeline
- Switched 'Highlight Reconstruction' from 'Blend' to "Reconstruct 3" (dcraw -H 3 equivalent), because 'Blend' resulted in black highlights in some edge-case captures

Desktop-specifi changes:

- Mouse-wheel will zoom the picture in. Any click will reset the zoom.

**v0.8.8.3 - 2024/10/27**

- Attempt to fix a bug where captured date resulted in 'None'

Desktop-specific changes:
- Fixed an UI issue in the 'About' section, where maximising the window could cause elements to overlap. 

v0.8.8.2 - 2024/10/26

Android-specific changes:

- Clicking the viewport background in the 'Develop' screen will cycle through different background colours. White -> Gray -> Black (The background will default to white every launch)
- UI should scale with resolution (some Android versions have a 'reduced resolution' option that's ON by default for battery saving)

Global changes:

- Removed 'Add frame' selector from the 'Export' modal
- Removed frame colour selector from the 'Settings' menu
- Added a 'Frame' button in the 'Develop' screen (Please report any UI issues) ('Frame' button will cycle through frame colour selection)
- Frame will be drawn as UI, using Kivy (previously it was baked-into the image array, which meant a hit to performance)
- Added frame text in the preview
- 'Loading...' text is now drawn instead of it being an image
- Tidied up loading (some functions were too RAM hungry, creating crashes on some older Androids)
- Fixed a bug where changing the window size after cropping would crash the app on export
- Capture date will now try to pull "Created Date" from the EXIF, if it fails it will use "Modified date" (previously always "Modified date")
- Frame text will now use  Noto Sans Monospace Bold font, instead of OpenCV2's 'Hershey'.
- Adding a frame will scale the image down slightly (less cropping-off)
- Added UI animations here and there (more will be added over time)
- Sauce rework: Sauces now lean heavily on the config.ocio, instead of cube LUTs. They should now be a lot more resilient to breaking. All sauces have been reworked from scratch.
- Experimental array caching (RAM-saving measure)
- Grain setting toggle has been removed. Grain can now only be applied as an overlay. (Moving away from pseudo-film mockery)
- Fixed the clipping indicator turning on and off when releasing a slider
- Pure log2 function in AgX Log will now be replaced with a log2 function with a linear segment near black (Which will now be controlled with "Target Black" slider). The function itself is identical to the log2 function in AgX Log.
- Big performance boost
- Tweaked 'sat vs. sat' slider to reduce the 'darkening' effect of the areas affected by sat vs. sat
- Viewport drawing improvements; various graphics should load faster and feel snappier
- Temporarily disabled 2399 sauce
- Updated "Exposure" and "Grain" descriptions
- Updated Sauce previews
- Fixed a bug where loading certain files would crash the app.
- Added a new mechanism which should help retain tint in the dark areas of the pictures, especially when "Target Black" is used.
- Sauce adjustment pass. Generally, reds have been nerfed (they were slightly problematic before), sauces lean into their 'taste' more strongly, 'Atlantic Tomato' unleashed its full potential.
  
**v0.8.4.7 - 2024/09/10**
- Fixed a bug where PC versions might have had their 'highlights' mode set to 'clip' instead of 'blend'
- Fixed a bug gesturing or going back from 'Sauces' screen did not refresh the viewport (while pressing the back button on the top did)
- Added 'Atlantic Tomato' sauce
- Added loading animations for PC when drag-and-dropping captures

v0.8.4.4 - 2024/07/30
- Fixed a bug that broke the clipping indicator
- Potentially fixed a bug where Tint slider could break the pipeline
- Fixed a bug where selecting "Common" export size would still export full-sized image
- Removed duplicate file loading function. ~200 lines of code have been deleted.
- Reworked 'Purity' from ground up. All camera files will now use (either provided or standard) matrices. (Previously, many dedicated-camera files had their matrices ignored). It is now once again a pre-formation and a post-formation operation.
- Fixed some loading issues. Sometimes UI was choppy, or unintuitive
- Added more credits to the 'About' page (please let me know if I got a name wrong)
- Added AgX Resolve DCTL default hue rotations to the 'AgX / no sauce" sauce.
- Slight tweak to Saulala Sauce
- Purity is now "Purity+" (name pending) and moved up in the list of sliders. When increasing the value of the slider, it will gently increase Power (behind the scenes). If you feel it's too much, you can always reduce the Power afterwards using the Power slider.
- Hopefully fixed a bug where double-clicking and triple-clicking a slider did not update the viewport.
- Added "3x2" and "2x3" cropping aspect ratios
- Fixed a bug where the cropping UI would show an incorrect 'selection', when an image was previously cropped using any 'locked' aspect ratio.
- Cool/Warm balance and Pink/Green balance sliders now have a 'ramping' effect. (Should be more or less the same sensitivity at low values, and become really sensitive at high values)

v0.8.3.1 - 2024/06/30
 - Added multi-threading (tiling) support. 2x preview loads about 2-4x times faster which makes the sliders feel a bit more snappy
 - Reworked how sliders interact with the viewport. Viewport updates are now done on a separate thread, so the sliders should feel much smoother, which should result in a much more pleasing user-experience.
 - Added automatic-cropping for after rotating the image (needs testing, weird interactions with tilt)
 - Shaved off a few seconds of initial raw loading time
 - Reduced the amount "Target Black" can be increased by
 - Changed how 'Grain' is previewed in the viewport. Should match the export much closer now.
 - Untangled and de-spaghettified a lot of the non-pipeline code. Double-clicks and Triple-clicks on sliders should perform as intended now.
 - 2x resolution updates now only happen when touch event stops. (I.e. you lift a finger off the slider)
 - Redrawn most of the clickables from scratch. Out with the PNGs, in with the canvas objects.
 - Fixed a bug where the Cropping would report incorrect aspect ratio lock chosen
 - Added a setting that enables saving the 'development string' into the .jpg metadata (OFF by default)
 - Clicking on the area where the development string should be pasted will paste it on-clicking (instead of requiring to do a 'paste' maneuver)
 - Fixed a bug where rotation didn't reset on loading a new image
 - Fixed a bug where entering Crop / Rotate windows will momentarily load the previous preview (caching problem)
 - Updated Target Luminance and Cool / Warm Balance info boxes
 - Fixed a bug where you could lose a row of pixels when cropping 
 - Fixed a bug where "Rotate" slider did not correspond with the angle
 - Made the sliders better correspond with the haptic ticks and the value indicated

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
