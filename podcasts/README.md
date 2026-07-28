# Podcast Production Workspace

This directory contains podcast source and output files. Jekyll does not publish this directory.

## Structure

```text
podcasts/
  getting-started-series/
    <episode-name>/
      src/
      mp4/
  pcb-build-it-series/
    <episode-name>/
      src/
      mp4/
  pcb-to-layout-series/
    <episode-name>/
      src/
      png/
      gif/
      mp4/
  shared/
```

- `getting-started-series/` contains introductory Fusion, architecture, and documentation episodes.
- `pcb-build-it-series/` contains detailed PCB and supporting build episodes.
- `pcb-to-layout-series/` contains broader end-to-end discussions that connect Fusion hardware, software, installation, and layout operation.
- Episode sources start under `src/`, and completed videos use `mp4/`.
- File-type folders such as `jpg/`, `png/`, `gif/`, `mp3/`, and `mp4/` hold episode media.
- `shared/` contains material that is not owned by one series or episode.

Published post articles remain in `_posts/`. Published posters and optional audio downloads remain in `assets/podcasts/`. Article download links may point to episode sources in this workspace.