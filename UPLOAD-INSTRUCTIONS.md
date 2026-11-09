# Upload instructions

The GitHub integration rejected writes with HTTP 403: Resource not accessible by integration. No repository changes were published.

1. Open the existing repository on GitHub and choose Add file → Upload files.
2. Upload README.md, INTERMEDIATE-QA.md, PRACTICE.md, and LEGACY-README.md from this package. Replace only README.md; retain the existing interview Markdown and PDF.
3. Commit the files to the desired branch.
4. In repository Settings → General, change the repository name to Intermediate-CS-Study-Guide-India if available. The connector does not expose this action.
5. The repository was already public when inspected on 9 November 2026; no visibility change is necessary.

Alternatively, reconnect GitHub with repository contents write permission and ask to publish this package. Repository administration capability is also needed for renaming.

Verification: all executable workbook Python checks and SQLite result assertions passed on Python 3.12.10. The guide contains 60 consecutively numbered questions. Existing interview files are referenced by their unchanged paths and are not bundled here.
