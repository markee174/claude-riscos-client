## Licence

Licensed under the Apache License, Version 2.0. See `LICENSE`.
```

Keep "Apache License" with an s: it's the licence's proper name, even in British English.

**Add the LICENSE file.** On GitHub, choose Add file → Create new file, type `LICENSE` as the name, then use "Choose a license template" and pick Apache License 2.0. GitHub fills in the full text and shows the licence on the repository page. Don't edit the body of the licence. If you include the appendix's copyright notice, fill in the year and name: `Copyright 2026 Mark Stephens`.

**Put a short header in the source.** Apache 2.0 recommends a notice at the top of each source file. For `!RunImage`, add these lines below the existing title REMs:

```
REM Copyright 2026 Mark Stephens
REM Licensed under the Apache License, Version 2.0 (the "License");
REM you may not use this file except in compliance with the License.
REM You may obtain a copy of the License at
REM     http://www.apache.org/licenses/LICENSE-2.0
REM Distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS
REM OF ANY KIND, either express or implied.
```

That's text only, so it costs nothing at run time beyond a few hundred bytes of comments. Tokenize can strip REMs from a release build if you care.

**A NOTICE file is optional.** You only need one if you want attribution notices that people must carry forward into their copies.

**One honest caveat:** Claude wrote most of this code, and who owns the copyright in AI-generated code is legally unsettled. UK law has a provision for computer-generated works, but how it applies to output like this hasn't been tested much. The README's "How it was made" section already says Claude wrote the code, which covers you on disclosure. If ownership matters to you beyond a hobby release, ask a lawyer; I'm not one.
