# Config Curator

[![npm](https://img.shields.io/npm/v/@rxrc/curator.svg)](https://www.npmjs.com/package/@rxrc/curator)
[![github](https://img.shields.io/badge/github-rxrc/curator-blue.svg)](https://github.com/rxrc/curator)
[![David](https://img.shields.io/david/rxrc/curator.svg)](https://david-dm.org/rxrc/curator)
[![CircleCI](https://img.shields.io/circleci/project/github/rxrc/curator.svg)](https://circleci.com/gh/rxrc/curator)

## Description

**CLI tool for installing static configuration.**

- **Idempotent:** syncs directories, copies files,
  creates system links, deletes paths, and sets access permissions to ensure
  the system will be in a consistent state after each run.
- **Declarative**: all operations are defined
  in a manifest file with a simple syntax.
- **Flexible**: operations may be limited only to specific hosts
  or only when specific packages are installed,
  additionally, since the manifest is written in JavaScript,
  it may include arbitrary logic.
- **Minimal:** written in Node.js using only the standard library
  and a few system calls.
- **Secure:** no additional third party dependencies (except `rsync`)
  and a small codebase for easy review.
  (Safe to run with `sudo` to install system files.)
- **Fast:** uses maximal concurrency for all file operations.

**To try it out:**

1. Clone this repo.
2. Run `npm install`.
3. Run `npm test`:
   This will install the configuration
   defined in `test/manifest.js` to `test/dest`.

## Requirements

- Linux or macOS with [rsync] installed.
- [Node.js] version 8 or above.

For conditional configuration based on installed packages,
the following package managers are supported:

- [Pacman]
- [Homebrew]
- [dpkg]

[dpkg]: https://help.ubuntu.com/lts/serverguide/dpkg.html
[Homebrew]: https://brew.sh/
[Node.js]: https://nodejs.org/
[Pacman]: https://www.archlinux.org/pacman/
[rsync]: https://rsync.samba.org/

## Installation

1. Add this as a development dependency to your project using [npm] with

    ```
    $ npm install --save-dev @rxrc/curator
    ```

2. Add a [script][npm scripts] to your `package.json` with `"curator": "curator"`
   so you may run this with

    ```
    $ npm run curator
    ```

[npm]: https://www.npmjs.com/
[npm scripts]: https://docs.npmjs.com/misc/scripts

## Usage

Create a `manifest.js` file to define the configuration
and run the `curator` command to install the configuration.

- The location of the manifest file may be passed as the first argument,
  otherwise it looks for `manifest.js` in the current working directory.
- The environment variables `CURATOR_IO` and `CURATOR_PKG` may be set
  to override the `io` and `pkg` values from the manifest.

## Similar Software

This is the successor to my original configuration tool written in Ruby:
https://github.com/razor-x/config_curator.

GitHub maintains an unofficial guide to dotfiles: https://dotfiles.github.io/.

## Contributing

Please submit and comment on bug reports and feature requests.

To submit a patch:

1. Fork it (https://github.com/rxrc/curator/fork).
2. Create your feature branch (`git checkout -b my-new-feature`).
3. Make changes.
4. Commit your changes (`git commit -am 'Add some feature'`).
5. Push to the branch (`git push origin my-new-feature`).
6. Create a new Pull Request.

## License

This npm package is licensed under the MIT license.

## Warranty

This software is provided by the copyright holders and contributors "as is" and
any express or implied warranties, including, but not limited to, the implied
warranties of merchantability and fitness for a particular purpose are
disclaimed. In no event shall the copyright holder or contributors be liable for
any direct, indirect, incidental, special, exemplary, or consequential damages
(including, but not limited to, procurement of substitute goods or services;
loss of use, data, or profits; or business interruption) however caused and on
any theory of liability, whether in contract, strict liability, or tort
(including negligence or otherwise) arising in any way out of the use of this
software, even if advised of the possibility of such damage.
