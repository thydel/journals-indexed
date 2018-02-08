**Set PDF file timestamp from metadata**

- [all index](/indexed/tde/journal-tde.md)
- dates: [2018-02-08](/indexed/tde/journal-tde.md#dates-2018-02-08)
- tags: [pdf](/indexed/tde/journal-tde.md#tags-pdf), [date](/indexed/tde/journal-tde.md#tags-date), [exiftool](/indexed/tde/journal-tde.md#tags-exiftool), [awk](/indexed/tde/journal-tde.md#tags-awk)
- nodes: [tde-ws](/indexed/tde/journal-tde.md#nodes-tde-ws)
- actors: [tde](/indexed/tde/journal-tde.md#actors-tde)



# Table of Contents

-   [Set PDF file timestamp from metadata](#set-pdf-file-timestamp-from-metadata)


# Set PDF file timestamp from metadata

```
ls *.pdf | awk '{ f=$0; s=" "; q="\""; "exiftool -s3 -CreateDate -d" s q "%Y-%m-%d %H:%M:%S" q s q f q | getline; print "touch -d" s q $0 q s q f q }' | dash
```
