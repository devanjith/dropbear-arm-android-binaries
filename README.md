# dropbear binaries for android
## armv7 / PIE / API 21+

###Client public key auth:

Dropbear can do public key auth as a client, but you will have to convert
OpenSSH style keys to Dropbear format, or use dropbearkey to create them.

If you have an OpenSSH-style private key ~/.ssh/id_rsa, you need to do:

'''bash
dropbearconvert openssh dropbear ~/.ssh/id_rsa  ~/.ssh/id_rsa.db
dbclient -i ~/.ssh/id_rsa.db <hostname>
'''

Dropbear does not support encrypted hostkeys though can connect to ssh-agent.

============================================================================

If you want to get the public-key portion of a Dropbear private key, look at
dropbearkey's '-y' option.

============================================================================

To run the server, you need to server keys, this is one-off:

'''bash
./dropbearkey -t rsa -f dropbear_rsa_host_key
./dropbearkey -t dss -f dropbear_dss_host_key
./dropbearkey -t ecdsa -f dropbear_ecdsa_host_key
'''
