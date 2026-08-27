# HISTORY.md — narrative archive

> Consulted only when a session needs to know why a decision was made, not on
> every open. For what's current, read `STATE.md` instead.

This file is new as of UBI-183 (2026-08-27). Real history predating it lives
in `ubiquex`'s own `HISTORY.md` (search `UBI-138`, `UBI-139`, `UBI-151`,
`UBI-185`, `UBI-189`) and in this repo's own real `git log`/merged-PR
history, which is authoritative for what actually shipped and when.

## Real, known decisions worth carrying forward

**UBI-138/UBI-139: this repo's own real shape.** Google was one of the four
original providers consolidated into one combined repo per provider,
carrying all three languages; the shared runtime code later moved out into
its own separate `ubx-sdk-go`/`ubx-sdk-typescript`/`ubx-sdk-python` repos so
it wasn't duplicated per provider.

**`google_dlp_dlp_job`'s own real triple-repeat bug.** Fixed at the source in
`ubx-provider-dynamic` (see `ubx-schema-google`'s own `HISTORY.md`), not in
this repo — the full ripple applied here once the fix regenerated.
