# Browser debug utilities

This project contains several scripts that make the process of debugging browser
engines much easier (some special cases excepted). The hallmark feature of this
project is its integration with `uncss` to automate the process of removing
unused CSS rules.

## Overview

- `bdu-outline-scripts`: replaces all inline script elements with references to
  outline script files.
- `bdu-outline-styles`: replaces all inline style elements with references to
  outline style files.
- `bdu-replace-outlined-styles`: deletes all outlined styles and inserts the
  contents of STDIN at the top of the document.
- `bdu-prepare`: automatically runs `bdu-outline-scripts` and
  `bdu-outline-styles`, then pipes the output of `uncss` into
  `bdu-replace-outlined-styles` to remove all unused CSS rules.

## Dependencies

This project requires `composer` and `npm` to be available, and both of their
respective bin directories should be in your PATH environment variable.
Additionally, PHP 7.2 or greater is required.

## Installation

```bash
npm install -g prettier uncss
composer global require clayfreeman/browser-debug-utils
```

## Usage

1. Create your minimum viable test case using the inspector in your favorite
   browser (e.g., delete all unnecessary elements and external resources).
2. Save the modified page in a way that is completely accessible offline.
3. Run the aggregate script, `bdu-prepare /path/to/index.html`, or any of the
   other scripts provided by this project.
