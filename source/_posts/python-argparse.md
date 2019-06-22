---
title: python argparse
date: 2018-08-08 22:01:45
tags: 
	- python
	- argparse
---
# Usage
```python
import argparse
parser= argparse.ArgumentParser()
parser = argparse.ArgumentParser(description='')
parser.add_argument('data', metavar='DIR', help='path to dataset')
```
## Parameter
- prog - The name of the program (default: sys.argv[0])
- usage - The string describing the program usage (default: generated from arguments added to parser)
- description - Text to display before the argument help (default: none)
- epilog - Text to display after the argument help (default: none)
- parents - A list of ArgumentParser objects whose arguments should also be included
- formatter_class - A class for customizing the help output
- prefix_chars - The set of characters that prefix optional arguments (default: ‘-‘)
- fromfile_prefix_chars - The set of characters that prefix files from which additional arguments should be read (default: None)
- argument_default - The global default value for arguments (default: None)
- conflict_handler - The strategy for resolving conflicting optionals (usually unnecessary)
- add_help - Add a -h/--help option to the parser (default: True)
- allow_abbrev - Allows long options to be abbreviated if the abbreviation is unambiguous. (default: True)

## The add_augment() method
- name or flags - Either a name or a list of option strings, e.g. foo or -f, --foo.
- action - The basic type of action to be taken when this argument is encountered at the command line.
- nargs - The number of command-line arguments that should be consumed.
- const - A constant value required by some action and nargs selections.
- default - The value produced if the argument is absent from the command line.
- type - The type to which the command-line argument should be converted.
- choices - A container of the allowable values for the argument.
- required - Whether or not the command-line option may be omitted (optionals only).
- help - A brief description of what the argument does.
- metavar - A name for the argument in usage messages. 有助于提醒用户，该命令行参数所期待的参数，如 metavar="mode"
- dest - The name of the attribute to be added to the object returned by parse_args().

# Reference
[Python 命令行解析](https://blog.csdn.net/itlance_ouyang/article/details/52489674)
[python.org](https://docs.python.org/3/library/argparse.html)