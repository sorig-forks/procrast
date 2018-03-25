# Procrast: a tool for managing blocked domains in `/etc/hosts`

A command line tool that allows you to manage a domain block list in
`/etc/hosts`. Turning blocking on/off for the entire list, adding, and removing
domains can be done from the command line using procrast. 

The tool writes directly to your `/etc/hosts` file and keeps track of the list
using an identifier comment (your existing entries won't be affected, and you
can keep adding entries that aren't managed by procrast). Turning blocking
on/off for the entire domain list works by commenting and uncommenting the
entries marked to be managed by procrast.

## Installation

If you are unsure what the `/etc/hosts` file is, you will probably want to make
a backup of the file and keep it safe in case you want to revert to your
pre-procrast configuration. When you wish to revert any changes procrast has
made, simply replace the `/etc/hosts` file with your backed-up version.

Download the `procrast` file. To see the options available in procrast type

```
sh path/to/the/file/procrast
```

Place the `procrast` file somewhere that's on your shell's `$PATH`, e.g. inside 
`/usr/local/bin`. Make sure the file is executable:
`chmod +x /usr/local/bin/procrast`. When you start a new shell, the tool can be
used by typing `procrast`.

## Usage

Note that procrast needs root privileges for operations that modify the
`/etc/hosts` file. 

To add a domain to the block list

```
procrast add facebook.com
```

To see the current list of domains

```
procrast list
```

To start blocking the list

```
procrast no
```

To stop blocking the list
```
procrast yes
```

To remove a domain from the block list

```
procrast remove facebook.com
```

On macOS you may have to restart the `mDNSResponder` daemon to clear the local
DNS cache. A convenience command is available in procrast to do this

```
procrast dns_reload
```
