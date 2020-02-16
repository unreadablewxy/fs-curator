# Curator

The curator is a file sorting automation daemon. It is meant to serve as a **part** of a comprehensive data management solution.

## What's in the box

The curator deals in files and directories. It monitors directories for changes and presents files where they need to based on a processing pipeline you define.

* Detects duplicate files as they are found
* Groups "related" files that were added together
* Trigger commands on files (un-archiving, re-encoding, etc)
* Create multiple directories of files without duplicating data (via hard links)
* Integrated ffmpeg based thumbnailing capability
* Easy to understand & write ini configurations

## How it works

* Directories are nominated as `hopper`s. Which are then watched for rename / move events. As well as closed for writing events for files. 
* The file or directory is then offered to `transform`s which performs changes in a colocated temporary directory.
* Transforms are repeated until no further transforms are possible.
* Files are then linked into a centralized "collection" directory, we take this opportunity to dedupe the new file and assign it a numeric ID for global ordering.
    * This mono-collection allows us to use your filesystem to its full potential. Granting the ability to do efficient b-tree based searches without meta-data files.
* The resulting files are offered to `store`s. Which may choose to create links or copies.
