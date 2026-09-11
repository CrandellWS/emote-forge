# Emote Forge

Browser-only emote converter. Drop a JPEG, PNG or GIF and get platform-ready files; nothing is uploaded, everything runs in your browser.

Live: https://crandellws.github.io/emote-forge/

| Preset | Size | Format | Limit |
|---|---|---|---|
| MyPrize | 112×112 | WebP (animated WebP for GIFs) | 40 KB |
| Kick | 500×500 | PNG, or GIF when animated | 1 MB |
| Discord | 128×128 | PNG, or GIF when animated | 256 KB |

How it fits the limit: WebP quality is searched down until the file fits; animated GIF output tries a few palette qualities; if an animation still will not fit, frames are thinned (1 in 2, 1 in 3, ...) with timing preserved, and the card says so.

Animated GIF decoding uses the browser's built-in `ImageDecoder` (Chrome, Edge). In other browsers the first frame is used. Animated WebP is muxed in-page from natively encoded frames (RIFF/VP8X/ANIM/ANMF), no WASM. GIF encoding: [gif.js](https://github.com/jnordberg/gif.js) (MIT), vendored in `lib/`.

Test hook: `index.html?src=samples/test-anim.gif&auto=1`.
