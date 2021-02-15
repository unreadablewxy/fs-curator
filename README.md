# FS-Curator

The curator is a meta-data repository that organizes your files. Designed to utilize modern filesystems to their full potential while keeping the operator in total control

### The service

![fs-curator workflow](https://user-images.githubusercontent.com/18103838/107893376-ad593880-6edf-11eb-8cfd-9b27101632ad.png)

* Makes no assumptions about nor places any demands on your workflow(s)
* Fault tolerant design that leverages OS guarantees for graceful degredation in the case of user error
* Configure for what you want, not what to do. Write 100 lines of config, it reorganizes 100K files

### Other tools

![other tools workflow](https://user-images.githubusercontent.com/18103838/107893377-ad593880-6edf-11eb-852e-33b407fc4e66.png)

* Demands your workflow adapt to its assumptions, behaves unexpectedly if violated
* Usually single point of failure, degrades terribly if corrupted
* Narrow purpose restricts the amount of compatible workflows, frequently involving repetitive list sifting

# No risk design

Rest assured the curator doesn't do anything risky or evil with your data

* No vendor lock in! Delete the curator's DB at no risk to your directory trees or your stored meta-data
* No propritary meta-data files. All meta-data are expressed as directory trees or attached via [NTFS streams](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-fscc/c54dec26-1551-4d3a-a0ea-4fa40f848eb3) or [xattrs](https://www.man7.org/linux/man-pages/man5/attr.5.html). Access them directly via `notepad` and `cli` commands, respectively
* No networking capabilities, the curator respects your privacy.
    * It uses Unix domain sockets that are literally incapable of connecting to another machines
    * For networked clients that need to access meta-data, attributes used by the curator are fully compatible with both Windows SMB and Samba ([with some config](https://www.samba.org/samba/docs/current/man-html/vfs_streams_xattr.8.html]))
* No data loss risk in the repository. Curator will never run the equivlent of `rm -rf` and or overwrite files. In fact, to regenerate a directory tree, you must delete it yourself (or the command fails)

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
