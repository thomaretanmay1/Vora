Vora

A private, account-free streaming client for Android.

Vora is a self-contained application for streaming video and audio from five sources in a single interface: YouTube, SoundCloud, media.ccc.de, PeerTube, and Bandcamp. The interface follows the conventions of a modern video platform and prioritizes YouTube as the primary source, while providing equal access to the other four. Vora ships with no advertisements, no analytics, and no account system. Every subscription, playlist, history entry, and setting lives on the device and nowhere else.

---

Overview

Vora is a portable streaming client designed for people who want the convenience of a unified media player without the data collection, advertising, and account requirements of the platforms it accesses. It runs entirely on the device, fetches only what it needs to play, and never transmits usage information to any server of its own. The application is released as an APK and can be installed without a browser, a server, or a login.

The application is built around a small number of principles:

· Privacy by default. No accounts, no telemetry, no advertising identifiers, no third-party scripts or fonts loaded at runtime.
· Local-first data. Subscriptions, history, playlists, bookmarks, download records, resume positions, settings, and the queue are stored in the device's local storage and can be exported or erased by the user at any time.
· Five sources, one player. Every service is treated as a first-class source with its own tabs, search, and content type. The same player, the same gestures, and the same controls work everywhere.
· Graceful degradation. When a source refuses direct streams, Vora falls back to the source's own embeddable player or to an alternative route rather than failing silently or blocking the application.

---

Supported Sources

YouTube. The primary source. Kiosks include Live, Music, Gaming, Podcasts, and Movies. Search, channels, playlists, comments, and a subscription feed are supported.

SoundCloud. Audio-only streaming with track search, user pages, playlists, and the official widget as a fallback for playback.

media.ccc.de. Conference recordings and talks, with dedicated Recent and Conferences kiosks and search.

PeerTube. Any federated PeerTube instance. The default is framatube.org, and the instance can be changed in Settings.

Bandcamp. Bandcamp Weekly radio shows and featured releases, plus individual album and track pages when opened by link.

---

Features

Playback

· Adaptive video and audio merging for sources that deliver picture and sound separately, with automatic drift correction and a fast-start strategy for slow connections.
· HLS playback for live broadcasts and completed livestreams whose manifest is still served.
· Resume playback from the last position, with a single tap to start over.
· Background playback that continues when the application is not in the foreground.
· Audio-only mode that stops video decoding to save battery and data.
· Data saver that caps the requested quality.
· Per-service quality preference, so each source can be tuned independently.

Player controls and gestures

· Double-tap to seek forward or backward.
· Vertical drag on the left half of the picture for brightness, on the right half for volume.
· Pinch to zoom the picture freely between 100% and 300%, with the level remembered for the next video.
· Long-press on the picture to temporarily increase playback speed.
· Picture-in-picture, a draggable popup player, and a mini player that keeps the running stream in the document.
· Fullscreen, theatre mode, mirror, rotation, and frame-by-frame stepping.
· Keyboard shortcuts on desktop and hardware-key support through the Media Session API.

Queue and playback options

· Play next, add to queue, shuffle, repeat one, and repeat all.
· A video carries its Up next list as the queue, so autoplay and next/previous work without manual setup.
· The queue can be saved as a local playlist.
· Autoplay, shuffle, and repeat are application-wide settings that are remembered between sessions.

Captions

· Automatic caption loading when a stream has a track.
· Caption appearance customization: size, text colour, box opacity, font, and edge style.
· Captions are rendered by the application itself, so they work in the page, in the popup player, and in fullscreen alike, for WebVTT, SRV1 XML, and timedtext v3 formats.

Audio

· Eight-band equalizer with preamp, bass shelf, and reverb.
· Equalizer presets (Flat, Bass boost, Treble boost, Vocal, Rock, Jazz, Electronic, Podcast, Night) and per-band manual adjustment.
· Equalizer runs on the device's audio graph and is only applied to streams the application can legitimately route.

Downloads

· Video-only, audio-only, and subtitle downloads with accurate file extensions that match the contained codec.
· When the source offers video and audio separately, Vora merges them into a single file via the local helper when one is available, and otherwise saves both files with clear labels so the sound is never left behind.
· Downloaded items open in a dedicated tab with the same player and nothing else.

Content organization

