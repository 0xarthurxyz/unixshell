# Other notes

## How To Use grep Command In Linux / UNIX With Practical Examples

Source: https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/

Search any line that contains the word in filename on Linux:

```zsh
grep 'word' filename
```

Perform a case-insensitive search for the word ‘bar’ in Linux and Unix:

```zsh
grep -i 'bar' file1
```

Look for all files in the current directory and in all of its subdirectories in Linux for the word ‘httpd’:

```zsh
grep -R 'httpd' .
```

Search and display the total number of times that the string ‘nixcraft’ appears in a file named frontpage.md:

```zsh
grep -c 'nixcraft' frontpage.md
```

## `curl --help` guidance

```zsh
Usage: curl [options...] <url>
 -d, --data <data>          HTTP POST data
 -f, --fail                 Fail fast with no output on HTTP errors
 -h, --help <category>      Get help for commands
 -i, --include              Include protocol response headers in the output
 -o, --output <file>        Write to file instead of stdout
 -O, --remote-name          Write output to a file named as the remote file
 -s, --silent               Silent mode
 -T, --upload-file <file>   Transfer local FILE to destination
 -u, --user <user:password> Server user and password
 -A, --user-agent <name>    Send User-Agent <name> to server
 -v, --verbose              Make the operation more talkative
 -V, --version              Show version number and quit

This is not the full help, this menu is stripped into categories.
Use "--help category" to get an overview of all categories.
For all options use the manual or "--help all".
```

Help categories for `curl --help <category>`

```zsh
Invalid category provided, here is a list of all categories:

 auth        Different types of authentication methods
 connection  Low level networking operations
 curl        The command line tool itself
 dns         General DNS options
 file        FILE protocol options
 ftp         FTP protocol options
 http        HTTP and HTTPS protocol options
 imap        IMAP protocol options
 misc        Options that don't fit into any other category
 output      Filesystem output
 pop3        POP3 protocol options
 post        HTTP Post specific options
 proxy       All options related to proxies
 scp         SCP protocol options
 sftp        SFTP protocol options
 smtp        SMTP protocol options
 ssh         SSH protocol options
 telnet      TELNET protocol options
 tftp        TFTP protocol options
 tls         All TLS/SSL related options
 upload      All options for uploads
 verbose     Options related to any kind of command line output of curl
```

Help for `http` protocol

```zsh
~  $ curl --help http
Usage: curl [options...] <url>
http: HTTP and HTTPS protocol options
     --alt-svc <file name>  Enable alt-svc with this cache file
     --anyauth              Pick any authentication method
     --aws-sigv4 <provider1[:provider2[:region[:service]]]> Use AWS V4 signature authentication
     --compressed           Request compressed response
 -b, --cookie <data|filename> Send cookies from string/file
 -c, --cookie-jar <filename> Write cookies to <filename> after operation
 -d, --data <data>          HTTP POST data
     --data-ascii <data>    HTTP POST ASCII data
     --data-binary <data>   HTTP POST binary data
     --data-raw <data>      HTTP POST data, '@' allowed
     --data-urlencode <data> HTTP POST data URL encoded
     --digest               Use HTTP Digest Authentication
     --disallow-username-in-url Disallow username in URL
 -D, --dump-header <filename> Write the received headers to <filename>
     --etag-compare <file>  Pass an ETag from a file as a custom header
     --etag-save <file>     Parse ETag from a request and save it to a file
     --expect100-timeout <seconds> How long to wait for 100-continue
 -f, --fail                 Fail fast with no output on HTTP errors
     --fail-with-body       Fail on HTTP errors but save the body
 -F, --form <name=content>  Specify multipart MIME data
     --form-escape          Escape multipart form field/file names using backslash
     --form-string <name=string> Specify multipart MIME data
 -G, --get                  Put the post data in the URL and use GET
     --haproxy-protocol     Send HAProxy PROXY protocol v1 header
 -I, --head                 Show document info only
 -H, --header <header/@file> Pass custom header(s) to server
     --hsts <file name>     Enable HSTS with this cache file
     --http0.9              Allow HTTP 0.9 responses
 -0, --http1.0              Use HTTP 1.0
     --http1.1              Use HTTP 1.1
     --http2                Use HTTP 2
     --http2-prior-knowledge Use HTTP 2 without HTTP/1.1 Upgrade
     --http3                Use HTTP v3
     --ignore-content-length Ignore the size of the remote resource
     --json <data>          HTTP POST JSON
 -j, --junk-session-cookies Ignore session cookies read from file
 -L, --location             Follow redirects
     --location-trusted     Like --location, and send auth to other hosts
     --max-redirs <num>     Maximum number of redirects allowed
     --negotiate            Use HTTP Negotiate (SPNEGO) authentication
     --no-alpn              Disable the ALPN TLS extension
     --no-npn               Disable the NPN TLS extension
     --ntlm                 Use HTTP NTLM authentication
     --ntlm-wb              Use HTTP NTLM authentication with winbind
     --post301              Do not switch to GET after following a 301
     --post302              Do not switch to GET after following a 302
     --post303              Do not switch to GET after following a 303
 -r, --range <range>        Retrieve only the bytes within RANGE
     --raw                  Do HTTP "raw"; no transfer decoding
 -e, --referer <URL>        Referrer URL
     --request-target <path> Specify the target for this request
 -z, --time-cond <time>     Transfer based on a time condition
     --tr-encoding          Request compressed transfer encoding
 -A, --user-agent <name>    Send User-Agent <name> to server
```

Couldn't get any requests with JSON data to work

```zsh
~  $ curl http://localhost:3000/mock --data --json {'text': 0} 
zsh: parse error near `}'
```

```html
~  $ curl http://localhost:3000/mock --json "{'text': '0'}"
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>Error</title>
</head>
<body>
<pre>SyntaxError: Unexpected token &#39; in JSON at position 1<br> &nbsp; &nbsp;at JSON.parse (&lt;anonymous&gt;)<br> &nbsp; &nbsp;at parse (/Users/arthur/Documents/mockapi/node_modules/body-parser/lib/types/json.js:92:19)<br> &nbsp; &nbsp;at /Users/arthur/Documents/mockapi/node_modules/body-parser/lib/read.js:128:18<br> &nbsp; &nbsp;at AsyncResource.runInAsyncScope (node:async_hooks:202:9)<br> &nbsp; &nbsp;at invokeCallback (/Users/arthur/Documents/mockapi/node_modules/raw-body/index.js:238:16)<br> &nbsp; &nbsp;at done (/Users/arthur/Documents/mockapi/node_modules/raw-body/index.js:227:7)<br> &nbsp; &nbsp;at IncomingMessage.onEnd (/Users/arthur/Documents/mockapi/node_modules/raw-body/index.js:287:7)<br> &nbsp; &nbsp;at IncomingMessage.emit (node:events:527:28)<br> &nbsp; &nbsp;at endReadableNT (node:internal/streams/readable:1344:12)<br> &nbsp; &nbsp;at process.processTicksAndRejections (node:internal/process/task_queues:82:21)</pre>
</body>
</html>
```

Incomplete JSON data seems to work:

```zsh
~  $ curl --json {} http://localhost:3000/mock/echo
{}%          
```