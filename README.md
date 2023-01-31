# egg-mode-text

like twitter-text, but in rust

This library is an attempt to port [twitter-text] to Rust. It was originally part of [egg-mode], but
it's totally distinct from egg-mode type-wise, so i pulled it out into its own library. (Also it's
chock full of macros so it was also a bid to bring egg-mode's compile times down. `>_>`)

[twitter-text]: https://github.com/twitter/twitter-text
[egg-mode]: https://github.com/QuietMisdreavus/twitter-rs

This library can be used to count characters for tweets, and extract URLs and "entities" from
arbitrary text, such as @-mentions and hashtags.

For example, to see how many characters a given tweet takes:

```rust
use egg_mode_text::character_count;

let count = character_count("This is a test.", 23, 23);
assert_eq!(count, 15);

// URLs get replaced by a t.co URL of the given length
//
// This length is available from the Twitter API in `help/configuration`
let count = character_count("test.com", 23, 23);
assert_eq!(count, 23);

// Multiple URLs get shortened individually
let count =
    character_count("Test https://test.com test https://test.com test.com test", 23, 23);
assert_eq!(count, 86);
```

To extract substrings of various "entities" used by Twitter:

```rust
use egg_mode_text::{EntityKind, entities};

let text = "sample #text with a link to twitter.com";
let mut results = entities(text).into_iter();

let entity = results.next().unwrap();
assert_eq!(entity.kind, EntityKind::Url);
assert_eq!(entity.substr(text), "twitter.com");

let entity = results.next().unwrap();
assert_eq!(entity.kind, EntityKind::Hashtag);
assert_eq!(entity.substr(text), "#text");

assert_eq!(results.next(), None);
```

For more information, check out the [documentation].

[documentation]: https://docs.rs/egg-mode-text

To use this crate in your own project, add the following to your Cargo.toml:

```toml
[dependencies]
egg-mode-text = "1.15.1"
```

...and add the following to your crate root:

```rust
extern crate egg_mode_text;
```

## License

egg-mode-text is licensed under the Mozilla Public License, version 2.0. See the LICENSE file for
details.
