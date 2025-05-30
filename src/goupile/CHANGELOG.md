# Goupile changelog

## Goupile 3.10

### Goupile 3.10.2

*Released on 2025-04-05*

- Reduce length of demo project names

### Goupile 3.10.1

*Released on 2025-04-04*

- Increase demo pruning delay to 7 days
- Fix early timeout when creating big archives from admin panel

### Goupile 3.10

*Released on 2025-04-03*

- Add `meta.count()` for custom sequential counters
- Add `meta.random()` for low-level for randomization
- Restore empty record summaries (regression introduced in Goupile 3.9)
- Improve some database schema migration steps
- Fix empty space in main toolbar
- Drop per-store sequence numbers (unused)
- Drop custom signup system (unused)

## Goupile 3.9

### Goupile 3.9.3

*Released on 2025-03-30*

- Add several syscalls to seccomp sandbox for ARM64 compatibility
- Fix startup crash in ARM64 Debian package
- Close demo warning after small delay

### Goupile 3.9.2

*Released on 2025-03-28*

- Keep active record after guest save
- Fix mismatch code/preview widget highlighting
- Fix internal server error related to record claims
- Improve demo mode:
  * Support reuse if random project URL is saved
  * Use JS to create demo instance to avoid project creation caused by HTTP probing
  * Clean up demo instances after two days
- Clean up authentifcation code
- Fix broken Windows build
- Reduce input auto-zoom issues on iPhone

### Goupile 3.9.1

*Released on 2025-02-21*

- Fix sequence value in exports

### Goupile 3.9

*Released on 2025-02-21*

- Fix incoherent completion status with disabled pages
- Implement proper per-thread sequential IDs
- Always show Continue button on sequenced pages
- Add app-global annotation setting
- Fix various variable tag inconsistencies
- Keep legacy record sequence values and HID
- Use simpler version numbers

## Goupile 3.8

### Goupile 3.8.3

*Released on 2025-02-17*

- Fix "page is undefined" error when navigating some pages
- Remove column masking heuristic from legacy exporter
- Include multi-valued null columns in legacy exports
- Keep ULID suffix in virtual export tables
- Fix migration FKEY errors with split projects and deleted records
- Fix SQL error when restoring archive
- Add root endpoints to exit goupile process
- Send internal server error details to root users

### Goupile 3.8.2

*Released on 2024-12-29*

- Fix possible infinite loop after failed HTTP request
- Hide forget action when autosave is in use
- Refuse compressed HTTP request bodies

### Goupile 3.8.1

*Released on 2024-12-20*

- Skip confusing Save button when Next is available
- Fix concurrency issue between autosave and confirm in legacy instances
- Replace code icon with design icon in legacy instances
- Update browser version requirements

### Goupile 3.8.0

*Released on 2024-12-20*

- Drop *New* user permission in favor of page `claim` option
- Improve support for dynamic `enabled` page option
- Add support for optional confirmation when saving page (option `confirm`)
- Always show status suffix in left menu
- Use different icons for conception menu and code panel
- Fix error when emptying user email or phone
- Fix stuck loading when record does not exist
- Avoid erroneous "confirm changes" dialog after code change
- Drop ill-designed export filter and dialog options
- Reduce unexpected errors caused by duplicate file changes
- Avoid noisy "single SQLite value" error when saving legacy records

## Goupile 3.7

### Goupile 3.7.7

*Released on 2024-11-23*

- Fix unsorted instances leading to duplicates and deadlocks (regression introduced in Goupile 3.7.3)

### Goupile 3.7.6

*Released on 2024-11-16*

- Enable development mode by default for demo instances
- Switch to form editor tab until it is explicitly changed
- Fix possible crash on mode change

### Goupile 3.7.5

*Released on 2024-11-12*

- Fix recurent crash in demo mode

### Goupile 3.7.4

*Released on 2024-11-12*

- Fix premature HTTP timeout when exporting data from legacy instance

### Goupile 3.7.3

*Released on 2024-11-12*

- Fix deadlocks after password change and TOTP activation
- Fix badly ordered sub-projects in admin panel
- Fix errors with empty email and phone user attributes

### Goupile 3.7.2

*Released on 2024-11-12*

- Restore missing Administration link in profile menu
- Switch to proper export buttons in legacy instances

### Goupile 3.7.1

*Released on 2024-11-07*

- Adjust default password constraints:
  * Moderate for normal users and project administrators
  * Hard for root users

### Goupile 3.7.0

*Released on 2024-10-31*

- Change `thread` object in scripts: `thread['form']` becomes `thread.entries['form']`
- Support custom category-level scripts
- Support custom content in form level elements
- Support custom form tile icons
- Increase height of top and bottom menu bar
- Center mobile action buttons when relevant
- Show home icon before main menu item
- Make menu categories clickables
- Switch to spaced buttons for enumerations
- Scroll to top on page change
- Simplify automatic sequencing of forms
- Support setting custom classes for most widgets
- Fix empty space at the bottom of forms on mobiles
- Improve styling and text of error boxes
- Fix broken "changed" attribute for widgets
- Fix broken `form.time()` widget in legacy Goupile
- Fix error tags showing up for delayed errors
- Reduce available annotation statuses in locked mode
- Target ES 2022 for `top-level await` support
- Introduce basic mail signup system

