# recall-testdata

Overwatch screenshot image fixtures for
[`sound-barrier/recall`](https://github.com/sound-barrier/recall).

This repo holds **only the binary screenshot images** (`*.png` / `*.jpg`) that
the Recall parser's golden-file tests run against. It exists so the image corpus
can grow without bloating the main repo's git history.

The matching `*.golden.json` expected-output sidecars and the fixture
documentation live in the **main** repo under `testdata/`, which references this
repo as a git submodule mounted at `testdata/images/`. The golden test resolves
each image here against its golden in the main repo by filename.

## Adding a screenshot

1. Drop the curated PNG (or JPG) into this repo's root and push.
2. In the main repo: `git submodule update --remote testdata/images` to bump the
   pinned commit, then `task update-goldens` to generate the sidecar, and commit
   the submodule bump + new golden together.

## Privacy

Images are deliberately curated post-match captures. The parser extracts no
BattleTags, so the golden sidecars are identity-free; the PNG bytes are
user-visible game UI. If you're not the maintainer and want to contribute a
fixture, open an issue on the main repo first.
