# gnostr-cat
[![Crates.io](https://img.shields.io/crates/v/gnostr-cat)](https://crates.io/crates/gnostr-cat)
[![Crates.io](https://img.shields.io/crates/d/gnostr-cat)](https://crates.io/crates/gnostr-cat)
[![Crates.io](https://img.shields.io/crates/l/gnostr-cat)](https://github.com/gnostr-org/gnostr-cat/blob/master/LICENSE)

###### gnostr-cat is part of the *[gnostr.org](https://gnostr.org)* command line utility suite. 

Websocket client command line tool for nostr relay scripting, with docker and tor support


## Examples

Using interactive input

```shell
$ gnostr-cat wss://relay.damus.io <return>
["REQ", "RAND", {"kinds": [1], "limit": 8}] <return>
<ctrl-D>
```

Using stdin (supports multiple lines of commands)

```shell
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 8}]' |
  gnostr-cat wss://relay.damus.io

$ cat commands.txt
["REQ", "RAND", {"kinds": [1], "limit": 2}]
["REQ", "RAND2", {"kinds": [2], "limit": 2}]

$ cat commands.txt | gnost-cat wss://relay.damus.io

```

Using jq to query Nostr JSON events and select the event JSON

```shell
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 8}]' |
  gnostr-cat wss://relay.damus.io |
  jq '.[2]'

$ echo '["REQ", "RAND", {"kinds": [1], "limit": 8}]' |
  gnostr-cat wss://relay.damus.io |
  jq '.[2].content'
```

Unique (dedupe) results as they come in (note: no longer applies sorting events - FIFO)

```shell
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 8}]' |
  gnostr-cat --unique wss://relay.damus.io wss://nostr.ono.re
```

With a websocket connection timeout in milliseconds

```shell
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 2}]' |
  gnostr-cat --connect-timeout 250 wss://relay.damus.io
```


Stream websocket data (like tail -f)

```shell
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 8}]' |
  gnostr-cat --stream wss://relay.damus.io
```

Output info log messages which can assist with debugging

```shell
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 8}]' |
  RUST_LOG=info gnostr-cat wss://relay.damus.io
```

Pipe events from one server to another (currently limited to 1 event at a time)

```shell
$ echo '["REQ", "RAND", {"limit": 1}]' |
  gnostr-cat wss://relay.damus.io |
  jq -c 'del(.[1])' |
  gnostr-cat wss://nostr.ono.re
```

Pipe events from one server to another (for multiple events, `ctrl-C` when finished)

```shell
$ echo '["REQ", "RAND", {"limit": 3}]' |
  gnostr-cat wss://relay.damus.io |
  jq -c 'del(.[1])' |
  gnostr-cat --stream wss://nostr.ono.re
  <ctrl-C>
```


## Getting started
Using Cargo to install (requires ~/.cargo/bin to be in PATH)

```shell
$ cargo install gnostr-cat
```

Building from source (may be unstable)

```shell
$ git clone https://github.com/gnostr-org/gnostr-cat && cd gnostr-cat
$ cargo build --release
```

Running inside a Docker image

```shell
$ docker build -t gnostr-cat .

# Run the the docker image as an executable
$ echo '["REQ", "RAND", {"kinds": [1], "limit": 2}]' | docker run --rm -i gnostr-cat wss://relay.damus.io
```
