# useful-snippets
A collection of useful code snippets and corresponding explanation


## Read HTTP Response:

```sh
cd ~
cat > .curlrc <<EOF
-w "\n"
silent
-D /dev/stderr
EOF
```
This set of commands:

1. Adds a newline character at the end of the response, which avoids having the next shell prompt end up on the same line as the last line of the curl response.
1. Disables the progress meter when piping the response to another command.
1. Writes the headers to standard error so that they are printed on the screen and not piped to another command.

With these options set, a curl command that is piped to jq, a JSON processor that pretty prints its input, will be very easy to read. The first line of the response shows the status code that was returned (200). The next lines show headers that were received with the response. Finally, the colorized output is pretty-printed JSON from the response.
