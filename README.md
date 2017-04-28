# lastfm vk.com Downloader

This is a tool for downloading your top (overall or for last 12 months or whatever) lastfm tracks
from <https://vk.com>.

## How To

You must have *w3m* installed. It's a text based web browser. Look in your distro's repos.
Get your last.fm API key at <https://www.last.fm/en/api>. Also you need a registered account
on <https://vk.com>.
Also you need javascript interpreter that provides *js* executable.

```shell
$ pip install --user lastfm_vk_download  # make sure ~/.local/bin is in your $PATH
$ w3m vk.com  # login here so that w3m stores your account's cookies, then exit by pressing q

$ lastfm_to_json --help  # to get help
$ export LASTFM_API_KEY="your_api_key_goes_here"  # or you can use --api-key parameter
$ lastfm_to_json --username cocacooler --num-tracks 100 --skip-tracks 10 --period overall cocacooler.json
# this will take a few second and will list
# top tracks 11 to 110 from https://www.last.fm/user/cocacooler/library/tracks
# to ./cocacooler.json

$ download_from_vk --help  # to get help
$ mkdir cocacooler_top_tracks
$ download_from_vk cocacooler.json cocacooler_top_tracks
# this will last for a long time because otherwise vk.com will ban you
# and will download tracks from cocacooler.json
#
# when it finishes, even with error, if any tracks from the list were not downloaded
# they will be listed in cocacooler_top_tracks/failed_to_dl.json

$ download_from_vk cocacooler_top_tracks/failed_to_dl.json cocacooler_top_tracks  # try again
```

## Notes

This program will sometimes get temporarily banned from using <vk.com> audio search.
If you see a lot of `Didn't find 'groupname' - 'songname'. It's possible that vk.com temporarily banned this ip or username from audio seach.` then that's probably what happened.
Just stop the program and wait some time.