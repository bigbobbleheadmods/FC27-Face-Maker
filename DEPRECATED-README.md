# 🛑 Deprecated versions (kill switch)

`deprecated-versions.json` lists FC27 Face Maker versions that should stop working and ask users to update.
The app's kill switch reads the same two fields from the update feed (the gist). This file is a standalone, public copy you can mirror into the gist.

## Fields

| Field | Meaning |
|---|---|
| `blocked_versions` | List of version patterns to block. Empty `[]` means nothing is blocked. |
| `blocked_message` | Optional. The text users see when their version is blocked. If you leave it out, the app uses its default message. |
| `updated_at` | The date you last changed the list (YYYY-MM-DD). This is just for your reference. |

## Pattern types

| Pattern | Blocks |
|---|---|
| `"1.0.0"` | **Exact:** only version 1.0.0 |
| `"1.0"` | **Prefix:** 1.0, 1.0.0, 1.0.1, and so on |
| `"1.0.*"` | **Wildcard:** every 1.0.x version |

## How to block a version later

1. Open `deprecated-versions.json` (and/or the update gist).
2. Add the version(s) to the list, for example:
   ```json
   "blocked_versions": ["1.0.0"],
   ```
3. Optionally change `blocked_message`, then set `updated_at` to today's date.
4. Check the JSON is valid: quotes, commas, and no trailing comma.
5. Save or commit. Users on a blocked version see the message the next time the app checks.

⚠️ **Never block the current release.** Make sure the version in the gist's `"version"` field isn't matched by any pattern, or everyone gets locked out.
To undo a block, remove the pattern and save.
