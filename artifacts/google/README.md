# artifacts/google

UBI-240 slice 6: the canonical home for this provider's own docs/codegen
artifacts, moved here from `ubiquex-docs` (where they lived under the
mismatched name `artifacts/gcp/` — every other provider's own directory
matches its `ubx-sdk-<provider>` repo name exactly; this was the one
real exception). See `ubx-sdk-kubernetes`'s own
`artifacts/kubernetes/README.md` for the full account of why this
moved (UBI-102's own comment thread).

- **`descriptions.json`** / **`intros.json`** / **`categories.json`** /
  **`exclusions.json`** — real source of truth, read by
  `ubx-docs-providers` at build time.
- **`google.json`** — codegen-ready export (`{resource: {relPath:
  text}}`, qualifier-stripped, HTML-unescaped). What `ubx sdk gen
  --descriptions-dir artifacts/google` actually reads. Never edited
  directly.

**A real, confirmed provider-display quirk**: pass `"GCP"`, not
`"Google Cloud"` (`providers.py`'s own registered `provider_display`
in `ubiquex-docs`), to `export_raw_descriptions.py` for this provider
specifically. The published SDK code's own qualifier suffixes were
baked in as "...computed by GCP.", not "...computed by Google Cloud." —
confirmed by a real byte-identical diff against currently published
code; the wrong display string leaves the qualifier unstripped since
the match is exact-string, not fuzzy.

To update: edit `descriptions.json` here, then regenerate `google.json`
from a sibling `ubiquex-docs` checkout:

```bash
ubx sdk gen --only google --dump-ir /tmp/dump --out /tmp/unused
cd ~/Ubiquex/ubiquex-docs/scripts/resource-reference-gen
python3 export_raw_descriptions.py google "GCP" \
    --dump-root /tmp/dump/google \
    --descriptions-path ~/Ubiquex/ubx-sdk-google/artifacts/google/descriptions.json \
    --nested-out ~/Ubiquex/ubx-sdk-google/artifacts/google/google.json
```

Commit both files together.
