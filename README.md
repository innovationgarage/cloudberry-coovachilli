# cloudberry-coovachilli

Configuration to be used with a cloudberry chilli deployment on OpenWrt/LEDE.

See [Chilli Access Controller On Raspberry Pi Model B V1.2](Rpi.md) for a step
by step guide setting up on a new device.

## Troubleshooting

Below are some possibly useful things depending on your issues.

### Dependencies

- Make sure [`haserl`](http://haserl.sourceforge.net) is installed (`opkg install haserl`).
- Check `haserl` and scripts work properly by running `/etc/chilli/wwwsh /etc/chilli/www/login.chi`.

### Check secrets are correct

- Make sure that `/etc/chilli/defaults` has the correct `HS_RADSECRET` and `HS_UAMSECRET`.
- Make sure that `/etc/config/chilli` has the correct `radiussecret` and `uamsecret`.

### Turning on debug

Chilli provides a lot of debug information that can be turned on by using the
`--debug` flag.  The file to change for this is in `/etc/init.d/chilli` where
you can look for the `start_chilli()` function. Also remember to restart for
the change to take effect.

### Restarting Chilli

Restarting is not reliable and might not always work as expected, so try
stopping and starting when doing configuration changes. Also verifying that
chilli is running via `ps` is a good idea.

    $ /etc/init.d/chilli stop
    $ /etc/init.d/chilli start
    $ ps | grep chilli


### Misc

- Don't mix WAN and LAN.

Disable `dnsmasq`, chilli already handles DHCP requests so having both dnsmasq
running might cause issues.

    $ /etc/init.d/dnsmasq stop
    $ /etc/init.d/dnsmasq disable

## Useful links

- [CoovaChilli captive portal](https://openwrt.org/docs/guide-user/services/captive-portal/wireless.hotspot.coova-chilli?s[]=coovachilli)
- [CoovaChilli - man pages](http://coova.github.io/CoovaChilli/man-pages.html)
- [Coova website](https://coova.github.io)
