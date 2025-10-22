# Bio-Techne (TECH) Common Stock Shares Outstanding Explorer

This project provides a single-file, responsive HTML application to visualize the highest and lowest Common Stock Shares Outstanding for Bio-Techne (TECH) and other specified companies, based on data fetched from the SEC EDGAR API.

## Features

*   **Dynamic Data Fetching**: Retrieves `EntityCommonStockSharesOutstanding` data from the SEC EDGAR API.
*   **Filtering**: Filters data for fiscal years (`fy`) greater than 2020 and includes a numeric `val`.
*   **Max/Min Identification**: Clearly displays the highest and lowest share outstanding values and their corresponding fiscal years.
*   **Responsive Design**: Built with Tailwind CSS for a modern, mobile-friendly user interface.
*   **Dynamic CIK Loading**: Supports loading data for any 10-digit CIK via URL parameter (e.g., `index.html?CIK=0001018724`) without a page reload.
*   **SEC Guidance Compliant**: Sets a descriptive `User-Agent` for SEC API requests.
*   **Attachment Display**: Includes and references `uid.txt` as requested.

## How to Use

1.  **Save the file**: Save the `index.html` content to a file named `index.html`.
2.  **Create `uid.txt`**: Create a file named `uid.txt` in the same directory as `index.html`. Its content should be `a1b2c3d4-e5f6-7890-1234-567890abcdef` (or the actual content if provided separately). The `index.html` expects this file to be present, though its content is also embedded for direct visibility.
3.  **Open in Browser**: Open `index.html` in your web browser.

    *   **Default View**: By default, it will display data for **Bio-Techne (CIK 0000842023)**.
    *   **Custom CIK**: To view data for a different company, append `?CIK=<your_10_digit_CIK>` to the URL. For example:
        `file:///path/to/your/index.html?CIK=0001018724`
        (Replace `0001018724` with the desired CIK).

## Technical Details

*   **Frontend**: HTML, JavaScript, Tailwind CSS (via CDN).
*   **Data Source**: SEC EDGAR API.
*   **Proxy for Dynamic CIKs**: Utilizes `AIPipe` (`https://api.allpipe.io/proxy`) for fetching data from the SEC API when a CIK is provided via the URL, to mitigate potential CORS issues or rate limits on direct browser requests to SEC for arbitrary CIKs.

## Development Notes

*   The `User-Agent` header is set in JavaScript for SEC API requests. While browsers might have limitations on setting this header directly, the `fetch` call attempts to include it as per SEC guidance. When using the `AIPipe` proxy, the proxy handles the actual request to the SEC, presumably with appropriate headers.
*   The `uid.txt` content is embedded directly into the `index.html` within a `<pre>` tag for immediate visibility. An `<img src='uid.txt'>` tag is also present as per specific instructions, which assumes `uid.txt` is co-located and might render as a broken image icon since it's a text file and not an actual image.
