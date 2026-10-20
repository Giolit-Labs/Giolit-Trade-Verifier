# Third-party notices

The Giolit Trading Risk Verifier includes the following open-source components: two in its front-end library
(`libgiolit_frontend.so`), and the fonts of its PDF documents (`share/giolit/fonts`). Their copyright notices and
licenses follow. Everything that decides a constraint --
the model builder, the provers, the search and the replay -- is Giolit's own.

| Component | Copyright | License | Used for |
|---|---|---|---|
| pugixml 1.14 | Arseny Kapoulkine | MIT | reading FIX Orchestra and FIXatdl files |
| LLVM / Clang 18 | LLVM project contributors | Apache 2.0 with LLVM exceptions | importing strategies and risk controls written in C++ |
| Geist, Geist Mono | The Geist Project Authors | SIL Open Font License 1.1 | the text and code of certificates and reports |
| Plus Jakarta Sans | The Plus Jakarta Sans Project Authors | SIL Open Font License 1.1 | the titles of certificates and reports |

## pugixml

```
Copyright (c) 2006-2023 Arseny Kapoulkine

Copyright (c) 2006-2023 Arseny Kapoulkine

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
```

## LLVM / Clang

LLVM and Clang are distributed under the Apache License v2.0 with LLVM Exceptions
(https://llvm.org/LICENSE.txt). The verifier uses Clang to parse the C++ sources a binding names (never to run them).

## Fonts: Geist, Geist Mono, Plus Jakarta Sans

Copyright 2024 The Geist Project Authors (https://github.com/vercel/geist-font); Copyright 2020 The Plus Jakarta
Sans Project Authors (https://github.com/tokotype/PlusJakartaSans). The fonts are licensed under the SIL Open Font
License, Version 1.1 (https://openfontlicense.org); the license texts are installed next to the fonts
(`share/giolit/fonts/OFL-Geist.txt`, `share/giolit/fonts/OFL-PlusJakartaSans.txt`). They are used unmodified.
