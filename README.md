tsocks
======

Clone of the official tsocks library, with specific build instructions so it works with TunnelSetup

The binaries are built like this:

./configure --with-conf=~/tsocks.conf
make

Example:

Create a tsocks.conf for each Proxy server containing something like this:

<pre>
server = 127.0.0.1
server_port = 10080
server_type = 5
local = 127.0.0.0/255.255.255.0
</pre>

Prepend the command line for each binary that communicate with target like this:

<pre>
LD_PRELOAD=\<path to tsocks\>/libtsocks.so TSOCKS_CONF_FILE=\<path to conf\>/tsocks.conf \<app connecting to target\>
</pre>

Note that the app that connect to target can use target IP address and port directly, because it will be automatically tunneled through the SOCKS server setup by TunnelSetup.
Make sure the server_port in tsocks.conf match the port in tunnels.cfg

