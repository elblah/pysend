# pysend

Send files/dirs over HTTP with interactive receive. 100% Python stdlib + tar.

```
# on rpi (receiver)
pysend receive

# on phone/tvbox (sender)
pysend send myfile.txt --host 192.168.1.100
pysend send mydir/     --host 192.168.1.100
```

## Why

- works behind HTTP proxies (unlike nc/rsync)
- no SSH setup (unlike scp/rsync)
- interactive "save as?" prompt with overwrite protection
- reject unwanted files on the fly

## Usage

```
pysend receive [--port PORT]
pysend send <path> --host HOST [--port PORT]
```

### Environment

| Variable | Default | Description |
|----------|---------|-------------|
| `PYSEND_HOST` | localhost | server hostname (send) |
| `PYSEND_PORT` | 8001 | server port |

### Receive prompt

```
save as [filename] (from 192.168.1.5):
```

| Input | Action |
|-------|--------|
| Enter | accept suggested name |
| `!` / `.` | reject file |
| `?` / `help` | show commands |
| `<name>` | save as `<name>` |

### Alias

```sh
alias pysend-rpi='pysend send --host 192.168.1.100'
```

## License

MIT License

Copyright (c) 2026 DanielT

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
