# progress of twitter-text port

At the time of writing, egg-mode-text is about a year behind of TLD updates and other changes to the
parsing regular expressions. There are also [pending changes to the structure of twitter-text
itself][text-change] that will require farther updates when they are released to GitHub. Until then,
this is the portion of egg-mode's `TODO.md` pertaining to twitter-text:

[text-change]: https://twittercommunity.com/t/updating-the-character-limit-and-the-twitter-text-library/96425

- [x] "character count" (`character_count`, `characters_remaining`)
- [x] "extract URL entities" (`url_entities`)
- [x] "extract hashtag entities" (`hashtag_entities`)
- [x] "extract symbol ("cashtag") entities" (`symbol_entities`)
- [x] "extract user mention entities" (`mention_entities`)
- [x] "extract user and list mention entities" (`mention_list_entities`)
- [x] "extract leading mention from reply" (`reply_mention_entity`)
- [x] "extract all entities" (`entities`)
- [ ] "given text, insert hyperlinks for URLs/mentions/hashtags/cashtags"
- [ ] "given text and tweet entities, insert hyperlinks for URLS/mentions/hashtags/cashtags"
