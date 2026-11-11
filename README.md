# Pick fingerprints

This repository is a public, timestamped record of the sportsbook picks made by our football prop model.

Every time the model sees a new sportsbook pick, and before that game kicks off, the picks are written to a file and
the file's SHA-256 fingerprint is added to `hashes/<season>.csv` here and pushed. The file itself stays private until
it is published later. Each row of `hashes/<season>.csv` has the time we recorded it, a batch id, the fingerprint, the
number of picks in the batch, and the first kickoff in the batch.

## How to check a file once it is published

1. Take the picks file exactly as published (do not open and re-save it; any change, even one byte, changes the
   fingerprint).
2. Compute its SHA-256 (for example `sha256sum FILE`, or `certutil -hashfile FILE SHA256` on Windows).
3. Find the row in `hashes/<season>.csv` with the same batch id. The fingerprint must be identical.
4. The time we pushed that row is recorded independently of us by GitHub's public event archive (GH Archive), so the
   row cannot be quietly back-dated.

The first line of each picks file is a random salt, so a fingerprint cannot be guessed from the picks.

The picks files are published later.
