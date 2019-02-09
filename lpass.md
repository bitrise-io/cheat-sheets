# lpass (LastPass CLI)

https://github.com/lastpass/lastpass-cli

- `lpass ls` : lists all available items.
- `lpass ls | grep -i 'something'` : filter/find items that include the text "something" in the title.
  - `grep -i` is case insensitive. For case sensitive simply don't include the `-i` flag in the `grep` part.
- `lpass show X` : Show the full item.
- `lpass show X --notes` : Show only the Notes part of item X.
