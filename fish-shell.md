# Fish shell

## How to `source` from a command's output instead of from a file

Just pipe into `source`!

```
some-command | source
```

You might think `eval (some-command)` would work, but _this won't work for **multi line outputs**_, as the newlines will be replaced by spaces!
For **multiline** command output you want to eval/source pipe it into `source`.
