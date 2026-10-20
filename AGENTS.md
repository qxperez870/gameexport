<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

## Architecture
- Keep shared Spanish workspace UI in reusable feature components with distinct content routes so navigation and page metadata stay consistent.
- Keep country-priority explanations in one shared feature component across summary, market and opportunities views so evidence limitations remain consistent.
- Use a single root session provider for account state and server functions with validated Cloud authentication for private profile reads and writes.
- Profiles use the authenticated user ID without foreign keys or triggers on managed auth schemas; lazily ensure the own profile on its first authenticated read to support email and social signups safely.
- Treat all market figures and game information in the workspace as explicitly labeled demonstration data until a real source integration is implemented.
- Pre-optimize shared hook-using UI dependencies alongside React in Vite to prevent late dependency discovery from mixing cached renderer generations.
- Premium access is decided only by server-written rows in the subscriptions table (users can read, never write their own) so payment status cannot be self-granted; the chat endpoint re-checks it on every request.
