There are now four GPU nodes available for your use.

We have configured a bastion host at rhelai-gw.int.massopen.cloud to
provide access to the bmcs of the gpu nodes. You can log in as jeremyeder
using the private key associated with https://github.com/jeremyeder.keys.

The BMC addresses are in the /etc/hosts file:

    10.2.18.127 gpu0-bmc
    10.2.18.128 gpu1-bmc
    10.2.18.130 gpu2-bmc
    10.2.18.131 gpu3-bmc

You will find credentials for these devices in the bmc-credentials.txt
file in your home directory.

We have allocated four ip address four you on the 129.10.5.0/24
network:

- 129.10.5.160
- 129.10.5.161
- 129.10.5.162
- 129.10.5.163

The default gateway for this network is 129.10.5.1. You will need to
assign these addresses manually; there is no DHCP service available.

You have a few options for accessing the bmcs from your local machine.
This is what I do:

1. Establish a SOCKS proxy when connecting to rhelai-gw:

    ssh -D1080 jeremyeder@rhelai-gw.int.massopen.cloud

2. Configure your browser to use the SOCKS proxy at localhost:8080. I
   use Proxy SwitchyOmega [1] in Chrome and FoxyProxy [2] in Firefox.

Some of my colleages prefer to use ssshuttle [3] instead.

Once you have established a connection:

3. Log in to the bmc using the credentials from bmc-credentials.txt.

4. Select the "Remote Console" menu option from the left navigation
   bar.

5. Select the "Launch console" button at the top of the following
   screen. You will need to enable popups for this to work.

6. Once the console is open (I had to switch browsers to get this to
   work), click the "Media" button at the top of the page to access
   the virtual media functions.

7. Click "Activate" to enable virtual media features, then "Browse" to
   select an installer image, and finally "Mount all local media" to
   mount the media on the remote system.

8. At this point you should be able to power on the system using the
   "Power" button at the top of the screen and have it boot into your
   installer.

Let me know if you have any questions.

[1]: https://chromewebstore.google.com/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif
[2]: https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/
[3]: https://github.com/sshuttle/sshuttle

