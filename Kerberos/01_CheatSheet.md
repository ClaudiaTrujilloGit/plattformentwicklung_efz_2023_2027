| Command | Description |
| ----------- | ----------- |
| `kinit` | Authenticates a user and obtains a Kerberos Ticket-Granting Ticket (TGT).  |
| `klist` | Lists the Kerberos tickets currently held in the credential cache.  |
| `kdestroy` | Destroys (removes) all Kerberos tickets from the credential cache.  |
| `kvno` | Displays the key version number (KVNO) of a service principal.  |
| `kpasswd` | Changes the Kerberos password of a principal.  |
| `kadmin` | Administrative tool for managing the Kerberos database remotely (requires proper ACLs).  |
| `kadmin.local` | Local Kerberos administration tool that runs directly on the Key Distribution Center (KDC) without needing Kerberos authentication.  |
| `ktadd` | Adds a principal’s key to a keytab file (used for service principals).  |
| `kadmin.local: addprinc [principal-name]` | Creates a new principal in the Kerberos database.  |
| `kadmin.local: delprinc [principal-name]` | Deletes a principal from the Kerberos database.  |
