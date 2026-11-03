Here's how to do it using your browser's DevTools (works in Chrome, Edge, Firefox, and Brave; Safari needs one extra step noted below).

**Setup**

1. Open a website, for example `wikipedia.org`.
2. Open DevTools:
   - Windows/Linux: press `F12` or `Ctrl+Shift+I`
   - Mac: press `Cmd+Option+I`
   - Or right-click anywhere on the page and choose **Inspect**
   - Safari: first enable it under Settings → Advanced → "Show features for web developers", then use `Cmd+Option+I`
3. Click the **Network** tab.
4. Reload the page (`F5` or `Ctrl+R`/`Cmd+R`) so the requests get recorded. The Network tab only captures traffic while it's open.

**Reading the requests**

You'll see a table of requests with these columns:

- **Name**: the file or endpoint requested
- **Status**: the status code (200, 301, 404, etc.)
- **Method**: GET, POST, etc. (If you don't see this column, right-click the column headers and enable **Method**.)
- **Type**: document, script, image, fetch/XHR, and so on

Pick any 3 requests and note the method and status for each. Clicking a request opens a **Headers** panel showing the full details, including "Request Method" and "Status Code".

**Tips for finding variety**

- Most requests will be `GET` with status `200`. To find something different, try:
  - Typing in a site's search box (often triggers a `fetch/XHR` request, sometimes `POST`)
  - Logging in on a test page, which usually sends a `POST`
  - Visiting a nonexistent page like `example.com/doesnotexist` to see a `404`
  - Visiting `http://` versions of sites that redirect to `https://`, which shows a `301` or `302`
- Use the **Fetch/XHR** filter to hide images and scripts and focus on API-style calls.
- Check **Disable cache** in the Network tab if you see `304` (Not Modified) or "(memory cache)" instead of fresh 200s.

**Example log**

| Website | Request | Method | Status |
|---|---|---|---|
| wikipedia.org | wikipedia.org/ (document) | GET | 200 |
| wikipedia.org | a logo image | GET | 200 |
| github.com | a search suggestion call | GET | 200 |
| example.com | /doesnotexist | GET | 404 |

Repeat the process on 3 different sites, and record 3 requests from each if the task means 3 per site, or 3 total if it means 3 overall.

**Quick refresher on common status codes**

- `200` OK
- `301`/`302` redirect
- `304` not modified (cached)
- `403` forbidden
- `404` not found
- `500` server error

If you'd like, tell me which browser you're using and I can point to exactly where things are in its interface.