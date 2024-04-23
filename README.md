# MS Patch Tuesday 

`MS Patch Tuesday` is the second Tuesday of every month when Microsoft releases security updates to fix vulnerabilities in their software products.

This is a simple script, written in Python, to perform quick analysis on security updates. 
It quickly summarizes:

 - Monthly security updates.
   - Any ***high severity*** vulnerabilities (CVSSi_Base >= 8.5).
   - Any ***high likelihood*** vulnerabilities (contains 'Exploitation More Likely')
   - Any vulnerability that ***exploited in wild*** (Exploited:yes)
 - Monthly MS patched product families.

Microsoft Security Response Center (MSRC) investigates all reports of security vulnerabilities affecting Microsoft products and services, and provides these updates as part of the ongoing effort to help you manage security risks and help keep your systems protected. 

All the details from Microsoft security update are formatted according to the Common Vulnerability Reporting Framework (CVRF). 
For more details, please visit [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide).

> ***CVRF*** *stands for `Common Vulnerability Reporting Framework`.*

<!--
# Usages
Get quick summary of MS vulnerability stats for current month. 
```console
$ ./patch_tuesday.py
```
![./patch_tuesday.py](.github/patch_tuesday1.png)

## Tips
Show quick summary with simple ASCII chart.
```console
$ ./patch_tuesday.py -vc -k 2022-apr
```
![./patch_tuesday.py -vc -k 2022-apr](.github/patch_tuesday2.png)

```console
$ ./patch_tuesday -k 2022-may -v
```
![./patch_tuesday.py -k 2022-may -v](.github/2022-may.png)

```console
$ ./patch_tuesday -k 2022-jun -v
```
![./patch_tuesday.py -k 2022-jun -v](.github/2022-jun.png)

-->

# Feature

```bash
$ ./patch_tuesday.py -h
Usage: pt3.py [-h] [-c] [-j] [-k <YYYY-mmm>] [-v]

   Zzzzz   |\      _,,,---,,_
           /,`.-'`'    -.  ;-;;,_   __author__ : [ zd ]
          |,4-  ) )-,_..;\ (  `'-'  __year__   : [ 2024.04 ]
         '---''(_/--'  `-'\_)       __file__   : [ ./pt3.py ]

         [ To get summary of product families and security updates from MSRC. ]

Options:
  -h, --help     show this help message and exit
  -c             show chart output
  -j             save the JSON file
  -k <YYYY-mmm>  Date string for the report query in format YYYY-mmm: <2024-apr>
  -v             verbose output

  Get security updates from MSRC, formatted according to CVRF.
```

## Usages

<!-- show a few usages -->

## Tips

Use the `-j` option to download the JSON file.
Then use `jq` utility to count the number of vulnerabilities released.

```bash
$ cat 2023_12.json | jq '.Vulnerability | length'
51
```

# History/Updates:

 - 2022.03 : ms_patch_tuesday_2.0
 - 2024.04 : ms_patch_tuesday_3.0

## CVRF API calls
 
 - https://api.msrc.microsoft.com/cvrf/v3.0/cvrf/
 - https://api.msrc.microsoft.com/cvrf/v2.0/cvrf/

# Links:

 - [MSRC-Microsoft-Security-Updates-API](https://github.com/microsoft/MSRC-Microsoft-Security-Updates-API)
 - [MSRC CVRF API v3](https://api.msrc.microsoft.com/cvrf/v3.0/swagger/v3/swagger.json)
 - [MySeq - Patch_Tuesday Utils](https://myseq.blogspot.com/2022/07/patchtuesday-utils.html)


