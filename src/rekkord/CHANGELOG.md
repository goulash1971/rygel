# Changelog

## Alpha versions

> [!CAUTION]
> This software has not been stabilized yet and **must not be used as your primary backup** tool.
> You've been warned!

### Rekkord 0.44

*Released on 2025-04-21*

- Auto-generate user passwords when prompt is left empty
- Fix ambiguous *--password* option in `rekkord add_user`

### Rekkord 0.43

*Released on 2025-04-21*

- Change users to be single-role and create two users by default (*full* and *write*)
- Rename repository environment variable from `REKKORD_URL` to `REKKORD_REPOSITORY`
- Rename user setting and environment variable
- Support -f as shortcut for `--force` in Rekkord user commands
- Try to prevent sensitive memory from ending up in core dumps

> [!WARNING]
> Existing users are not migrated and new users must be created with the master key.

### Rekkord 0.42

*Released on 2025-04-18*

- Fix error when trying to restore special files (such as sockets)
- Skip creation of root directory in `rekkord restore` when *--dry_run* is used

### Rekkord 0.41

*Released on 2025-04-17*

- Drop support for long snapshot names (reduce list performance)
- Explictly limit snapshot name length to 80 bytes
- Remove username suffix in default snapshot names
- Fix ignored value from *REKKORD_USERNAME* environment variable

### Rekkord 0.40

*Released on 2025-04-16*

- Derive encryption keys from the master key
- Use separate data key pair (for blobs) and tag/log key pair (for snapshot log)
- Derive the FastCDC chunker seed from the write key
- Derive the BLAKE3 hash salt from the write key
- Pad blobs with Padmé algorithm to reduce size leakage
- Always prompt user for master key export path
- Drop `rekkord export_key` command since the master key is not stored anymore
- Drop *--skip_key* option from `rekkord init` since export is not possible after that
- Sort `rekkord list_users` entries alphabetically

> [!WARNING]
> This is a breaking change, and there is no migration path. A new repository must be used.

### Rekkord 0.39

*Released on 2025-03-23*

- Fix excessive memory usage during `rekkord save`

### Rekkord 0.38

*Released on 2025-03-23*

- Use 256 subdirectories for blobs instead of 4096

> [!WARNING]
> This is a breaking change, and requires migrating older repositories manually!

### Rekkord 0.37

*Released on 2025-03-23*

- Add retry logic to handle transient SFTP errors in rekkord
- Add *--preserve_atime* option to `rekkord save`
- Fix wrong cache ID used by `rekkord rebuild_cache`
- Fix minor typos in help and log

### Rekkord 0.36

*Released on 2025-03-22*

- Fix stalling and deadlock when restoring many files in `rekkord restore`

### Rekkord 0.35

*Released on 2024-12-25*

- Fix error when listing empty directories and snapshots (regression introduced in Rekkord 0.30)

### Rekkord 0.34

*Released on 2024-12-09*

- Use more standard syntax in usage texts
- Use assembly implementations of blake3 and libsodium algorithms

### Rekkord 0.33

*Released on 2024-11-29*

- Show busy progress bar while running `rekkord save`

### Rekkord 0.32

*Released on 2024-11-28*

- Support sub-object listing and restoration in rekkord
- Drop *--flat* option from `rekkord restore` command
- Drop *--flat* option from `rekkord mount` command

### Rekkord 0.31

*Released on 2024-11-25*

- Fix use of unix time format for `rekkord list -f XML`
- Change style of CLI progress bars

### Rekkord 0.30

*Released on 2024-11-24*

- Adjust rekkord data format for better progress reports (causes transient repository size expansion)
- Report progress while running `rekkord restore`
- Report progress while running `rekkord list`
- Reduce number of threads for local rekkord repositories
- Default to 100 threads for S3 access in rekkord
- Fix detection of *sftp:* URLs in rekkord
- Fix stripped root '/' with short SSH urls
- Expose tag filename in `rekkord snapshots`
- Use ISO time strings for JSON and XML rekkord outputs
- Fix typos in help and error messages

### Rekkord 0.29

*Released on 2024-10-16*

- Revert "Always append username to snapshot names" change

### Rekkord 0.28

*Released on 2024-10-15*

- Add *--pattern* option to `rekkord snapshots`
- Clean up and rename `rekkord mount` fuse options

### Rekkord 0.27

*Released on 2024-10-08*

- Replace base64 master key display with file export
- Always append username to snapshot names

### Rekkord 0.26

*Released on 2024-10-02*

- Fix `rekkord save` crash when saving in raw mode
- Fix read-beyond-end of hash identifiers
- Append username to default snapshot names
- Fix possible NULL name when listing snapshots

### Rekkord 0.25

