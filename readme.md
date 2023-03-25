# An unofficial SQLite Driver for YOURLS 1.9.2

This is a fork of a [fork](https://github.com/reanimus/yourls-sqlite) of the [original](https://github.com/ozh/yourls-sqlite), but now outdated SQLite driver for [YOURLS](https://yourls.org/). To my knowledge, it's the only actively maintained version, now with a readily available Docker image (thanks [@Niduroki](https://github.com/Niduroki)).

### Running in a container with Podman or Docker

If you'd like to run Yourls with this Sqlite driver in a production-ready container, you can use [Podman](https://podman.io) or [Docker](https://www.docker.com).

You can get an image from [Niduroki/docker-yourls-sqlite](https://github.com/Niduroki/docker-yourls-sqlite).

## A note on encoding

YOURLS switched to the *UTF8mb4* encoding for the official MySQL database driver for *v1.7.10*. Since SQLite uses *UTF8*, and has no support for the new character encoding format, using this unofficial driver will not allow you to create short URLs with extended characters stored as 4 Bytes, such as emojis.

### From the original README

## What

This is a custom DB layer that allows to use YOURLS with PDO + SQLite. This requires **YOURLS 1.8**, not before, not after. See [YOURLS releases](https://github.com/YOURLS/YOURLS/releases).

This is experimental, mostly to show how it should be done, ie without [hacking core file](https://github.com/YOURLS/YOURLS/wiki/Dont-Hack-Core) - see [YOURLS issue #1337](https://github.com/YOURLS/YOURLS/issues/1337) (1337, for real!).

If you notice something that doesn't work as expected, please open an issue with details on how to reproduce and wait for someone to submit a pull request to fix. If you can both submit the issue and the pull request, you're the boss!

## How

* Drop these files in `/user/`, next to your `config.php` (this is *not* a plugin)
* Load YOURLS: the first time, it will create a fresh SQlite DB in that same `user` directory
* Have fun

## FAQ

##### *Doesn't work!*
See above

##### *Will this break my existing install that uses MySQL?*
Nope! All the data stored in MySQL is untouched (you can test this driver with no SQL server running to be sure) and when you're done, simply delete (or rename) the `db.php` file and you'll get all your original data back from MySQL

## License

Do whatever the hell you want with it
