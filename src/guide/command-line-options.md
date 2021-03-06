---
title: Command Line Options
type: guide
order: 4
---

Besides general Symfony Console application command line options, Infection has its own ones.

### `--filter`

If you're only interested in mutating a subset of your files, you can pass a `--filter` option containing any value, supported by Symfony Finder's `name()` method.

``` bash
infection --filter=Mailer.php
```

This in no way restricts the initial Infection check on the overall test suite which is still executed in full to ensure all tests are passing correctly before proceeding.


### `--threads`

If you want to run tests for mutated code in parallel, set this to something > 1. It will **dramatically speed up** mutation process. Please note that if your tests somehow depends on each other or use database, this option can lead to failing tests which give many false-positives results. 

### `--test-framework`

This is a name of the Test framework to use. Currently Infection supports `PhpUnit` and `PhpSpec`.

>Feel free to request a new test framework to be supported out of the box in Github's issues.

### `--only-covered`

Run the mutation testing only for covered by tests files.

### `--show-mutations`

Show colorized diffs of mutated files to the console.

> Please note that all mutations are logged to the `infection-log.txt` log file as well.

### `--min-msi`

This is a minimum threshold of Mutation Score Indicator (MSI) in percentage. Can be used with CI server to automatically control tests quality.

> Read more about [using Infection in CI server](./using-in-ci.html)

### `--min-covered-msi`

This is a minimum threshold of Covered Code Mutation Score Indicator (MSI) in percentage. Can be used with CI server to automatically control tests quality.

### `---formatter`

This is a name of console output formatter. Possible values are: `dot`, `progress`. Default is `dot` formatter.