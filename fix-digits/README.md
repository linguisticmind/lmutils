# fix-digits

Adds leading zeros to numbered files to avoid the sort order problem:

| Before       |     | After  |
| ------------ | --- | ------ |
| <pre>1 - test&#13;10 - test&#13;2 - test&#13;3 - test&#13;4 - test&#13;5 - test&#13;6 - test&#13;7 - test&#13;8 - test&#13;9 - test</pre> | `→` | <pre>01 - test&#13;02 - test&#13;03 - test&#13;04 - test&#13;05 - test&#13;06 - test&#13;07 - test&#13;08 - test&#13;09 - test&#13;10 - test</pre>

**[Video tutorial](https://www.youtube.com/watch?v=6Q2avEWiQB8&t=28m19s)**

## Dependencies

Requires [GNU coreutils](https://www.gnu.org/software/coreutils/).

Install them on a Mac via [MacPorts](https://www.macports.org/) or [Homebrew](https://brew.sh/):

`$ sudo port install coreutils`<br>
`$ brew install coreutils`

**[MacPorts and Homebrew video tutorial](https://www.youtube.com/watch?v=vC6ykcyTzLg)**

## Installation

Add the [script](fix-digits) to a directory on your `PATH`.

## Help

View this help on command line:

`$ fix-digits --help`

```

  fix-digits - add leading zeros to numbers in filenames

  fix-digits [<options>] <file> ... [<options>]

  <file> ...                      Files to rename. If none given, the script
                                  acts on all files in the current working
                                  directory (that match the '--head' and
                                  '--tail' regexes, see below).

  Options

  --head                          <regex>

                                  Regex for the part preceding digits.
                                  Default value: '^'.
                                  Regex flavor is POSIX Extended Regular
                                  Expressions.

  --tail                          <regex>

                                  Regex for the part following digits.
                                  Default value: ' - .*$'.
                                  See '--head' for regex flavor.

  -r, --rename                    (--run)

                                  Rename files. If unset, the process is
                                  simulated. See '-s, --simulate'

  -s, --simulate                  (-R, --no-rename,
                                   -d, --dry-run)

                                  Preview new filenames without renaming
                                  files. Disables '-r, --rename'. This is
                                  the default behavior.

  --                              End of options. All arguments after this
                                  option will be treated as operands.
                                  Operands are non-option arguments. In
                                  fix-digits those are the <file> arguments.
                                  This option allows to start those arguments
                                  with a hyphen (-).

  -h, --help                      Print this help message.

  --no-ansi-escape                (--no-ansi,
                                   --plain-output, --plain)

                                  Disable colorization and formatting
                                  (ANSI escape sequences) in the output
                                  of fix-digits.

  --ansi-escape                   (--ansi,
                                   --no-plain-output, --no-plain)

                                  Keep colorization and formatting
                                  (ANSI escape sequences) in the
                                  output of fix-digits. Disables
                                  '--no-ansi-escape'. This is the default
                                  behavior.

  --message-labels                When fix-digits prints a message, add a
                                  label categorizing it as informational,
                                  warning, error etc.

  --no-message-labels             Don't add labels to messages
                                  printed by  fix-digits. Disables
                                  '--message-labels'. This is the default
                                  behavior.

  --no-message-sources            When printing a message, don't show the
                                  name of the script that issued the message.

  --message-sources               When printing a message,
                                  show the name of the script
                                  that issued the message. Disables
                                  '--no-message-sources'. This is the default
                                  behavior.

  --rename-in-alphabetical-order  Rename files in alphabetical order,
                                  i.e. with non-zero prefixed numbers out
                                  of order.

                                  (This does not affect the resulting
                                  filenames, only the order in which the
                                  renaming is happening.)

  --rename-in-natural-order       Rename files in natural order, i.e. with
                                  numerical order respected.

                                  Disables
                                  '--rename-in-alphabetical-order'. This is
                                  the default behavior.

                                  (This does not affect the resulting
                                  filenames, only the order in which the
                                  renaming is happening.)

  About

  fix-digits is part of lmutils - collection of command line tools for
  language learning and more.
  lmutils are hosted at https://github.com/linguisticmind/lmutils

  Written by Alex Rogers (linguisticmind).

  Linguistic Mind - a language learning tools, tutorials and resources hub

  https://linguisticmind.github.io

```

## License

[GNU General Public License v3.0](LICENSE)

## Support Linguistic Mind

Patreon: https://patreon.com/linguisticmind
