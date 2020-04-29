# Curator

On the surface this project is a high performance small media deduplicator. Able to spot duplicates against a collection of hundreds of thousands in a fraction of a second without the need to keep meta-data files separate to your data.

Dig deeper and the project reveals itself for what it actually is. A different way to use your file system, perhaps to its full potential. To this end, we ask "what if we treated files as more than just a blob of data identified by its path?". What if instead of paths, files are identified by any number of arbitrary meta-data? Which at a whim, may be used to create whatever directory structure one's workflow requires, based on rules instead of manual intervention? Similar to how SQL databases creates materialized views, optimal to a particualr workflow.

To this end, the program maintains a `mono-collection`. A centralized location that serves as the authority of data and metadata for all the files it manages. Then based on rules and meta data, the service selects files and links them to other locations in your filesystem creating directory structures that suits a particular workflow.

Under this vision
* Directory structure no longer needs to be planned out beforehand.
* Rule based file sorting produces fewer placement inconsistencies than its manual counterpart.
* If directory structure requirements change, or more than one directory structure is required, all that's required is to change a rule and the daemon take care of the rest.

## What's in the box

The curator deals in files and directories. It monitors directories for changes and presents files where they need to based on a processing pipeline you define.

* 100% native program written in C++20 with the resource efficiency you'd expect
* Watches directories for files and directories to ingest files
* Incrementally dedupe files as they are added
* Murmur3 hash based binary level deduplication
* PHash perceptual deduplication
* Integrated FFMPEG thumbnailer
* Groups "related" files that were added together
* Regex based renaming capabilities (with named capture groups)
* Transform files by invoking other programs (un-archiving, re-encoding, etc)
* Rules based directory tree generation
* Hard links support to keep file contents synced & reduce duplication
* Easy to understand & write ini configurations
* A durable meta-data design (literally no SQL) using human operable directory trees & xattrs

[See the configuration manual](https://github.com/unreadablewxy/fs-curator/wiki) for how it works