## Goupile 3.6

### Goupile 3.6.4

*Released on 2024-09-05*

- Fix default panels when building and opening URLs
- Fix infinite loop when assembling export structure
- Fix FOREIGN KEY bug when saving data in multi-center projects
- Fix incomplete app homepage option
- Fix disabled "Publish" button after adding file
- Switch to new HTTP server code in goupile
- Use mimalloc on Linux and BSD systems

### Goupile 3.6.3

*Released on 2024-07-26*

- Fix a possible crash when sending mails
- Expose hash and CRC32 functions to scripts
- Expose more utility functions to scripts

### Goupile 3.6.2

*Released on 2024-07-11*

- Fix navigation bugs in goupile (including main "Add" button not working)

### Goupile 3.6.1

*Released on 2024-07-10*

- Expose thread object in user scripts to access sibling entries
- Fix mandatory markers showing up on calc widgets

### Goupile 3.6.0

*Released on 2024-06-28*

- Add basic entry summary to replace old HID system
- Show list of entries when normal users connect
- Fix broken export endpoint for legacy instances
- Fix various offline cache and profile sync bugs
- Fix undefined username in initial password change dialog
- Fix broken automatic relogin after expiration
- Fix database migration error from some Goupile versions
- Fix some parsing errors in save endpoints
- Fix infinite spinner for late startup errors
- Clean up lock related code in the client

## Goupile 3.5

### Goupile 3.5.3

*Released on 2024-06-20*

- Fix compatiblity with legacy server-side locks
- Fix various client-side locking bugs
- Allow scripts to use lit `until` directive

### Goupile 3.5.2

*Released on 2024-06-20*

- Fix unstyled widget labels in legacy instances
- Fix esbuild.wasm fetch for non-Brotli content encodings
- Use identity when Content-Encoding is missing or empty
- Build Debian packages for ARM64

### Goupile 3.5.1

*Released on 2024-06-18*

- Add pushPath/popPath system to replace "path" widget option
- Use legacy form code in legacy instances
- Drop forced low-complexity password change for now
- Fix failure to enable develop mode in multi-center projects
- Expose PeriodPicker widget to legacy instances
- Clean up leftover debug statements

### Goupile 3.5.0

*Released on 2024-06-17*

- Support running legacy (v2) Goupile projects
- Bundle page scripts with esbuild to support import and provide better syntax error reports
- Fix non-unique HTML ids in generated forms
- Fix various offline bugs

## Goupile 3.4

### Goupile 3.4.0

*Released on 2024-03-22*

- Simplify goupile top menu
- Change automatic form page with separate levels and tiles
- Improve goupile task menu on small screens
- Refuse excessive password lengths
- Fix export key error when guest sessions are enabled
- Automatically create session when guest saves data
- Improve page redirection in sequence mode

## Goupile 3.3

### Goupile 3.3.6

*Released on 2024-02-08*

- Improve data migration from goupile2

### Goupile 3.3.5

*Released on 2024-01-26*

- Reduce permissions for demo users
- Assign export keys to master instance

### Goupile 3.3.4

*Released on 2024-01-24*

- Add option to disable SQLite snapshots
- Disable SQLite snapshots in demo domains

### Goupile 3.3.3

*Released on 2024-01-22*

- Warn user about demo mode
- Fix HTTP property being set from Defaults section

### Goupile 3.3.2

*Released on 2024-01-22*

- Add demo mode to Goupile
- Show username on password change dialog

### Goupile 3.3.1

*Released on 2024-01-22*

- Add hover effect to tiles
- Disable Publish button if main script does not work

### Goupile 3.3.0

*Released on 2024-01-20*

- Show completion tiles for groups of forms
- Show first-level columns and stats in data table
- Show basic record status in menus
- Support basic form sequence configuration
- Reintroduce support for page filename option
- Keep explicitly defined single-child menu relations
- Fix missing menu items in some cases
- Fix panel blink when clicking on current page menu item
- Drop broken offline login code for now
- Fix crash when requesting '/manifest.json'
- Improve main.js fallback code when guest sessions are enabled

## Goupile 3.2

### Goupile 3.2.3

*Released on 2024-01-17*

- Fix UI deadlock in develop mode

### Goupile 3.2.2

*Released on 2024-01-16*

- Fix support for repeated sections and notes
- Fix undefined variable error while exporting
- Fix minor deadlock issues

### Goupile 3.2.1

*Released on 2024-01-16*

- Fix missing code for record deletion
- Improve selection of visible data columns
- Handle modification time on the server
- Build with JavaScriptCore

### Goupile 3.2.0

*Released on 2024-01-14*

- Add configurable password complexity checks to goupile
- Fix generic 'NetworkError is not defined' error
- Fix error when creating multi-centric projects
- Fix possible NULL dereference in goupile login code
- Allow reset of email and phone in goupile admin panel
