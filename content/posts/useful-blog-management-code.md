+++
title="Useful Blog Management Code"
date=2021-05-17
extra.tldr="Code for me to use to not have to look stuff up on Stack Overflow when I am writing posts for this blog. More than you might expect! Like for converting images from PNG to JPG for web optimization."
+++

<!-- TODO: Fix the formatting on this page, it is absolutely fucked -->

# Convert MOV to Gif, Get good speed and optimize file size. Takes some time

```sh
ffmpeg -y -i Omnibot\ v40-cropped.mp4 -vf "scale=800:450" -f image2pipe -vcodec ppm - | convert -delay 2 -loop 0 -layers Optimize - gif:- | gifsicle -d 3 -O3 -o optimized.gif
```

source: https://superuser.com/a/1061409

```sh
sed 's/base_url\ =\ \"https:\/\/www.zachbellay.com\"/base_url\ =\ \"https:\/\/www.develop.zachbellay.com\"/g' config.toml >> config.toml
```

source: https://www.cyberciti.biz/faq/how-to-use-sed-to-find-and-replace-text-in-files-in-linux-unix-shell/

I hope this works lol, this is in the build step in netlify
