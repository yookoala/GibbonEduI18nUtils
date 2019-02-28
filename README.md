# i18n Inspection Utilities

Inspect i18n of GibbonEdu project.


## `genlocale`

The bash tool [`bin/genlocale`](bin/genlocale) can be used to generate
POT tranlsation template file from live source code. It can then create
or update translation file from existing PO translation file.

This tool is for cleaning up old translation files from outdated
translation string (i.e. `msgId`), extracted comments and function line
information.

### Usage

```
./bin/genlocale -i ../i18n/en_GB/LC_MESSAGES/gibbon.po -o ./gibbon.po -s ..
```

**Note:** this tool will generate an intermediate POT file from the live
source code. The intermediate file will not be removed or rewritten.
You'd need to remove that file if your source code has updated.

To understand all the options, please see Usage by this command:

```
./bin/genLocale -h
```


## `gendiff`

The python3 tool [`bin/gendiff`](bin/gendiff) can be used to generate
`msgId` differences between a POT translation template file with a PO
translation file.

This tool is for reviewing outdated translation in current PO file as
compare to the live source code. You'd need to generate a POT file from
live source code. You may use the `genlocale` tool in this repository.
Or you may call `xgettext` directly.

### Usage

```
./bin/gendiff POT_FILE PO_FILE | tee diff.txt
```
