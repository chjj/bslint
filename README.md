# BSLint

A zero-dependency package which vendors [ESLint][eslint] and all of its
dependencies for security and simplicity. In other words, it's ESLint without
the BS (or with it, depending on your point of view).

BSLint follows the same versioning scheme as eslint: e.g. `bslint@5.11.1`
should be equivalent to `eslint@5.11.1`.

## Reasoning

BSLint is simply a snapshot of the official eslint NPM package. It was
specifically created for the [bcoin] development cycle. Bcoin is a
cryptocurrency project whose devs and users are particularly target-able for
certain kinds of package attacks like the one seen on the `event-stream`
package. As such, we seek to minimize the NPM attack surface.

### Why not use shrinkwrap?

Bundling the dependencies directly allows one to clone directly from github
without having to run `npm install`. We are aiming to minimize reliance on NPM
altogether.

### Why not bundle it?

ESLint is difficult to bundle into a single file due to its use of dynamic
requires. [bpkg] can currently bundle _some of it_ into a single file with
[some minor changes][patch], but until someone takes the time to truly rid the
entire codebase of all dynamic requires, this is the best we can do.

## Usage

Note that this module will provide the `eslint` command. This will conflict
with the regular `eslint` install.

``` bash
$ eslint -h
```

## License

ESLint License

```
Copyright JS Foundation and other contributors, https://js.foundation

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

BSLint License

```
This software is licensed under the MIT License.

Copyright (c) 2018, Christopher Jeffrey (https://github.com/chjj)

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

[eslint]: https://eslint.org/
[bcoin]: https://github.com/bcoin-org
[bpkg]: https://github.com/bpkg
[patch]: https://gist.github.com/chjj/b2329e9c44bc8be4b5e7df8480642059
