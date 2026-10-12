# Run existing checks on the Mac

The existing test workflow is manual-only. From an isolated checkout with uv and ffmpeg available, run the same existing checks sequentially:

```bash
uv run --with pytest pytest -q tests
./bin/um --help
for g in scan fal comfy sprite render3d video win backup publish kb; do ./bin/um "$g" --help > /dev/null; done
./bin/um kb check --index
./bin/um publish check .
```

These are tests, CLI help and validation; they do not publish a release. The star-chart workflow writes and force-pushes a separate branch, so it is intentionally untouched pending owner coordination. The workflows were unregistered in this fork at inventory time; that is distinct from a passing check. Do not run hosted checks or enable the dormant workflow without Austin's explicit request. Run one heavy project job at a time. Record exact commit, commands and results; Mac results do not certify Windows tools. No check system is added to repositories that lack one.
