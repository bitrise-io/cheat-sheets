# lpass (LastPass CLI)

https://github.com/lastpass/lastpass-cli

- `lpass ls` : Lists all available items.
- `lpass ls | grep -i 'something'` : Filter/find items that include the text "something" in the title.
  - `grep -i` is case insensitive. For case sensitive simply don't include the `-i` flag in the `grep` part.
- `lpass show X` : Show the full item.
- `lpass show X --notes` : Show only the Notes part of item X.
- `lpass show -G case-insensitive-term` : Search + show the result in one command.
  - Note: if there are multiple items matching the specified term it will just list them, will not show any of them.

## Load envs from a LastPass Secure Note

If you have a Secure Note in LastPass in the format:

```
export SECRET_KEY_1='value 1'
export SECRET_KEY_2='value 2'
```

To not to risk the secret being accidentally exposed by having it in a file, forgetting about it and then someone getting it from a backup/via any way if they can access your computer/file system/backups/... you can load this environment set directly from the Secure Note into your shell **without ever saving it into a file** this way:

Bash:

```
eval $(lpass show -G 'name of the secure note' --notes)
```

Fish:

```
lpass show -G 'name of the secure note' --notes | source
```
