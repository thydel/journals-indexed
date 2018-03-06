**Fix jpeg for samsung panorama**

- [all index](/indexed/tde/journal-tde.md)
- dates: [2018-02-26](/indexed/tde/journal-tde.md#dates-2018-02-26)
- tags: [jpeg](/indexed/tde/journal-tde.md#tags-jpeg), [panorama](/indexed/tde/journal-tde.md#tags-panorama), [photo](/indexed/tde/journal-tde.md#tags-photo)
- nodes: [tde-ws](/indexed/tde/journal-tde.md#nodes-tde-ws)
- actors: [tde](/indexed/tde/journal-tde.md#actors-tde)



# Table of Contents

-   [jpegoptim fails for samsumg panoramic](#jpegoptim-fails-for-samsumg-panoramic)
-   [Someone have a fix](#someone-have-a-fix)
-   [New template to store incoming pictures](#new-template-to-store-incoming-pictures)
-   [Somes usefull packages](#somes-usefull-packages)


# jpegoptim fails for samsumg panoramic

```console
$ jpegoptim -p -m90 -v 2016-08-14_11-22-04.jpg
Image quality limit set to: 90
2016-08-14_11-22-04.jpg 6272x3744 24bit N Exif Adobe JFIF  (Invalid SOS parameters for sequential JPEG)  [WARNING]  (Unsupported marker type 0x08)  [ERROR]
```

# Someone have a fix

Gets [bcyrill/fix_eoi.py][] and apply fix to the fix

```
proot -w /usr/local/bin curl -O https://gist.githubusercontent.com/bcyrill/e59fda6c7ffe23c7c4b08a990804b269/raw/e2821f480abd114a5a0062dbd3eed474a362a51d/fix_eoi.py
echo -e '/if version != 101:/s//if (version < 101) or (version > 103):/\nwq' | ed /usr/local/bin/fix_eoi.py
chmod +x /usr/local/bin/fix_eoi.py
```

[bcyrill/fix_eoi.py]: https://gist.github.com/bcyrill/e59fda6c7ffe23c7c4b08a990804b269 gist.github.com

# New template to store incoming pictures

```
ls *.jpg | xargs -i echo fix_eoi.py \"{}\" | dash
ls *_pano.jpg | cut -d_ -f1 | xargs -i echo 'touch -r "{}.jpg" "{}_pano.jpg"' | dash
mkdir -p .2rm
ls *_pano.jpg | cut -d_ -f1 | xargs -i echo 'mv "{}.jpg" .2rm' | dash
jhead -n%Y-%m-%d_%H-%M-%S -ft *.jpg
jpegoptim -p -m90 -v *.jpg
```

# Somes usefull packages

```
echo jhead jpegoptim jpegtran exiftool | fmt -w1 | xargs -i apt-file search {}
sudo aptitude install jhead jpegoptim libjpeg-turbo-progs libimage-exiftool-perl
```
