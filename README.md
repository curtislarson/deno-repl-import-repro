# `deno repl --eval-file` repro

Run `deno task repl` or `deno repl --unstable --no-check --eval-file=./dir1/mod1.ts`

with `mod1.ts` being:

<https://github.com/curtislarson/deno-repl-import-repro/blob/1234567667c2f0c0356ec44f3b7976aef9dcbd99/dir1/mod1.ts#L1>

and `mod2.ts` being:

<https://github.com/curtislarson/deno-repl-import-repro/blob/1234567667c2f0c0356ec44f3b7976aef9dcbd99/dir2/mod2.ts#L1>

You should see something like:

```zsh
❯ deno repl --unstable --no-check --eval-file=./dir1/mod1.ts
error in --eval-file file ./dir1/mod1.ts. Uncaught TypeError: Module not found "file:///Users/curputer3/dev/me/dir2/mod2.ts".
    at async <anonymous>:2:1
Deno 1.25.2
exit using ctrl+d or close()
>
```

Compared to `deno task repl:quack` or `deno repl --unstable --no-check --eval='await import("./dir1/mod1.ts")'`

Which shows:

```zsh
❯ deno repl --unstable --no-check --eval='await import("./dir1/mod1.ts")'
QUACK
Deno 1.25.2
exit using ctrl+d or close()
>
```
