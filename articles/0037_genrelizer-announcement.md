---
type: announcement
title: New feature and crowdsourced repo -- Genrelizer
banner: generic.webp

authors:
  - frickitickitavi
---

# New feature and crowdsourced repo: Genrelizer
YARG Nightly just got a new feature, and it needs your help!

If you have a big collection of charts from various sources, you probably know the pain of trying to sort through an unstandardized list of genre names, It's great that charters can express any hyperspecific genre they want, but it's no good for sorting and filtering. Our solution is simple on the surface level: a `genre` metadata tag that pulls from [our official list of genres](https://wiki.yarg.in/wiki/List_of_common_genre_names), and a freeform `sub_genre` tag that lets you express whatever nuance you want. Official YARG content already uses these tags, so you can go see some hand-crafted descriptions of your favorite setlist and DLC songs in the Nightly music library.

But you might be wondering - how does this help my sprawling library of customs with crazy `genre` tags and no `sub_genre` tags? That's where the new [Genrelizer](https://github.com/YARC-Official/Genrelizer) repo comes in. Just like OpenSource, this is a crowdsourced GitHub repo that YARG reads from at launch. It contains mapping files for YARG's official genres, each containing lists of dozens to hundreds of recognized subgenres to use in categorizing your charts. Have a custom with `genre = Symphonic Technical Death Metal`? That's not an official genre, but Genrelizer recognizes it as one of the subgenres for the `Death/Black Metal` genre, and your chart ends up with `genre = Death/Black Metal ; sub_genre = Symphonic Technical Death Metal`. Charter intent is preserved, but your charts get neatly categorized.

We're very proud of the breadth of subgenres we've covered, but **Genrelizer is always open to new submissions!** If you have a chart with a genre that Genrelizer doesn't recognize and dumps under `Other`, please submit a pull request to add a mapping for that subgenre!

## FAQs
For gory details about how Genrelizer works and how to contribute, see the docs in the Genrelizer repo. But up front, here are a few FAQs:

**I don't want my genres getting messed with - can I turn this off?** - Yes! Go to `Settings > Songs` and clear the `Standardize Genre Metadata` toggle. You'll need to rescan any time you change this setting.

**Does this edit my chart files?** - Nope; this all happens inside YARG. Your chart files will never be edited.

**I don't like that Genrelizer categorizes <x> as a subgenre of genre <y>. What if I want my chart to have subgenre <x> but genre <z> instead?** - No worries; Genrelizer isn't here to police your subgenres. If you fill out the `sub_genre` field, Genrelizer will honor it - you can make a `Grindcore` chart with the `Bubblegum Pop` subgenre and it won't bat an eye. It kicks in to categorize charts with unrecognized genres and blank subgenres, not to correct the subgenres that you explicitly provide.