---
title: 🔒 Security by design
description: OpenUEM Security
keywords:
  [
    IT assets,
    inventory,
    openuem,
    uem,
    rmm,
    security,
    unified endpoint manager,
    remote monitoring and management,
  ]
---

# 🔒 Security by design

**OpenUEM uses digital certificates** (this is not optional) for several purposes:

- To provide **mutual TLS authentication** between its components
- A user certificate will be used to log in to the console (OpenUEM Web Interface). No password for console access is stored in the database
- The SFTP server requires a certificate to log in
- The VNC/RDP session uses TLS to encrypt the remote assistance traffic

A tool to create your own Certificate Authority (cert-manager) is provided with OpenUEM and can generate the required certificates during the setup, but you can use proven tools like [CFSSL](https://github.com/cloudflare/cfssl) or [EasyRSA](https://github.com/OpenVPN/easy-rsa) to generate them too.

If you want to use remote assistance with VNC, to improve security, OpenUEM will start a supported VNC server and a noVNC proxy only when the remote assistance is needed, set a one-time password and shutdown the server when it’s no longer needed. Also, secure web sockets are used between the browser where the console is opened and the VNC server. For Gnome endpoints with Wayland, RDP can be used and credentials are changed every time a remote connection is requested.