*Released on 2024-10-02*

- Support locating snapshots by name in main commands
- Show SSH error message if SFTP error is "Success"
- Fix broken multi-sort in `rekkord snapshots`

### Rekkord 0.24

*Released on 2024-10-01*

- Remove support for anonymous snapshots
- Add sort option to `rekkord snapshots`
- Improve exploration commands with colors
- Fix ugly double-slash in restore paths
- Use O_TMPFILE for `rekkord restore` on Linux
- Improve Windows compatibility
- Switch to GPL 3+ license

### Rekkord 0.23

*Released on 2024-09-03*

- Support *--verbose* and *--dry_run* flags in `rekkord restore`

### Rekkord 0.22

*Released on 2024-09-03*

- Add option to delete extra files and directories with `rekkord restore`
- Fix incorrect mtime when restoring files on POSIX systems

### Rekkord 0.21

*Released on 2024-07-28*

- Update to LZ4 1.10.0
- Use higher LZ4 compression level by default
- Add setting to change LZ4 compression level

### Rekkord 0.20

*Released on 2024-07-19*

- Fix error when using `rekkord build_cache`

### Rekkord 0.19

*Released on 2024-07-18*

- Reduce intempestive rekkord cache rebuilds
- Drop buggy error code check in SFTP code
- Always run cache rebuild inside transaction

### Rekkord 0.18

*Released on 2024-07-18*

- Rebuild local cache when ID changes
- Fix silent SSH overwrite fails in rekkord commands
- Normalize and check mount point ahead of time
- Fix crash after `rekkord mount` exit due to destructor ordering
- Use capitalized attribute names in XML outputs
- Adjust open mode required for advanced commands
- Protect rekkord secrets with mlock() and zero erase

### Rekkord 0.17

*Released on 2024-04-01*

- Optimize tag storage and listing
- Isolate advanced rekkord commands
- Add `rekkord rebuild_cache` command

### Rekkord 0.16

*Released on 2024-03-18*

- Add FUSE support with `rekkord mount`
- Rename put/get commands to save/restore
- Store number of subdirectories in directory entries (causes transient repository size expansion)
- Reduce unnecessary traffic while listing tree content
- Reduce binary size

### Rekkord 0.15

*Released on 2024-02-19*

- Improve error message for uninitialized repository
- Better handle transient repository errors

### Rekkord 0.14

*Released on 2024-02-12*

- Rename `rekord` project to `rekkord`

### Rekkord 0.13

*Released on 2024-01-21*

- Rename `rekord log` command to `rekord snapshots`

### Rekkord 0.12

*Released on 2024-01-18*

- Combine repository ID and url to secure cache ID

### Rekkord 0.11.1

*Released on 2024-01-11*

- Use case-insensitive test for rekord CLI output format name
- Add Windows and macOS builds

### Rekkord 0.11

*Released on 2024-01-05*

- Rename exploration commands
- Fix broken compilation on Windows

### Rekkord 0.10

*Released on 2023-12-22*

- Replace object ID mentions with object hash
- Generate or prompt for passwords after config check
- Add `rekord change_id` command
- Fix broken highlight in help texts

### Rekkord 0.9.1

*Released on 2023-12-22*

- Fix possible use-after-free while snapshotting

### Rekkord 0.9

*Released on 2023-12-22*

- Add user management commands
- Support `<username>@<host>:[path]` syntax for SSH URLs

### Rekkord 0.8

*Released on 2023-12-18*

- Export master key after repository initialization
- Change `rekord export_key` to export in base64 format
- Change `rekord init` to use -R for repository URL (like other commands)

### Rekkord 0.7

*Released on 2023-12-15*

- Fix init of local and S3 rekord repositories
- Adjust names of config keys and environment variables
- Support s3:// scheme for S3 repository URLs
- Minor CLI output changes

### Rekkord 0.6

*Released on 2023-12-13*

- Fix excessive memory usage when storing big files in parallel

### Rekkord 0.5

*Released on 2023-12-12*

- Fix unbounded task queue for large put and get tasks
- Change plain output format for `rekord list`
- Minor other output changes

### Rekkord 0.4

*Released on 2023-12-03*

- Add JSON and XML list output formats
- Add `rekord tree` command to list files

### Rekkord 0.3

*Released on 2023-11-29*

- Improve rekord performance on low-core machines
- Improve error when rekord cannot reserve space for file

### Rekkord 0.2

*Released on 2023-11-16*

- Automatically create Linux cache directory if needed
- Show base64 SHA256 fingerprints for unknown SSH servers
- Support config-based SSH known fingerprint
- Restore files with temporary name until complete
- Use "default" repository username if not set

### Rekkord 0.1

- First proper release
