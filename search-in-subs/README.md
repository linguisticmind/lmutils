# search-in-subs

**This tool has been rewritten and moved to https://github.com/linguisticmind/search-in-subs**

---

Quickly find words in `.srt` subtitles with this command line tool.<br>
Uses [GNU sed](https://www.gnu.org/software/sed/) under the hood to search through the files.

**[Video tutorial](https://www.youtube.com/watch?v=6Q2avEWiQB8&t=10m53s)**

## Dependencies

Requires [GNU coreutils](https://www.gnu.org/software/coreutils/).

Install them on a Mac via [MacPorts](https://www.macports.org/) or [Homebrew](https://brew.sh/):

`$ sudo port install coreutils`<br>
`$ brew install coreutils`

**[MacPorts and Homebrew video tutorial](https://www.youtube.com/watch?v=vC6ykcyTzLg)**

## Installation

Add the [script](search-in-subs) to a directory on your `PATH`.

## Help

View this help on command line:

`$ search-in-subs --help`

```

  search-in-subs - search for words in subtitle files

  Requires GNU coreutils.

  search-in-subs [<options>] <search_term> ... [<options>]

  <search_term> ...           <string|regex>

                              Terms to search for in subtitle files. Can
                              be POSIX Extended Regular Expressions if
                              '-r, --regex' is set, otherwise literal text
                              strings.

                              Number and type of consecutive whitespace
                              characters is ignored, unless '-e,
                              --strict-search' is set. See there for details.

                              When multiple search terms are given,
                              statistics are calculated for matches to
                              <search_term_1> *or* <search_term_2> *or*
                              <search_term_3>, and so on, without keeping
                              track of which term was the hit. Think
                              searching for different forms or spellings of
                              the same word, variants of the same phrase etc.
                              In regex terms, they are compiled
                              into a regular expression of the form
                              (<s1>|<s2>|<s3>|...), and statistics for
                              matches to that regex are calculated.
                              If statistics on individual search terms are
                              needed, multiple searches should be run.

  Options

  -s, --search-items          <file|directory> ...
  -s=, --search-items=        <file|directory>

                              (--search)

                              Subtitle files to search. Must be .srt
                              files. If a directory is given, all .srt files
                              in that directory will be searched. (See also
                              '-x, --exclude-items'.)

                              If not set, defaults to current working
                              directory.

                              Files will be searched in the given order.

                              **Shell globbing and end of options**

                              Shell globbing patterns may be used if values
                              are passed as separate arguments (i.e. without
                              using an equals sign after the option name).

                              If setting this option right before the search
                              terms, make sure to end the argument list with
                              the end of options option (--). See more on the
                              '--' option below.

                              To pass a value starting with a hyphen (-),
                              use the equals sign after the option name.

  -x, --exclude-items         <file|directory> ...
  -x=, --exclude-items=       <file|directory>

                              (--exclude)

                              Exclude files (from those included by the '-s,
                              --search-items' option) from search. Files in
                              directories are matched by the same principle
                              as in '-s, --search-items'.

                              The order in which '-x, --exclude-items' and
                              '-s, --search-items' options are set and the
                              order of the files or directories specified
                              under '-x, --exclude-items' does not matter.

                              See also the subsection 'Shell globbing and end
                              of options' under '-s, --search-items'. Same
                              applies here.

  -v, --verbose               Print names of all files as they are being
                              searched.

  -V, --no-verbose            Disables '-v, --verbose'. This is the default
                              behavior.

  -i, --inverse               (-n, --inverse-search,
                               --invert, --invert-search,
                               --no-match, --no-match-search)

                              Print names of the files that do *not* contain
                              the search term.
                              Gives the same output as '-v, --verbose',
                              but without the matches.

  -I, --no-inverse            (-N, --no-inverse-search,
                               --no-invert, --no-invert-search,
                               --match, --match-search)

                              Disables '-i, --inverse'. This is the default
                              behavior.

  -q, --quiet                 (--quiet-search,
                               --silent, --silent-search)

                              Suppress search output: neither matches nor
                              filenames are shown as the files are being
                              searched. Useful with the '--statistics' option
                              if one only wishes to see the statistics.

  -Q, --no-quiet              (--no-quiet-search,
                               --no-silent, --no-silent-search)

                              Don't suppress search output. This is the
                              default behavior.

  -r, --regex                 (--regexp,
                               --regex-search, --regexp-search)

                              Search using POSIX Extended Regular
                              Expressions.

  -R, --no-regex              (--no-regexp,
                               --no-regex-search, --no-regexp-search,
                               --string, --string-search)

                              Search using literal strings. Disables '-r,
                              --regex'. This is the default behavior.

  -c, --match-case            (--case-sensitive)

                              Distinguish between upper and lower case
                              when searching.

  -C, --no-match-case         (--case-insensitive)

                              Search without distinguishing between upper and
                              lower case. Disables '-c, --match-case'. This
                              is the default behavior.

  -e, --strict-search         (--exact,
                               --exact-search, --strict)

                              Match whitespace strictly when searching. (See
                              '-E, --no-strict-search'.)

  -E, --no-strict-search      (--no-exact,
                               --no-exact-search, --no-strict)

                              Treat whitespace characters as interchangeable
                              when searching. The number of consecutive
                              whitespace characters will also be ignored.
                              Most importantly, this allows to treat line
                              breaks in subtitles lines the same as spaces.

                              Disables '-e, --strict-search'. This is the
                              default behavior.

                              Whitespace characters are: space, newline,
                              carriage return, horizontal tab, vertical tab
                              and form feed (POSIX ERE [:space:] character
                              class).

  --                          End of options. All arguments after this option
                              will be treated as operands.

                              Operands are non-option arguments. In
                              search-in-subs those are the <search_term>
                              arguments.
                              Thus, this option allows, for instance, to
                              start a search term with a hyphen (-).

                              See also 'Shell globbing and end of options'
                              under '-s, --search-items' for another
                              use case.

  -h, --help                  Print this help message.
                              This message also gets printed if the script
                              is run with no arguments.

  --statistics                (--stats)

                              Collect and display statistics about the
                              search.

  --no-statistics             (--no-stats)

                              Don't collect or display statistics about the
                              search. Disables '--statistics'. This is the
                              default behavior.

  --stats-compact-headers     (--statistics-compact-headers)

                              Abbreviate long headers in the statistics
                              output.

  --stats-no-compact-headers  (--statistics-no-compact-headers)

                              Don't abbreviate long headers
                              in the statistics output. Disables
                              '--stats-compact-headers'. This is the default
                              behavior.

  --stats-no-headers          (--statistics-no-headers)

                              Hide headers in the statistics output.

  --stats-headers             (--statistics-headers)

                              Hide headers in the statistics output. Disables
                              '--stats-no-headers'. This is the default
                              behavior.

  --stats-no-file-numbers     (--stats-no-file-nums,
                               --statistics-no-file-numbers,
                               --statistics-no-file-nums)

                              Hide file numbers in the statistics output.

  --stats-file-numbers        (--stats-file-nums,
                               --statistics-file-numbers,
                               --statistics-file-nums)

                              Show file numbers in the
                              statistics output. Disables
                              '--stats-no-file-numbers'. This is the default
                              behavior.

  --no-ansi-escape            (--no-ansi,
                               --plain-output, --plain)

                              Disable colorization and formatting
                              (ANSI escape sequences) in the output of
                              search-in-subs.

  --ansi-escape               (--ansi,
                               --no-plain-output, --no-plain)

                              Keep colorization and formatting
                              (ANSI escape sequences) in the
                              output of search-in-subs. Disables
                              '--no-ansi-escape'. This is the default
                              behavior.

  --message-labels            When search-in-subs prints a message, add
                              a label categorizing it as informational,
                              warning, error etc.

  --no-message-labels         Don't add labels to messages
                              printed by  search-in-subs. Disables
                              '--message-labels'. This is the default
                              behavior.

  --no-message-sources        When printing a message, don't show the name
                              of the script that issued the message.

  --message-sources           When printing a message, show the name of
                              the script that issued the message. Disables
                              '--no-message-sources'. This is the default
                              behavior.

  About

  search-in-subs is part of lmutils - collection of command line tools for
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
