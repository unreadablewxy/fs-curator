# Curator

The curator is a file sorting automation daemon. It is meant to serve as a **part** of a comprehensive data management solution.

## What's in the box

The curator deals in files and directories. It monitors directories for changes and presents files where they need to based on a processing pipeline you define.

* Watches directories for files and directories to ingest based on rules you configure
* Incrementally dedupe files as they are added
* Groups "related" files that were added together
* Trigger commands on files (un-archiving, re-encoding, etc)
* Create multiple directories of files without duplicating data (via hard links)
* Integrated ffmpeg based thumbnailing capability
* Easy to understand & write ini configurations
* A durable meta-data design that stores the data on the files with xattrs so it is hard to get the two desynced

[See the configuration manual](https://github.com/unreadablewxy/fs-curator/wiki) for how it works
