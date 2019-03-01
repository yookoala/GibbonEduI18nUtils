# i18n Inspection Utilities

Inspect i18n of GibbonEdu project.


**Table of Content**

* [i18n Inspection Utilities](README.md#i18n-inspection-utilities)
  * [genlocale](README.md#genlocale)
	 * [Prerequisites](README.md#prerequisites)
	 * [Usage](README.md#usage)
  * [gendiff](README.md#gendiff)
	 * [Prerequisites](README.md#prerequisites-1)
		* [Python 3](README.md#python-3)
		* [venv (Optional)](README.md#venv-optional)
		* [polib](README.md#polib)
	 * [Usage](README.md#usage-1)


## `genlocale`

The bash tool [`bin/genlocale`](bin/genlocale) can be used to generate
POT tranlsation template file from live source code. It can then create
or update translation file from existing PO translation file.

This tool is for cleaning up old translation files from outdated
translation string (i.e. `msgId`), extracted comments and function line
information.

### Prerequisites

You'd need to run this on an OS with a `bash` shell environment.
The following CLI softwares would need to be in it:

* xgettext
* msgmerge
* perl (version 5)
* sed
* find

Most, if not all, of these tools come with a stock installation
of Linux or macos. If you're using Windows, please use a Linux VM
or [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

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

### Prerequisites

#### Python 3

The tool is written in Python 3. So naturally you'd need to
[install it](https://www.diveinto.org/python3/installing-python.html).

#### `venv` (Optional)

It is recommended to isolate your environment with
[`venv`](https://docs.python.org/3/library/venv.html). To start your
own isolated python3 environment:

```
python3 -m venv .venv
```

You'd need to activate this environment before anything you want to do
with `pip3` and `./bin/gendiff`. To activate your venv environment
(for `bash`):

```
. .venv/bin/activate
```

#### `polib`

You'd need to install the [`polib`](https://pypi.org/project/polib/)
library. You may install it with [`pip3`](https://pypi.org/project/pip/).

```
pip3 install -r requirements.txt
```

### Usage

```
./bin/gendiff POT_FILE PO_FILE | tee diff.txt
```
