# space for thoughts and discussion #

### opnsense updates ###
Update packages from https://pkg.opnsense.org/FreeBSD:13:amd64/22.1/sets/ change files in / and some other folders being part of the zroot/ROOT/default dataset.
Other files are being modified in /tmp, /usr and /var mounted from other zfs datasets.

To roll back it's safer to not only snapshot / but the other zfs datasets as well.

### zfs hierarchy ###
From a maintanance view it would be cleaner and easier if the zfs datasets would not be created under zroot directly but something like zroot/prod. Then everything beneath zroot/prod would just be snapshotted. But I don't think that opnsense core would do the change as I assume that the default FreeBSD install scripts are used and nobody wants to touch and break anything there.

So an alternative approach might look like to scan the zfs datasets for mountpoints and snapshot these. We'd need some naming convention then to not snapshot our own snapshots again and again...
