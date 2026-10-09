# MuseFlow MVP — Requirements

## Required

1. Google Chrome or Chromium
2. A Muse.ai account
3. A signed-in Muse chat tab in the same Chrome profile

MuseFlow itself has **zero npm/pip dependencies**. The supplied folder is already a loadable Chrome extension. After replacing files, open `chrome://extensions` and click Reload on MuseFlow. The Muse session check runs automatically on canvas open and when a Muse tab finishes loading.

MuseFlow uses the signed-in Muse.ai tab directly and no longer requires `muse2api`, an API key, or a local backend. Keep the Muse chat tab open while generating. Text-to-image is supported; reference-image upload is not yet implemented. The integration follows Muse's current page UI and may need updating if Muse changes its interface.
