Profile Manager CLI
===================

A command line interface for Profile Manager administration.


Usage
-----

You can specify the server, username, and password on the command line:

    ./pmcli.py -u pmserver.example.com -u diradmin -p apple

You can also force a prompt for a password with `-P`.

Or you can set defaults (but command line options will override):

    defaults write se.gu.it.pmcli server pmserver.example.com
    defaults write se.gu.it.pmcli username diradmin
    defaults write se.gu.it.pmcli password apple


### • add_placeholder

Add a placeholder device, and optionally add it to a group.

    ./pmcli.py add_placeholder name (serial|imei|meid|udid)=value [group]


### • import_placeholders

Import a CSV file with devices:

    ./pmcli.py import_placeholders input.csv

The CSV should have the following columns, with a header in the first line:

* name - name of the placeholder device
* ids - one or more unique identifiers for the device, on the form `type=value` and separated by `+`. Available types are `serial`, `imei`, `meid`, and `udid`
* groups - groups to add the placeholder device to, separated by `+`

The CSV file should be plain ascii or UTF-8 encoded.


### • export_placeholders

Export a CSV file with devices:

    ./pmcli.py export_placeholders output.csv

The CSV file is UTF-8 encoded and formatted for importing with `import_placeholders`.


### • dump_devices

Dump all devices in the server to a json file:

    ./pmcli.py dump_devices output.json
