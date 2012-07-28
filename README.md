Web tunnel on dotCloud
======================
If you ever need to share you local web server to the world, here is an easy way to do that using dotCloud.

There are three steps:
# Create the dotCloud application
# Open an SSH tunnel to the dotCloud server
# Access your local web server using the dotCloud URL


Create the dotCloud application
-------------------------------
`dotcloud create webtunnel`

`dotcloud push webtunnel`


To open a tunnel
----------------
You need to open an SSH tunnel on the machine your local webserver is running *to* the dotCloud server.

First determine your $HOST and $PORT by looking at the ssh url by doing `dotcloud info webtunnel.proxy | grep "ssh://"`. It is formatted as `ssh://dotcloud@$HOST:$PORT`.

In the command below, replace `localhost:8080` to point to your webserver. If you don't have any just run `python -m SimpleHTTPServer` to get one running on port 8080. Do not change port 8042.

`ssh -i ~/.dotcloud/dotcloud.key -p $PORT dotcloud@$HOST -R 8042:localhost:8080`


Access your application
-----------------------
Your local web server should now be accessible at the URL given after deploying the dotCloud application.
