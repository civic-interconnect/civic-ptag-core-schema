# DEVELOPER

These repos use simple Git tags (no automation needed).
Update [CHANGELOG.md](./CHANGELOG.md) first.

### 1. Prepare the release
```shell
git add .
git commit -m "Prep vx.y.z"
git push origin main
```

After all GitHub actions pass, continue. 

### 2. Tag the release
```shell
git tag vx.y.z -m "vx.y.z"
git push origin vx.y.z
```

### 3. Verify
- The tag appears at: https://github.com/civic-interconnect/<repo>/tags
- If applicable, update CHANGELOG.md for the next release.