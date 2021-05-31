# hugo-video

<!-- [![Awesome](https://awesome.re/badge.svg)](https://github.com/budparr/awesome-hugo) -->

## About

This [Hugo](https://gohugo.io) theme component provides a shortcode: `video` for embedding videos using the [HTML video element](https://devdocs.io/html/element/video).

It comes with english, french, german and russian localization. Other languages welcome! Send your pull request.

## Features

This shortcode uses Hugo [Page Resources](https://gohugo.io/content-management/page-resources/). The video to display __must be placed in the [page bundle](https://gohugo.io/content-management/page-bundles/)__.

The shortcode takes one mandatory argument: the filename of the video file to display, __without the extension__. It detects automatically if several versions of the file exists in the page bundle, and add accordingly the multiple `src` tags. When an image file with the same filename is also present in the page bundle, it is automatically used as a poster frame.

When the browser doesn't support the [HTML video element](https://devdocs.io/html/element/video), the shortcode displays a localized notice allowing the video download for local playing.

Following video formats are supported:
- MP4 (extension `.mp4` or `.m4v`)
- WebM, (extension `.webm`)
- Ogg, (extension `.ogv`)

Default values:
- Browser's default controls are displayed (`controls` attribute is always included)
- Video can be preloaded (`preload="auto"` attribute is always included)
- Video width is 100% (`width="100%"` attribute is included); this can be changed by indicating the desired width when calling the shortcode, see example below)
- Video height attribute is not set by default, but can be explicitly set by indicating the desired height in pixels (i.e. `height="640"`); credit goes to Evgeny Kuznetsov for this feature
- Following other video attributes can be set: `muted="true"`, `autoplay="true"` and `loop="true"`. Credit goes to Tom McKenzie for this feature
- Default settings are used for other video attributes

When no video file of the given name is found in the supported format (see above), the shortcode __intentionally fails__ with a `No valid video file with filename <filename> found.` error.

## Usage

1. Add the `hugo-video` as a submodule to be able to get upstream changes later
    ```bash
    git submodule add https://github.com/martignoni/hugo-video.git themes/hugo-video
    ```
2. Add `hugo-video` as the left-most element of the `theme` list variable in your site's or theme's configuration file `config.yaml` or `config.toml`. Example, with `config.yaml`:
    ```yaml
    theme: ["hugo-video", "my-theme"]
    ```
    or, with `config.toml`,
    ```toml
    theme = ["hugo-video", "my-theme"]
    ```
3. Place your video file(s) in the [page bundle](https://gohugo.io/content-management/page-bundles/) of your post.
4. In your site, use the shortcode, this way, indicating the video filename __without its extension__. If your video file is `my-beautiful-screencast.mp4`, type this:
    ```go
    {{< video src="my-beautiful-screencast" >}}
    ```
    or
    ```go
    {{< video src="my-beautiful-screencast" width="600px" >}}
    ```

### Thanks

- To [Tom McKenzie](https://github.com/grrowl), for implementing `muted`, `autoplay` and `loop` video attributes support.
- To [Olaf Haag](https://github.com/OlafHaag), [Paul Lettington](https://github.com/plett) and [Christian Mahnke](https://github.com/cmahnke), for raising and fixing some bugs.
- To [Arsenii Lyashenko](https://github.com/ark0f), for implementing `controls` disabling option and for providing the russian localization.
- To [Evgeny Kuznetsov](https://github.com/nekr0z), for implementing `height` optional attribute.

### Licence

Copyright © 2019 onwards, Nicolas Martignoni nicolas@martignoni.net.

All the source code is licensed under GPL 3 or any later version

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
