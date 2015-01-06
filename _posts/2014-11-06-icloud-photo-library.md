---
layout: post
title:  "iCloud Photo Library"
date:   2014-11-06 21:53:40
---

I store all of my photos in [iCloud Photo Library][].
It secures every digital photo that I have taken and kept since 1999 and makes them readily available to me on iOS and the web.

[iCloud Photo Library]: https://apple.com/icloud/photos

I really like the Collections view.
It groups photos by time and location similar to how I remember them.
It does this by using each photo's [Exif][] tags.

[Exif]: http://cipa.jp/std/documents/e/DC-008-2012_E.pdf

73 of my photos had no Exif tags though.
I had regrettably taken most of these with Instagram while in London and Scotland.
Without these tags the photos appeared out of place.

To fix this I created Exif tags for these photos using [ExifTool][].
A Windows [Gui wrapper][] is available.

[ExifTool]: http://sno.phy.queensu.ca/~phil/exiftool
[Gui wrapper]: http://freeweb.siol.net/hrastni3/foto/exif/exiftoolgui.htm

I set two tags:
- `DateTimeOriginal` which represents the date and time when the original image data was generated.
- `CreateDate` which is not in the Exif specification but is read when uploading photos to iCloud Photo Library using the web app.

Now that I've migrated 15 years of photos I use Photos the same way that a new user does.
Rather than Exif tags, folders and file names I think about moments, collections and years.
It's progress.