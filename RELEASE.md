## Cutting a Release

### Prep

- Ensure `enhance` branch is up to date
- Update CHANGELOG and docs if needed
- Decide the next SemVer: <MAJOR.MINOR.PATCH>

### Create the Release (this creates the tag)

#### UI Method:

1. Go to **Releases** → **Draft new release**
2. Choose target: `enhance`
3. Tag: enter new tag (e.g. `v1.2.3`) — GitHub will create it
4. Add title/notes → **Publish release**

#### CLI Method (optional):

```bash
gh release create v1.2.3 --target enhance --generate-notes
# or add -t/ -n for custom title/body
```

### Major Tag Update

- A workflow automatically updates the floating major tag (e.g. `v1`) to point at this release
- Consumers using `uses: cloud303/tf-via-pr@v1` get the latest `v1.x.x`
- Consumers pinned to `v1.1.0` remain on that exact version

### Post-release Checks

- Verify the release page and that `v1` now points to the new commit
- If needed, mark pre-releases; consider skipping the major-tag move for pre-releases

> [!TIP]
> Don't push tags directly to `enhance` unless you're intentionally cutting a release. Use the Release flow above.