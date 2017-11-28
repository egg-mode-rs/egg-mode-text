# changelog for egg-mode-text

## Pending
### Changed
- TLDs and parsing regexes updated to match upstream.
- `character_count` and `characters_remaining` no longer assume 140 characters. Since Twitter now
  accepts 280-character tweets for everyone, it seemed fit to take out the 140 assumption from my
  library. Note that this *does not* include the new character weighting algorithm proposed for
  twitter-text 2.0; this library will include that when twitter-text 2.0 is made public.
  - This is a **breaking change**, since `character_count` doesn't return the boolean any more, and
    `characters_remaining` takes an extra parameter for the character maximum.

## [0.1.0] - 2017-11-27

A near-direct rip of `egg_mode::text` as of egg-mode 0.11.0, with tests adjusted to fix paths.

<!-- vim: set tw=100 expandtab: -->
