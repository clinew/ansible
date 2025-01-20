# Troubleshooting

## `yt_dlp.networking.exceptions.HTTPError: HTTP Error 403: Forbidden`
Adding the arguments `--extractor-args "youtube:player-client=tv"` as per [this comment](https://github.com/yt-dlp/yt-dlp/issues/11868#issuecomment-2585533699) works around the issue as of 2025 Q1.
