git-media-test
==============

A test run of the git-media project. https://github.com/schacon/git-media

Installation of git-media
=========================

To install git-media on a development machine, follow these steps in a terminal window.

```bash
$ sudo gem install git-media
$ git config --global filter.media-clean "git-media filter-clean"
$ git config --global filter.media-smudge "git-media filter.smudge"
```

If you do not want to register the git-media filters globally, you will have to run the filter creation commands for all new repositories you create, or any repositories that you pull down. 

Note: Not setting the filter for an existing repo will not prevent git-media from fetching the files from the remote location. However, once the files are fetched, they will appear as "modified", as the hash contained within the file is replaced with the actual file contents. 

Configuration of git-media
==========================

git-media will most likely have to be configured for each repo on which you use it. The config contains which files should be filtered through git-media, and where they should be stored.

Filters
-------

When within a repository's directory, create a `.gitattributes` file if there is none. The example below uses `.ext` as an example file extension.

```bash
$ echo "*.ext filter=media -crlf" > .gitattributes
```

Remote Storage
--------------

You can then set up a storage location for the media -- we will most likely be using S3 for this. For instructions on how to set up other storage types, consult the [README](https://github.com/schacon/git-media) file for the git-media project.

An example entry in `repo-directory/.git/config` is below.

```
[git-media]
    transport   = s3
    s3bucket    = bucket-name
    s3key       = access-key
    s3secret    = secret-key
```
