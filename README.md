
<h1 align="center">Blacklisted Domains as Output <a href="https://github.com/ngadmini/Grabbing-Blacklist-for-Bind9-RPZ">this repo</a></h1>

<p align="center">
  <b>blacklisted domains as output <a href="https://github.com/ngadmini/Grabbing-Blacklist-for-Bind9-RPZ">this repo</a></b><br>
  <a href="https://github.com/ngadmini/Grabbing-Blacklist-for-Bind9-RPZ"><img src="https://img.shields.io/badge/bind9%20RPZ-Grabbing%20Blacklist%20for%20Bind9%20RPZ-blue?style=flat-square&logo=github"></a>
  <br><br>
  <a href="#"><img src="http://s.4cdn.org/image/title/105.gif"></a>
</p>

### featuring
- [x] free from duplicate entries and sub-domains entries (if it's parent-domain exist) across categories
- [x] free from invalid TLDs and domain entries that construct with international characters (non ASCII)
- [x] ip-address is written in CIDR block

### usage
concatenate `txt.adulta* and txt.trust+a*`, then use `grab_build.sh` in [this repo](https://github.com/ngadmini/Grabbing-Blacklist-for-Bind9-RPZ/blob/master/libs/grab_build.sh)
```shell
~$ grab_build="https://raw.githubusercontent.com/ngadmini/Grabbing-Blacklist-for-Bind9-RPZ/master/libs/grab_build.sh"
~$ grab_libs="https://raw.githubusercontent.com/ngadmini/Grabbing-Blacklist-for-Bind9-RPZ/master/libs/grab_library"
~$ curl -s -o rpz_db.zip https://codeload.github.com/ngadmini/partial-output/zip/refs/heads/master
~$ unzip rpz_db.zip -x partial-output-master/{LICENSE,README.md,.gitignore}
~$ curl -s -o "partial-output-master/grab_build.sh" "${grab_build}"
~$ curl -s -o "partial-output-master/grab_library" "${grab_libs}"
~$ cat partial-output-master/txt.adulta* > partial-output-master/txt.adult
~$ cat partial-output-master/txt.trust+a* > partial-output-master/txt.trust+
~$ rm partial-output-master/txt.{adulta,trust+a}*
~$ bash partial-output-master/grab_build.sh
~$ unset -v grab_build grab_libs
```
you will get domain list in BIND9-rpz format in 5 catagories (7 sub-categories of adult category AND 2 sub-categories of trust+). enjoy it's
### Renaming CNAME Targer 
```
sed 's/CNAME\ ./IN CNAME\ @/g' db.trust+ab > db.trust+ab.rpz
```
### license
- [x] [![CC BY-SA 4.0][cc-by-sa-shield]][cc-by-sa]
- [x] this work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License][cc-by-sa].

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