· Account-free subscriptions to channels from any of the five sources.
· Subscription import and export in a small, portable JSON format compatible with the NewPipe schema.
· Feed groups for organizing subscriptions into tabs such as Music or News.
· Local playlists, bookmarks for remote playlists, and a watch history with resume positions.
· A What's New feed built from subscriptions.
· On-device statistics showing plays per service, top channels, and watch time over the last seven days.

Customization

· Theme: Light, Dark, Black (OLED-friendly), or Auto (follow the system).
· Accent colour with eight options that apply to buttons, switches, focus rings, and the application mark.
· Font scaling from 85% to 130%.
· Corner style (sharp, rounded, soft) and layout density (comfortable or compact).
· Toggle for showing or hiding thumbnails, quality labels, service badges, and kiosk chips.
· Reduce motion option.
· Configurable default playback speed, seek step, long-press speed, default resolution, and default zoom mode.
· Ambient glow around the player, with three intensity levels or an option to turn it off entirely.

Well-being

· Watch-time tracking that counts only real playing time, never paused, buffering, or hidden playback.
· Optional daily and weekly watch limits with a soft wall that pauses playback and offers fifteen more minutes, the rest of the day, or a stop.
· The whole watch-time record is stored on the device and can be cleared at any time.

Help and transparency

· A first-run guide that explains the sources, the player, and the privacy model.
· A full feature list and a plain-language privacy statement, both reachable from the application at any time.

---

Privacy

Vora does not collect, store, transmit, or sell any personal information. There is no account system, no analytics service, no crash reporter, and no advertising identifier. The application does not load third-party scripts, fonts, or trackers at runtime. All code runs locally.

What stays on the device:

· Subscriptions, feed groups, playlists, bookmarks, and download records.
· Watch history, search history, and resume positions.
· Settings and the play queue.
· A cache of feeds, searches, and thumbnails.

What leaves the device:

· Only the requests needed to display content: a request to a source when a feed, search, channel, or video is opened, and requests for thumbnails and media from the source's own hosts. The privacy policies and terms of each source apply to those requests, exactly as they would in a browser.

The full privacy statement, including what is never collected, is available inside the application and can be read before or after use.

---

How It Works

Vora does not operate its own server. Content is fetched from the sources themselves through one of two routes, chosen automatically at startup:

Local helper. When the application is run alongside its companion extraction helper, the helper fetches, resolves, and merges streams on the device or on the local machine. This route provides the widest quality selection, full merging of adaptive streams, and the best reliability across all five sources.

On-device extraction. When no helper is available, the application extracts content directly in the client using public, CORS-enabled endpoints: the official APIs for media.ccc.de and PeerTube, a public Invidious or Piped bridge for YouTube, and the public SoundCloud and Bandcamp endpoints. This route supports every source that publishes a CORS-enabled API and falls back to the source's own embeddable player when a stream cannot be pulled directly.

The user can change the YouTube bridge, the PeerTube instance, and the source address at any time from Settings. The application remembers the last working configuration and re-discovers the local helper automatically on each start.

---

Installation

Vora is distributed as an Android APK. Install the APK on the device and open the application. No account, no browser, and no server are required. The first launch probes the available sources, selects the best route for the device, and explains what is available in a single screen. Nothing needs to be configured unless the user wants to change it.

---

Building

The application is a single-file front end and does not require a build step to run. The full source is included in the APK packaging. If you want to inspect, modify, or rebuild the application, you can open the source file in a text editor and package it with the tool of your choice.

---

Licence

Vora is released under the GNU General Public License v3.0 or later (GPL-3.0-or-later). You are free to use, study, share, and modify the application under the terms of the licence. The full licence text is available at the Free Software Foundation's website.

Copyright © 2026 Tanmay Thomare. All rights reserved.

---

Credits

Vora is developed by Tanmay Thomare.

The extraction logic is a faithful port of the NewPipe extractor's service model, adapted for on-device use and for the five sources Vora supports. The interface, the player, and the customization system are Vora's own.

Vora does not host content. All media is fetched from the sources named in this document. Vora is not affiliated with YouTube, SoundCloud, media.ccc.de, PeerTube, or Bandcamp.

---

Disclaimer

Vora is a client for publicly accessible media. It does not host, mirror, or redistribute any content. Users are responsible for complying with the terms of service of each source and with the laws of their jurisdiction. The application is provided as-is, without warranty of any kind. See the GPL-3.0-or-later for the full warranty and liability terms.