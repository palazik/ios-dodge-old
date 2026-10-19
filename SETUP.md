# One-time activation

The automation that populated this repo could not push GitHub **workflow** files
(its token lacks the `workflow` scope). So the CI workflow is staged at
`ci/xnu.yml`. To activate it, move it into place once:

```sh
git clone https://github.com/palazik/ios-dodge && cd ios-dodge
mkdir -p .github/workflows && git mv ci/xnu.yml .github/workflows/xnu.yml
git commit -m "ci: activate xnu workflow" && git push
```

(or on github.com: create `.github/workflows/xnu.yml` and paste `ci/xnu.yml`.)

Then run it:  `gh workflow run xnu.yml -R palazik/ios-dodge`
