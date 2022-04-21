
* **[openvk.uk](https://openvk.uk)** - official mirror of openvk.su (<https://t.me/openvkch/1609>)
* **[openvk.co](http://openvk.co)** - yet another official mirror of openvk.su without TLS (<https://t.me/openvkch/1654>)
* [social.fetbuk.ru](http://social.fetbuk.ru/)
* [vep

Yes! And you're very welcome to.

However, OVK makes use of Chandler Application Server. This software requires extensions, that may not be provided by your hosting provider (namely, sodium and yaml. these extensions are available on most of ISPManager hostings).

If you want, you can add your instance to the list above so that people can register there.

### Installation procedure

1. Install PHP 7.4, web-server, Composer, Node.js, Yarn and [Chandler](https://github.com/openvk/chandler)

* PHP 8 has **not** yet been tested, so you should not expect it to work. (edit: it does not work).

2. Install MySQL-compatible database.

* We recommend using Percona Server, but any MySQL-compatible server should work
* Server should be compatible with at least MySQL 5.6, MySQL 8.0+ recommended.
* Support for MySQL 4.1+ is WIP, replace `utf8mb4` and `utf8mb4_unicode_520_ci` with `utf8` and `utf8_unicode_ci` in SQLs.

3. Install [commitcaptcha](https://github.com/openvk/commitcaptcha) and OpenVK as Chandler extensions like this:

```bash
git clone https://github.com/openvk/openvk /path/to/chandler/extensions/available/openvk
git clone https://github.com/openvk/commitcaptcha /path/to/chandler/extensions/available/commitcaptcha
```

4. And enable them:

```bash
ln -s /path/to/chandler/extensions/available/commitcaptcha /path/to/chandler/extensions/enabled/
ln -s /path/to/chandler/extensions/available/openvk /path/to/chandler/extensions/enabled/
```

5. Import `install/init-static-db.sql` to the **same database** you installed Chandler to and import all sqls from `install/sqls` to the **same database**
6. Import `install/init-event-db.sql` to a **separate database** (Yandex.Clickhouse can also be used, highly recommended)
7. Copy `openvk-example.yml` to `openvk.yml` and change options to your liking
8. Run `composer install` in OpenVK directory
9. Run `composer install` in commitcaptcha directory
10. Move to `Web/static/js` and execute `yarn install`
11. Set `openvk` as your root app in `chandler.yml`

Once you are done, you can login as a system administrator on the network itself (no registration required):

* **Login**: `admin@localhost.localdomain6`
* **Password**: `admin`
  * It is recommended to change the password of the built-in account or disable it.

💡Confused? Full installation walkthrough is available [here](https://docs.openvk.su/openvk_engine/centos8_installation/) (CentOS 8 [and](https://almalinux.org/) [family](https://yum.oracle.com/oracle-linux-isos.html)).

### If my website uses OpenVK, should I release it's sources?

It depends. You can keep the sources to yourself if you do not plan to distribute your website binaries. If your website software must be distributed, it can stay non-OSS provided the OpenVK is not used as a primary application and is not modified. If you modified OpenVK for your needs or your work is based on it and you're planning to redistribute this, then you should license it under terms of any LGPL-compatible license (like OSL, GPL, LGPL etc).

## Where can I get assistance?

You may reach out to us via:

* [Bug-tracker](https://github.com/openvk/openvk/projects/1)
* [Ticketing system](https://openvk.su/support?act=new)
* Telegram chat: Go to [our channel](https://t.me/openvkenglish) and open discussion in our channel menu.
* [Reddit](https://www.reddit.com/r/openvk/)
* [Discussions](https://github.com/openvk/openvk/discussions)
* Matrix chat: #openvk:matrix.org

**Attention**: bug tracker, board, telegram and matrix chat are public places. And ticketing system is being served by volunteers. If you need to report something, that shouldn't be immediately disclosed to general public (for instance, vulnerability report), please use contact us directly at this email: **openvk [at] tutanota [dot] com**

<a href="https://codeberg.org/OpenVK/openvk">
    <img alt="Get it on Codeberg" src="https://codeberg.org/Codeberg/GetItOnCodeberg/media/branch/main/get-it-on-blue-on-white.png" height="60">
</a>
