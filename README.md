# gh-thread

A [boring, tiny tool](https://vaughntan.org/boringtinytools) for reading GitHub issue threads from the terminal.
Fuzzy-search every issue across your repos, preview the whole comment
history in a pane, open one in a pager. Nothing more.

```
gh thread                       # everything, most recently updated first
gh thread bluesky               # keyword
gh thread -c "race condition"   # something you wrote in a comment
gh thread -R me/notes -s open
```

## Why

Reading code means reconstructing context that was never written down.
The final state survives in the file; the reasoning that produced it does
not. The author knew why line 12 had to come before line 15, tried three
other things first, and none of that is in the source.

Simon Willison's habit of [narrating his work into a GitHub issue](https://news.ycombinator.com/item?id=38836569) is a fix
for exactly this. Every task, however small, starts as an issue, and the
thread fills up with what he tried, what failed, and what he decided. The
deliberation ends up stored next to the code instead of evaporating —
which means an interruption costs a read rather than a re-derivation.

That only works if the threads are cheap to get back to. Opening a browser
is not cheap when you are in an editor.

This is the first of a few small tools trying to carry ideas from Roam Research into
everyday software work: cheap capture, dense linking, and the assumption
that you will need to re-enter your own thinking later.

> Creators need an immediate connection to what they're creating.
>
> — Bret Victor, *Inventing on Principle* (2012)

## Install

```
gh extension install trangtinkers/gh-thread
```

Requires [`gh`](https://cli.github.com) and [`fzf`](https://github.com/junegunn/fzf).
Note that the `gh` in Debian and Ubuntu's own repositories is several years
stale and will fail on issue commands; install from GitHub's apt repository
instead.

## Keys

| key      | does                    |
| -------- | ----------------------- |
| `enter`  | read the thread         |
| `ctrl-o` | open in browser         |
| `ctrl-/` | toggle the preview pane |
| `esc`    | quit                    |

## Notes

Reading goes through the REST API rather than `gh issue view`, so the body
and *every* comment always appear — including on issues that have neither.
An issue whose preview is nearly empty is one you opened and never logged
into, which is a useful thing to be able to see at a glance.

## Related

- Simon Willison, [Coping strategies for the serial project hoarder](https://simonwillison.net/2022/Nov/26/productivity/)

## License

MIT
