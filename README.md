# FS-Curator

![curator-pipeline](https://user-images.githubusercontent.com/18103838/83365303-fa01e100-a35b-11ea-9175-a102e20c2032.png)

The curator is a meta-data repository that sorts your files. Designed to utilize modern filesystems to their full potential while keeping the operator in control. With its help:
* Deduplication can be done incrementally, using less resources
* Directory structures no longer needs to be planned out beforehand and can be re-generated to adapt to changing workflows
* Rule based file sorting leads to fewer placement inconsistencies

## No risk design

Rest assured the curator doesn't do anything risky or evil with your data

* No vendor lock in! Delete the curator's repository at no risk to your directory trees or your stored meta-data
* No propritary meta-data files. All meta-data are expressed as directory trees or attached via [NTFS streams](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-fscc/c54dec26-1551-4d3a-a0ea-4fa40f848eb3) or [xattrs](https://www.man7.org/linux/man-pages/man5/attr.5.html). Access them directly via `notepad` and `bash` commands, respectively
* No networking capabilities, the curator respects your privacy. Which is why it uses Unix domain sockets that are literally incapable of connecting to another machines
* No data loss risk in the repository. Curator will never run the equivlent of `rf -rm` and or overwrite files. In fact, to regenerate a directory tree, you must delete it yourself (or the command fails)

# What exactly is in the box

* 100% native program written in C++20 with the resource efficiency you'd expect
* Easy to understand & write ini configurations
* Monitors multiple paths for directories & files to injest
* Incrementally dedupe files as they are added
* Murmur3 hash based binary level deduplication
* PHash perceptual deduplication for images
* Integrated FFMPEG thumbnailer for images & videos
* Groups "related" files and maintain file ordering
* Regex based renaming capabilities (with named capture groups)
* Transform files by invoking other programs (un-archiving, re-encoding, etc)
* Rules based directory tree generation
* Hard links support to keep file contents synced & reduce duplication

[See the configuration manual](https://github.com/unreadablewxy/fs-curator/wiki) for how it works
