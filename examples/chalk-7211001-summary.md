<!-- Example step 10 chat summary for examples/chalk-7211001.md. Punch test passed: a fresh reader, given only this summary, named both Watch out risks and both moves. -->

# chalk in 60 seconds

**What it is:** A Node library that wraps text in terminal color codes. You chain style names, such as `chalk.red.bold`.
**Watch out:** The color tables and terminal detection are copied code with no upstream version recorded. Installs are unpinned, because the repo has no lockfile (a file fixing exact package versions).
**Scope:** commit `7211001`, examined 2026-11-18. Read 100% in full, skimmed 0%; the rest is three image files, unread. No code ran. 163 of 168 citations passed; most failures were claims wider than their cited lines.

**1. "No dependencies" hides copied code.** The package declares 0 runtime dependencies. Copied code in `source/vendor/` does the color and detection work, with no upstream version recorded.
➜ **Do:** If you audit chalk, compare `source/vendor/` with upstream releases.

**2. Installs are not pinned.** The repo has 0 lockfiles; `.npmrc` (npm settings) sets `package-lock=false`.
➜ **Do:** Contributors should pin versions themselves.

**3. No network or file code.** A whole-`source/` search found 0 matches for file, network or program-launch code.
*A shop with no back door.*

**README:** ❌ 1 unsupported ("Clean and focused" is a judgment) · ✅ Matched, with limits: 38 supported, 12 partly supported (2 rest on a failed check) · ❔ 7 need a run to judge
**Safety:** The whole-checkout hidden-text scan found 1 long-line hit, an image file with no text. It found 0 invisible characters and 0 `<!--` comments. No instructions aimed at an AI were found. The report records no secrets scan.
Proof: [`chalk-7211001.md`](chalk-7211001.md).
