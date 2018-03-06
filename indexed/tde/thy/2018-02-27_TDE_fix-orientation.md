**Manually fix orientation**

- [all index](/indexed/tde/journal-tde.md)
- dates: [2018-02-27](/indexed/tde/journal-tde.md#dates-2018-02-27)
- tags: [jpeg](/indexed/tde/journal-tde.md#tags-jpeg), [orientation](/indexed/tde/journal-tde.md#tags-orientation), [photo](/indexed/tde/journal-tde.md#tags-photo)
- nodes: [tde-ws](/indexed/tde/journal-tde.md#nodes-tde-ws)
- actors: [tde](/indexed/tde/journal-tde.md#actors-tde)



# Table of Contents

-   [Howto fix orientation for old picture without EXIF orientation](#howto-fix-orientation-for-old-picture-without-exif-orientation)


# Howto fix orientation for old picture without EXIF orientation

Use `gthumb` to manually select and lossless rotate picture in some *folder* , then

```
exiftool "-FileModifyDate<DateTimeOriginal" $folder
```

`exiftool` tricks [Found on exiftool forum][]

[Found on exiftool forum]:
	http://u88.n24.queensu.ca/exiftool/forum/index.php?topic=4596.0
