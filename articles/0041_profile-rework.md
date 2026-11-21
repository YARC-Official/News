---
type: announcement
title: Reusable Binding Sets Now in Nightly! (aka 'The Profile Rework')
banner: generic.webp

authors:
  - frickitickitavi
---

# Reusable Binding Sets Now in Nightly! (aka 'The Profile Rework')

The long-awaited profile rework has finally come to Nightly! Gone are the days of managing separate profiles for different instruments and game modes - you should now find it much simpler to edit bindings and use just one profile per person. This is a huge overhaul to how YARG handles profile and binding data, so expect some hiccups and please report any bugs you encounter (and thanks to those who already flagged bugs in the test builds! We tightened up a lot with that feedback)

Your existing bindings should carry over automatically, but consider backing them up first if you have a complex setup (see the FAQ below for instructions). If you've edited a lot of bindings in the past, you might find yourself with a lot of migrated sets - feel free to merge or remove ones that seem redundant or unnecessary

## High-Level Changes

* Previously, bindings were tied to individual profiles and were stored as a big soup of all of a profile's bindings across all devices and modes. Now, a binding set is a reusable structure that profiles can share, and which is scoped to contain bindings for just a single mode with a specific controller type
* The Profiles menu has a new Bindings tab, where you can edit your binding sets directly, even without signing into a profile or connecting a controller. You can hand-edit bindings by using dropdowns, or you can connect a "dummy controller" to use for the convenient press-to-bind functionality we've always supported
* Binding sets can be exported as `.yargbinds` files for sharing between different setups
* Previously, a profile's connected controllers and microphones weren't readily visible from the profile menu. Now, we have a device management UI built right into the profile view, so you can see and configure your devices in the same place you manage all your other profile settings
* When selecting a controller or microphone, we now allow you to "steal" a device that's claimed by another profile, without having to manually disconnect that controller from the old profile first

## FAQ

### Is this the overshell system that RB3/4 used?

No, but it's an important step toward implementing that. For now, you still have to navigate out to the Profiles to manage active players, but we hope to start in earnest on developing a proper overshell now that we've untangled the profile data structures under the hood!

### I have complex bindings - how do I back them up before upgrading?

Navigate to your Nightly installation's persistent data directory (see below), then go into the `profiles` folder and copy `bindings.json` to another directory. If something goes wrong with your bindings when you open Nightly (it shouldn't!), please file a report in <#1139681226907734201> and include that backup file

By default, you can find your Nightly persistent data directory here:
* Windows: `C:\Users\<username>\AppData\LocalLow\YARC\YARG\nightly`
* macOS: `~/Library/Application Support/YARC/YARG/nightly`
* Linux: `~/.config/unity3d/YARC/YARG/nightly`

### If binding sets care about specific controller types now, am I still able to make silly bindings like drums-on-guitar or whatever?

Absolutely! The UI allows you to make a binding set for any combination of mode and controller type - go ahead and make a "Pro Keys on 5-Lane Drumkit" binding set for all we care

### If I set up bindings for a Rock Band guitar, will those also work on a Guitar Hero guitar, and vice versa?

Yes! Well, for the controls they have in common, anyway. This update includes logic to generalize bindings between different families of 5F guitar controllers, so binding something to `greenFret` with one guitar type will apply to the green fret on _all_ 5F guitars. This wasn't previously the case, but it should make sharing bindings even easier!