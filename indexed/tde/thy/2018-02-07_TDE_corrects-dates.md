**Apply file timestamp shift**

- [all index](/indexed/tde/journal-tde.md)
- dates: [2018-02-07](/indexed/tde/journal-tde.md#dates-2018-02-07)
- tags: [photos](/indexed/tde/journal-tde.md#tags-photos), [date](/indexed/tde/journal-tde.md#tags-date), [jpeg](/indexed/tde/journal-tde.md#tags-jpeg), [jhead](/indexed/tde/journal-tde.md#tags-jhead), [awk](/indexed/tde/journal-tde.md#tags-awk)
- nodes: [tde-ws](/indexed/tde/journal-tde.md#nodes-tde-ws)
- actors: [tde](/indexed/tde/journal-tde.md#actors-tde)



# Table of Contents

-   [Corrects file timestamp](#corrects-file-timestamp)
-   [Corrects jpeg header and rename](#corrects-jpeg-header-and-rename)


I've got some photos from a camera with a wrong date setting.

# Corrects file timestamp

After empirically finding a correct enough time shift

```
ls *.JPG | awk '{f=$1; "date -r " f | getline; "date -d \"" $0 " + 8 years + 18 days - 30 minutes\"" | getline; print "touch -d \"" $0 "\"", f}' | dash
```

# Corrects jpeg header and rename

```
jhead -dsft *.JPG
jhead -n%Y-%m-%d_%H-%M-%S *.JPG
```
