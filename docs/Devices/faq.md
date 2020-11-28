# FAQ

## SSH
* Q: When i try to ssh into (router|switch) i get the message. ``Unable to negotiate with x.x.x.x port 22: no matching key exchange found. Their offer diffie-hellman-group1-sha1``
* A: edit /etc/ssh/ssh_config and uncomment
	* ``#   MACs hmac-md5,hmac-sha1,hmac-sha2-256,umac-64@openssh.com,hmac-ripemd160``
	* ``#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc``
	* and add these next few lines.
	* ``HostkeyAlgorithms ssh-dss,ssh-rsa``
	* ``KexAlgorithms +diffie-hellman-group1-sha1``
	* Then you should be able to access the (switch|router) as you would over serial.