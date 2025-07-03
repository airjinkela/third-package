# openwrt-twin-bcrypt-js
 
This is a package that I cobbled together for OpenWRT.  I admit that it isn't exactly "compatible" with the way that LuCI runs things, but I am able to load it from a JS file using code like this from the [LuCI AdGuardHome app Configuration Page](https://github.com/xptsp/luci-app-adguardhome/blob/main/htdocs/config.js):
```
		var BCryptInclude = form.DummyValue.extend({
			renderWidget: function(section_id, option_index, cfgvalue) {
				return E('script', { 'type':'text/javascript', 'src':'/luci-static/resources/view/twin-bcrypt.min.js' });
			}
		});
		o = s.option(BCryptInclude, 'misc');

		var ChangePassword = form.Button.extend({
			set_passwd: rpc.declare({
				object: 'luci.adguardhome',
				method: 'set_passwd',
				params: [ 'username', 'hash' ],
			}),
			onclick: function() {
				var username = document.getElementById("widget.cbid.adguardhome.config.web_username").value;
				var password = document.getElementById("widget.cbid.adguardhome.config.web_password").value;
				var hash = TwinBcrypt.hashSync(password);
				return Promise.all([ this.set_passwd( username, hash ) ]);
			},
		});
		o = s.option(ChangePassword, 'change_password', _('Change Password'));
```

### Source:
- [Twin-BCrypt repository](https://github.com/fpirsch/twin-bcrypt)
