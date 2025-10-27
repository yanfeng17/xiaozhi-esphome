
<img width="1600" height="950" alt="esphome-yaml-layout-pro-v8" src="https://github.com/user-attachments/assets/92c246d2-295a-4a11-8c03-87963034dcd6" />

This section is for those that tried the standard full yaml in the respective directories and everything works, but want more ;)

Those that just want the basics code to modify might find it easier to use the non-modular yamls.

👉 If you try this and run into problems, please revert to the known working non-modular YAMLs.
And if you believe the issue isn’t just user error, please report back. 😉

---

```markdown
## 🚀 Installation

1. Copy the YAML for your device (e.g. `Muma.yaml`) into your **ESPHome** configuration.  
   - Keep your own `name:` and `friendly_name:` values.  

2. Install the firmware to your device.  

3. (Optional) Update the **settings** section of the YAML if you want to:  
   - Change the `imagemodel`  
   - Change the `startup_sound`  

4. The **clockbackground** can be set directly from **Home Assistant (HA)**.

After this, if there is a update, all you need to do is compile again.
```

```markdown
## 🚀 Running locally (optional)

If you want to run and edit the Modular files locally:
1. Create a directory in your esphome/ directory called "localtest" and copy core.yaml + display_pages.yaml there.
2. Create a directory inside localtest/ called "HW" and copy the hardware file for your device there (eg. ball_v2_hw.yaml)
3. change the packages in main yaml on the device to:

packages:
  core: !include localtest/core.yaml
  hw:   !include localtest/HW/ball_v2_hw.yaml

```
Changes:
---
### Modular v1.08
- **Changes**
  - Updated most devices for mipi spi display drivers

### Modular v1.07
- **Changes**
  - Updated most devices with Music Assistant support

### Modular v1.06
- **Changes**  
  - Fixed swipes didn't work when "handle swipes locally" switch was off, optimized timing
  - changed minor non-breaking spelling mistake

### Modular v1.05
- **Changes**  
  - Added Rolex clockface (wallpaper) for analog clock
  - Fixed Battery status not showing on analog clock and presence (if enabled)

### Modular v1.04
- **Changes**  
  - Added Analog clock (yeah i know, why not)
  - Added switch for doing swipe actions internally (for better first experience), turn off if using automations.
    hardcoded swipe functions: left & right change clock style, down toggle battery, up change wallpaper.
  - Added light sensors for all 5 rooms and changed so presence shows a red LED dot. if light is on in room color is filled.

### Modular v1.03
- **Changes**  
  -  added 2 more clocks, a presence sensor clock and a weather clock

### Modular v1.02
- **Changes**  
  -  added 4 binary sensors for screen swipes, these do nothing by themself but are available in HA for whatevery you desire.
  -  Example automation that changes clock type (left and right swipes), changes wallpaper (swipe up) and toggles battery status (swipe down) can be found in: /Under_Development/Home_Assistant_Automations/
  -  I did it this way so it's not a locked functionality and we can do whatever we want with the sensors.

### Modular core v1.01
- **Fixes**  
  - fixed timer widget, fixed clock screensaver so it doesn't go on when timer is running
  - fixed so it also doesnt show clock until api image timer is done.
- **Changes**  
  - changed font for default clock from 30 to 42, and date font from 18 to 22
  - changed timer widget to new design. and removed 1 font (more memory saving ;)
  - removed removed 1 font, saved memory
  - moved micro wake words to main and left only "okay nabu" in core, this gives a wider selection of mmw's without loading all
---

## Older versions of Modular can be found in /OLD/ if wanting to revert to a previous version.

---

## Previous Changes (before resetting to Modular 1.00)

### Version 1.06 (dev)
- **Fixes**  
  - Media player buffer set to `250000`  
  - Speaker WAV, mono  
  - Removed `handle_screen_tap` from touchscreen section  

### Version 1.05 (dev)
- Show image API got its own timer  
- Added block so images only display in *idle* or *replying* phase  
- Added switch for time  
- Added clock wallpaper  

### Version 1.04 (dev)
- **Added:** Online clock wallpaper with select in HA  
- **New API service** to send images from HA:

```yaml
service: esphome.esphome_web_0bac48_show_fullscreen_image
data:
  url: "http://homeassistant.local:8123/local/funny.png"
````

### Version 1.03 (dev)

* Minor memory fixes
* Clock select from HA
* Removed one font (req/res font same)
* Removed `alpha_channel`

### Version 1.02 (dev)

* Cleanup and fixes

### Version 1.01 (dev)

* **Added:** Clock when idle for more than 10 seconds
* **Added:** Virtual touch (same functionality as touch available from HA: start, stop, stop timer alarm)
* **Added:** Use original `playing.png` emo when playing music on media player (still reverts to clock after 30s)
* **Added:** Timer ringing entity (can trigger automations)
* **Added:** Longer request/response entities for dashboards (limit 255 characters)
* **Fix:** Timer pages now dynamic for different screen sizes

### Version 1.00

* First working code ✅

