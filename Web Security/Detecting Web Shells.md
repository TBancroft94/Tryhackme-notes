# Detecting Web Shells

## Room Summary

This room focused on investigating a compromised WordPress server to identify web shell activity.

---

## Skills Learned

- Apache log analysis
- Web shell detection
- Linux command line investigation
- HTTP request analysis
- Identifying attacker behavior
- Attack timeline reconstruction

---

## Useful Commands

Find PHP files

```bash
find /var/www -type f -name "*.php"
```

Display a web shell

```bash
cat /var/www/html/wordpress/wp-content/uploads/shadyshell.php
```

Search Apache logs

```bash
grep ".php" /var/log/apache2/access.log
```

---

## Investigation Timeline

1. Identified the attacker's IP.
2. Found the first successful directory.
3. Located `upload_form.php`.
4. Identified the uploaded web shell.
5. Observed the first command (`whoami`).
6. Found the download of `linpeas.sh`.
7. Examined the web shell source code.
8. Retrieved the hidden flag.

---

## Key Indicators of Compromise

- Repeated GET requests
- POST request to upload page
- Query string containing `cmd=`
- Download of `linpeas.sh`
- PHP web shell

---

## What I Learned

Following one attacker through the logs makes it much easier to reconstruct the full attack timeline than searching for isolated events.
