# ![App](lucide://Sparkles?color=%23fb923c&size=26) DeskMemory — User guide

A friendly tour of the desktop app. Your files stay **on your computer** in one folder you set up on first launch—the **memory the AI uses when you chat**.

> **Built into the app.** This guide is shipped inside DeskMemory (not read from your vault or the `.rebel` folder). You can open it anytime from **Help** ![Help](lucide://CircleHelp?color=%23fb923c&size=16) in the top bar. Editing `Docs/user-manual.md` in the source project updates the next app build.

---

## ![Contents](lucide://BookOpen?color=%23fb923c&size=22) On this page

- [First launch and your folder](#first-launch-and-your-folder)
- [Settings overview](#settings-overview)
- [Billing and quota alerts](#billing-and-quota-alerts)
- [Files workspace and Chat workspace](#files-workspace-and-chat-workspace)
- [Chat with AI (gateway)](#chat-with-ai-gateway)
- [Saving a chat thread to the vault](#saving-a-chat-thread-to-the-vault)
- [Compressing a long chat thread](#compressing-a-long-chat-thread)
- [Vault save automation](#vault-save-automation)
- [Prompt compiler (from search results)](#prompt-compiler-from-search-results)
- [The file list](#the-file-list)
- [Icons in the list](#icons-in-the-list)
- [Opening and editing a note](#opening-and-editing-a-note)
- [Saving](#saving)
- [Note details (pasted or old files)](#note-details-pasted-or-old-files)
- [Include in vault search](#include-in-vault-search)
- [Tuning meaning-based search](#tuning-meaning-based-search)
- [Bringing files in from disk](#bringing-files-in-from-disk)
- [Import, move, and organize](#import-move-and-organize)
- [Common questions (Q&A)](#common-questions-qa)
- [Tips](#tips)

---

## ![Folder pick](lucide://FolderOpen?color=%23fbbf24&size=22) First launch and your folder

When you start DeskMemory, pick **one** folder for your files. Most people tap **Get started** — DeskMemory creates the default folder under **Documents** (typically `…/Documents/DeskMemoryVault`). That is all you need.

**More options** (collapsed by default): see the exact path, **Create and use this folder** again, **Choose a different empty folder…** (must be completely empty), or **Use a folder that already has your files…** when moving from another computer.

Only note-style files (Markdown) appear in the sidebar; for a fresh start, use an empty folder so mixed folders are not misleading.

The current library path appears under the app name in the top bar. With **Advanced settings** enabled, it is also shown read-only in **Settings → File Settings** (it cannot be relocated from Settings). To bring files in from elsewhere, use **drag-and-drop**, **paste**, sidebar **Add file…**, or—with advanced on—**Settings → File Settings → Import Markdown from folder…** for bulk top-level Markdown. See [Bringing files in from disk](#bringing-files-in-from-disk).

When you create a **new** library (recommended or empty-folder path), DeskMemory:

- Adds a welcome note as `README.md` when that name is free, or `DeskMemory-Welcome.md` if `README.md` already exists. The note includes the DeskMemory logo and opens in **preview** once—the first time only after that setup.
- Creates an empty **`DeskMemory-packs/`** folder and shows **Boost your AI memory** so you can optionally install **memory packs** (curated Markdown for chat—e.g. marketing, branding, recipes). Pick any packs or **Skip for now**; add more anytime under **Settings → Chat Settings → Memory packs**. All packs are free. DeskMemory does not overwrite pack files you already have.

Choosing **Use a folder that already has your files…** does not add the welcome note or memory-pack onboarding (your existing library stays as-is). Older libraries may still contain **`AI-starter-context/`** from previous app versions.

---

## ![Settings](lucide://Settings?color=%23c4b5fd&size=22) Settings overview

Open **![Settings](lucide://Settings?color=%23c4b5fd&size=18) Settings** from the top bar. The dialog opens on **Account**; use the sidebar to switch sections:

- **Account** — Sign in with your **DeskMemory** Supabase account (email + password). Chat **send** uses the API gateway; your session persists across restarts. When signed in, see **Plan & billing** (plan name, subscription status, **Refresh**), **Message usage** breakdown (plan allowance + message packs), and links to the **web dashboard** (plans, message packs, billing). Sign out here when needed. At the bottom of this page, **Advanced settings** reveals **File Settings** and other power-user options (indexing, search debug, vault save automation).
- **Chat** — **Memory packs** in the chat header (install + **Start in chat**). **Chat Settings** — same packs list under **Memory packs** (download curated notes into `DeskMemory-packs/`). **Prompt creation**: vault **categories**, **tag suggestions**, **role** text, **output format presets**, and **prompt templates** (for [compile prompts](#prompt-compiler-from-search-results) and chat templates). With **Advanced settings** on: **Vault save automation** (AI prefill, silent save gate) and **Chat preferences** (max vault files per send, up to **10**). Chat send, **Compress…**, and **Save to vault…** use **Account**—no provider API keys.
- **File Settings** *(advanced only)* — **Markdown library** path (read-only), **Import Markdown from folder…** (bulk top-level `.md` import), **File viewer** (optional indexing and metadata badges in Files), and **Capture & search** (Quick Capture shortcut, embeddings index, semantic strictness / debug tuning — see [Tuning meaning-based search](#tuning-meaning-based-search)). Hidden until **Advanced settings** is checked on **Account**.

---

## ![Billing](lucide://CreditCard?color=%23fbbf24&size=22) Billing and quota alerts

When you are **signed in**, DeskMemory keeps your **plan**, **message usage**, and **billing status** in sync with the web dashboard and API gateway. Billing actions (upgrade, buy packs, update payment) always open the **web** in your system browser—the desktop app does not embed checkout or store payment keys.

### Global banners (Files and Chat)

These appear **below the top bar** on every main screen until the situation changes:

| Banner | When | What to do |
|--------|------|------------|
| **Payment failed** (amber) | Lemon Squeezy subscription status is `past_due` | **Update payment details** → web billing page |
| **Subscription cancelled** (sky/neutral) | Status is `cancelled` | Shows access-until date; **Manage subscription** on web to resume |
| **Monthly quota reached** (red, compact strip) | `quotaPeriodExceeded` is true | **Top-up messages or upgrade** → web message-packs section |

If you have a **scheduled plan downgrade**, a short line may appear under payment or cancel banners with the effective date.

State refreshes on **sign-in**, when the app window **regains focus**, and after gateway quota fetches (same cadence as the chat usage badge).

### In Chat

- The chat header repeats **quota exceeded** and **payment failed** alerts when relevant.
- Hitting the limit while sending shows **Monthly quota reached** with a **Top-up messages or upgrade** link.
- The **usage badge** in the chat header summarizes plan % used and messages left; hover for the full breakdown and web links (same as **Settings → Account**).

---

## ![Workspace](lucide://Folder?color=%23fb923c&size=22) Files workspace and Chat workspace

Next to the theme control, the **Files / Chat** control switches the main area:

- **Files** (folder + file-tree icon in the app) — Your vault browser and note editor (this guide’s file list, search, and editing sections).
- **Chat** (speech-bubble icon in the app) — In-app chat via your DeskMemory account (API gateway).

Your choice is remembered for next launch (`deskmemory.workspaceMode`). **Chat** does not replace closing the app — use the window **close** control; you may be asked to confirm quitting.

---

## ![Chat](lucide://Sparkles?color=%23fb923c&size=22) Chat with AI (gateway)

Sign in under **Settings → Account** (or use **Sign in** in the top bar when signed out). Open **Chat** from the workspace toggle.

- **Mode** — **Fast (everyday)** uses the gateway’s general model (DeepSeek v4 Flash); **Research (deeper)** uses the research model (DeepSeek v4 Pro). You do not pick provider API keys for ordinary chat send.
- **Monthly cloud usage** — When signed in, the chat header shows a compact **usage badge** (plan % used and messages left, e.g. “72% of plan used · 1,240 left” or “Plan used · 500 pack left”). Hover for the full breakdown: plan allowance (resets each billing period; unused plan messages expire), **message packs** (purchased extras that **never expire**), and **total available**. Links open the web dashboard to **upgrade**, **buy packs**, or manage **billing**. The same breakdown appears under **Settings → Account**. See [Billing and quota alerts](#billing-and-quota-alerts) when limits or payment status need attention.
- **Open chats** — The collapsible **Open chats** rail on the left lists draft sessions (hide/show with the panel control; a badge shows how many are open). The **active chat is always shown at the top** of the list; click another row to switch (and move it to the top). A spinning icon on a row means that chat is still streaming. Close with **×** on a row (you may be asked to **save to vault first** or confirm delete; closing aborts an in-flight reply for that chat). **New chat** in the header starts another session with **Settings defaults** and **empty attachments**. **Composer drafts** (text you typed but have not sent yet) are **remembered per chat** when you switch chats, search in Files, or restart the app.
- **Chat settings (per chat tab)** — Expand **Chat settings** above the message area for **Mode**, **Web search**, **Tone**, **Template (role + format)**, **Rich replies**, and **Display** (Formatted vs Raw Markdown). Each **open chat tab** remembers its own bundle—switch tabs and the accordion restores that chat’s choices. Changing settings **in chat** updates **only the active tab**, not your other open chats. **New chats** copy defaults from **Settings → Chat preferences** (tone, display, web search, etc.). Summary chips on the collapsed row show your current choices. **Instruction preview** at the bottom shows the tone instruction sent to the gateway (including the same-language rule and optional template).
- **Web search** — **Web: Auto / Always / Off** works in **Fast** and **Research**. **Auto** runs a Brave web search when the gateway decides fresh facts are needed; **Always** searches on every send; **Off** never searches. Web search uses your account quota when it runs. During a search you may see a short status line; when results arrive, assistant replies include a **Web sources** block (clickable links, shown above the answer and kept visible while streaming). If search is skipped or fails, a notice appears only for that case.
- **Research reasoning** — In **Research** mode, the model’s intermediate **Reasoning** appears in a collapsible block **above** the final answer (opens automatically while streaming). Copy on an assistant message includes reasoning and answer when both exist.
- **Tone** — Preset styles (default, concise, friendly, professional, coach, creative) are sent to the gateway with each message. The assistant also follows a fixed rule: **reply in the same language as your latest message** (no separate language setting).
- **Vault note bodies** — Removed Lean/Normal/Full slicing (ADR 15). Full bodies are sent up to inject limits; see [Vault inject limits](#vault-inject-limits).
- **Template (role + format)** — Optional vault template adds **role** and **output format** to the gateway tone instruction (shown in **Instruction preview** when selected).
- **Vault context on send (per chat tab)** — Each chat tab has its **own** vault attachment list. When you activate a chat, **Top relevant matches** checkboxes in the Files workspace mirror **that tab’s** attachments. Files you add with **+** beside the composer attach to the **active chat only**. On **Send**, those paths are read from disk and sent as **inject context** (full note bodies; YAML front matter always included). A banner shows how many selected files are attached and the per-send cap from **Settings → Chat Settings**. If a file is **empty**, **too large**, or **total attach** exceeds limits, send is **blocked** with a clear message (see [Vault inject limits](#vault-inject-limits)).
- **Persistence** — Messages and per-tab settings live in **local SQLite** and **restore after restart** until you close a chat from the rail or **save to vault**. Labels use your **first user message** preview (or a saved title). Only **one** chat is visible at a time; the rail holds the rest; background streams continue when you switch away.
- **Header actions** — **Save to vault…** and **Compress…** use your DeskMemory account (same sign-in as chat send). Sign in via **Settings → Account** when either action is disabled.
- **Message area** — **Enter** sends; **Shift+Enter** inserts a new line. The round **up-arrow** button sends the same way. **Stop** appears while a reply is streaming.
- **Copy** — Each message has a copy icon for that turn’s text (assistant copies include reasoning when present). The small copy control beside the composer copies the **draft** only (disabled when the draft is empty). After a successful copy, a short **toast** at the bottom confirms it.

**Draft vs vault:** Ephemeral chat is **not** indexed for meaning-based vault search and **not** a vault file until you **save to the vault** (or paste elsewhere). A line under the chat title reminds you while you work.

---

## Vault inject limits

When you attach vault files to chat, DeskMemory sends **full note bodies** (YAML front matter is always included). Files on disk are never modified.

To prevent abuse and runaway token cost, each send has limits:

| Limit | Value |
|-------|-------|
| Per file (body) | **150,000 characters** (~40 pages of typical notes) |
| Total (all attached files) | **500,000 characters** |
| Empty body | Not allowed |

If a file exceeds a limit, you see an error naming the file and the limit—you can split the note, attach fewer files, or use search to pick smaller pieces. **Writing a book in the vault is fine**; attaching an entire manuscript in one message is not.

---

## ![Vault from chat](lucide://FolderOutput?color=%23fb923c&size=22) Saving a chat thread to the vault

Use **Save to vault…** in the chat header when you want a **durable vault note** from the current chat.

1. **Summarize (background)** — The app asks the **DeskMemory gateway** to turn the thread into a **standalone Markdown note**. This often takes **1–2 minutes** on long threads. The app **does not freeze**: a **banner** at the top shows progress (Summarizing… / Classifying…) and you can switch to **Files** or other chat tabs while you wait. **Cancel** stops the in-flight request. Only **one** vault summary runs at a time; other **Save to vault…** buttons stay disabled until it finishes or you review the result.
2. **Review** — When the summary is ready, a toast and the banner offer **Review & save**, which opens the same **Save** dialog you use elsewhere (title, type, category, tags, path). The default document type is **note**; the first `#` heading helps suggest the filename. If the gateway call fails, you still get a short draft you can edit.
3. **After save** — On success, the chat **closes** (removed from **Open chats**), the session is marked as exported, and a **toast** confirms the vault path. Your new file is a normal vault note (searchable when not opted out, same as any other save).

**AI prefill (optional)** — When **AI prefill** is enabled under [Vault save automation](#vault-save-automation), the gateway may **classify** the note before the dialog opens so **category** and **tags** arrive prefilled (and new tags can be added to your taxonomy). If classification fails, the dialog opens with a notice so you pick category and tags yourself. You should still review them before saving.

**Silent save (optional)** — When **Silent save** is enabled *and* your vault has reached the **reviewed-save gate** (see [Vault save automation](#vault-save-automation)), a later **Save to vault…** can write the file **without opening the dialog** when the gateway returned both a valid title **and** classification—then show a **toast** instead. If classification is missing, the dialog opens even when silent save is on.

---

## ![Compress](lucide://Scissors?color=%23fb923c&size=22) Compressing a long chat thread

**Compress…** reduces **token-heavy** back-and-forth while keeping your **first user message** (everything from the start of the thread through that turn) **unchanged**. All **later** turns are removed and replaced by **one** new assistant message: a **Markdown summary** from the gateway of what was cut (facts, decisions, code, errors, open items).

- **When it is available** — You need a first user message, at least one follow-up turn, and roughly **12,000 characters** of text in that **tail** (combined length of messages after the first user turn). A thin **progress bar** above the button fills toward that minimum so you can see how close you are.
- **Long-thread reminder** — When **all message bodies** add up to about **150,000 characters**, an **amber banner** suggests compress (or save to vault). At about **200,000 characters**, a **dialog** asks you to compress (or start a new chat). Neither blocks sending ([details](#what-is-the-amber-long-thread-banner)).
- **Confirm** — The dialog explains that tail content is replaced by one account-backed summary; confirm to run. A busy overlay runs while the gateway works.
- **Trade-off** — You no longer have the exact wording of removed turns—only the summary—so copy anything critical **before** compressing if you need it verbatim.

---

## ![Vault save automation](lucide://Tags?color=%23c4b5fd&size=22) Vault save automation

Open **![Settings](lucide://Settings?color=%23c4b5fd&size=18) Settings → Chat Settings**. Enable **Advanced settings** at the bottom of **Account** first—the **Vault save automation** section (below Prompt creation) is hidden until then. It controls chat → vault behavior:

- **Reviewed saves** — Each time you complete a **Save** from the chat export flow **through the dialog** (not silent), a counter increases. This represents saves you have **eyed and confirmed**.
- **AI prefill** — When checked, saving from chat asks the **gateway** to suggest **category and tags** (and extend your tag list) before you commit.
- **Silent save** — When checked, **Save to vault…** may skip the dialog after the gateway returns a valid note **and** classification. This checkbox stays **disabled** until the counter reaches the app’s **gate** (20 reviewed saves for that vault), so silent mode only turns on after deliberate practice with the form.

Changing library folder reloads these prefs for the new vault path.

---

## ![Compile](lucide://Cpu?color=%23fbbf24&size=22) Prompt compiler (from search results)

When a **meaning-based** search shows **Top relevant matches** under the sidebar search box, you can tick one or more files, then click **Create prompt**:

1. A short wizard confirms **category** and **tags** per selected file (aligned with **Settings → Chat Settings**).
2. A second step sets **role**, optional **request** text, and **output format**, then **Compile to clipboard** and/or **Add to chat** (opens the Chat workspace and drops the compiled text into the message box; selected ranked files still feed chat context when you send).

You can optionally save the compiled text as a new vault note through the normal classified-save flow. Configure categories, templates, and output presets in **Settings → Chat Settings** so the wizard matches how you work.

---

## ![Tree](lucide://Folder?color=%23f59e0b&size=22) The file list

The **left panel** is your vault tree:

- **Folders** — ![Closed](lucide://ChevronRight?color=%2371717a&size=16) or ![Open](lucide://ChevronDown?color=%2371717a&size=16) next to ![Folder](lucide://Folder?color=%23f59e0b&size=18) **folder** rows: click the row to expand or collapse and show files **nested underneath**. All folders stay visible in the tree so you can drag files between them. Each row shows the **file or folder name only** (not the full `Folder/file.md` path); hover for the full vault path.
- **`.md` files** — open in the **right panel** when you click them. Opening from **Recent**, **Quick open**, or search expands ancestor folders so the file is visible in the tree.
- **![Search](lucide://Search?color=%23c4b5fd&size=18) Find files by name** — narrows the list to **Markdown file names** that contain **all** the words you type (spaces separate words; not the note body, not folder names). Files **excluded from vault search** stay hidden here too. Clear the box to show the full tree again.
- **Quick open (Ctrl+P / ⌘P)** — opens a palette to jump to a searchable Markdown file. **Recent** paths appear first when the box is empty. Start with **`~`** for **meaning-based** matches (vault embeddings; desktop app with a vault). Without `~`, the palette filters by **path and file name** (like the sidebar search words, but it does **not** add hybrid semantic ranking—use `~` for that). Press the shortcut again to close the palette. **Recent files** under the search box is a **collapsible** row (chevron): expand it to open recent paths quickly (stored per vault on this computer).
- **![Settings](lucide://Settings?color=%23c4b5fd&size=18) Settings** — library folder, prompt creation (taxonomy / templates), capture & search, account, and chat preferences (see [Settings overview](#settings-overview)).
- **Paste imported files** — copy one or more **`.md` files** in Explorer/Finder, click somewhere in the app (not inside a text editor field), then press **Ctrl+V / ⌘V** to import them into the selected folder context (same parent logic as **New file**). This is separate from normal text paste while editing a note.
- **![Refresh](lucide://RefreshCw?color=%23c4b5fd&size=18) Refresh** — reloads the list from disk.
- **![New file](lucide://Tags?color=%23c4b5fd&size=18) New file** — opens the **Save** (classified) dialog to create a **new** vault note with title, type, category, tags, and placement. The default parent folder follows your current list selection when it makes sense (otherwise vault root).
- **![Add file](lucide://Upload?color=%23c4b5fd&size=18) Add file…** — opens the OS file picker for **exactly one** **`.md` or `.pdf`** file (both types appear in the same list). Markdown bodies go into the **Save** flow; PDFs are **text-extracted** locally (up to **20 pages** per file so the note stays usable in search and AI chat), then **Save** for category/tags. Scanned PDFs with no text layer, or very long PDFs, may fail with a clear message.

---

## ![Legend](lucide://Sparkles?color=%23fbbf24&size=22) Icons in the list

These decorations apply to **files**. Folder rows always use the **folder** + **chevron** pattern above.

| Icon | What it means |
|------|----------------|
| ![Current master](lucide://Crown?color=%23fbbf24&size=22) | **Current master** — YAML `type: master` and `status: current`. |
| ![Superseded master](lucide://Crown?color=%2371717a&size=22) | **Other master** — e.g. **superseded**; same crown shape, muted color. |
| ![Note](lucide://FileText?color=%23d4d4d8&size=22) | **Normal note** — included in vault search unless you opt out. |
| ![Hidden from search](lucide://EyeOff?color=%23d4d4d8&size=22) | **Excluded from search** — YAML `searchable: false` (non-masters). |

*Tip:* Shape matters as much as color — **crown** vs **page** vs **eye-off** are easy to scan at a glance.

---

## ![Edit](lucide://FileText?color=%23fb923c&size=22) Opening and editing a note

Select a file to load it on the right.

- **![Source](lucide://Code2?color=%23c4b5fd&size=18) Source** — edit your note text. If the file has an info block at the top, it appears in a **read-only** strip above the editor; use **Edit details…** to change it. Files without that block show everything in the editor until you add details.
- **Web copy to Markdown** — when you paste rich text copied from a webpage into a note body, DeskMemory converts clipboard HTML into Markdown automatically (headings, lists, links, and emphasis).
- **![Preview](lucide://Eye?color=%23c4b5fd&size=18) Preview** — rendered Markdown (no info block shown). Use **Save PDF as…** to build a **real PDF** from your note’s Markdown: **selectable text**, **page margins**, and **natural page breaks** between blocks (not a screenshot). Output is a light, print-friendly layout even when the app uses dark theme. The app asks where to save **`.pdf`** on disk, then shows **File downloaded successfully.** when it finishes. Cancel the save dialog to abort quietly. If export fails, you may see a red message at the bottom; it **auto-clears after a while** and you can tap **Dismiss** (×) to close it sooner.

Unsaved changes are tracked; switching to another file may ask to discard changes.

- **![Save](lucide://Save?color=%23c4b5fd&size=18) Save** or **Ctrl+S** — writes the file to disk.
- **Quick capture hotkey** — press **Ctrl+Shift+Space** (Mac: **⌘+Shift+Space**) to open **Quick capture**: title + body saved as a new vault note at the library root (with `source: quick-capture` in front matter). With **Advanced settings** on, the shortcut is also listed under **Settings → File Settings → Capture & search**. Rich paste from the web is converted to Markdown in the capture body.

---

## ![Save](lucide://Save?color=%23fb923c&size=22) Saving

- **Save changes** — Writes the **currently open** file as-is (full Markdown, including any info block at the top). Shown in the editor header when there are unsaved edits.
- **New note via Save dialog** — The **Save** dialog (title, type, category, tags, path) appears whenever you create a **new** organized file from **New file** or **Add file…**, **drag a `.pdf`**, [save a chat thread to the vault](#saving-a-chat-thread-to-the-vault) after the gateway draft, or **paste-import** that creates new files. If you leave **date** empty, **today’s date** is stored. **Masters** get versioned; the previous current master for the same category can be marked **superseded** automatically.
- **Suggested tags** — After you pick a **category**, you’ll see tap-friendly chips with common tags for that topic (you can still type your own). Tags and categories are driven by your vault **taxonomy** in **Settings → Chat Settings**; saving from chat with **AI prefill** on can also add new suggestions to the taxonomy over time.

## ![Clipboard](lucide://ClipboardList?color=%23fb923c&size=22) Note details (pasted or old files)

Copied-in Markdown often has **no info block** at the top. When you open such a file, the header shows a short status, for example **No note details yet** or **Note details incomplete** — not technical jargon.

Click **Edit details…** in the editor header to set **title**, **type** (including **Master** for a flagship doc such as a brand guide), **category**, **date**, and **tags**. If **date** is left empty, **today’s date** is filled when you save. DeskMemory adds or updates the small block at the top of the file, **renames the file from the title**, and when a category is chosen, places it into that category folder (creating it if needed). Your writing below is left as-is. You can open **Edit details…** anytime, even when the block is already there, to change type or add tags.

Making a file a **master** here follows the same versioning rules as the **Save** dialog for “current” vs “older” masters in that category.

---

## ![Search](lucide://Eye?color=%23fb923c&size=22) Include in vault search

For files that already have YAML front matter (`---` … `---`), the editor header can show **Include in vault search**.

- Turn it off to set **`searchable: false`** (you will see ![eye off](lucide://EyeOff?color=%23d4d4d8&size=16) in the list).
- **Current master** documents always stay searchable; the checkbox is disabled for them.
- Save any edits before changing this setting.

---

## ![Search tune](lucide://SlidersHorizontal?color=%23fb923c&size=22) Tuning meaning-based search

Your library can be searched in two complementary ways:

- **File name filter** — Words in the sidebar search box match **Markdown file names** (all words must appear). This is fast and literal.
- **Meaning-based matches** — When the search box starts with **`~`**, the app ranks notes by **topic and wording similarity** to the rest of your query (after the tilde). If you **do not** use `~` but you typed several name tokens, the app can **blend** name matches with a limited set of meaning-based suggestions (“hybrid” mode).

**Freshness (recency):** On top of similarity, the vault index applies a **small** ranking nudge (at most **+3%** score) for notes that were **recently updated in the index** (`updated_at` in the local SQLite index), so stale-but-similar files do not always win ties. **Current masters** (`type: master` + `status: current`) are **excluded** from that nudge. The YAML **`date`** field is for your own metadata; if you leave it blank when using the **Save** dialog or **Edit details…**, the app fills **today’s date**—but **search freshness uses index update time**, not YAML `date`, so saving the body still moves the note forward even if you forget to change the calendar field. See [`vault-search-recency.md`](vault-search-recency.md) / **ADR 011**.

All tuning below affects **how strict** those meaning-based matches are and **how many** extra hits appear—not *how* text is stored on disk.

### Advanced settings (master switch)

Most everyday use only needs **semantic strictness** (below). Power-user controls are grouped behind a single switch so Settings stays simple.

1. Open **![Settings](lucide://Settings?color=%23c4b5fd&size=18) Settings** (the dialog opens on **Account**).
2. Scroll to the bottom of **Account** and check **Advanced settings**.

When **Advanced settings** is **off** (default), these panels are **hidden**:

- **File Settings** — entire section (library path, bulk import, capture & search tuning).
- **Embeddings index** — Recheck, Index missing, Refresh search text (**Settings → File Settings → Capture & search**).
- **Advanced search tuning** — match-label and semantic-score checkboxes, **Threshold bias**, and **Max semantic expansion** sliders (same section).
- **Vault save automation** — AI prefill and silent save for chat → vault exports (**Settings → Chat Settings**).
- **Max vault files in chat context** — Cap on ranked files sent per message (**Settings → Chat Settings → Chat preferences**; max **10**, default **8**). Memory pack **Start in chat** attaches coach + references first, then filled outputs, up to this cap.
- **Indexing and metadata badges in Files** — Optional header chips (Idle/Indexed, Metadata set) and read-only metadata block in Source view (**Settings → File Settings → File viewer**). Off by default; requires **Advanced settings** on Account.

When **Advanced settings** is **on**, those sections appear for the current app session. The switch **starts unchecked** and resets when you **sign in** or **sign out**—it is **not** saved to disk. Turning advanced **off** only hides the controls; your other search and automation prefs still persist locally.

### Where to adjust settings

Open **![Settings](lucide://Settings?color=%23c4b5fd&size=18) Settings**, then the **Capture & search** section in **Settings → File Settings**. Enable **Advanced settings** at the bottom of **Account** when you need indexing tools or search debug sliders. The same **semantic strictness** choices also appear as small buttons next to **Top relevant matches** in the sidebar when you have ranked results, so you can experiment without leaving the search context.

### Semantic strictness (Conservative · Balanced · Broad)

This controls the **default cutoff** for meaning-based similarity: how close a note must be to your query to stay in the list.

- **Conservative** — Keeps **fewer**, **stronger** matches. Use this when results feel noisy or off-topic.
- **Balanced** — A middle setting for everyday use.
- **Broad** — Allows **more** notes, including weaker matches. Use this when you suspect the right note is phrased very differently or you want to cast a wide net, then narrow by eye.

### When strictness and sliders make a visible difference

The app does **not** use a fixed rule like “you need 100 documents.” Meaning-based search always runs against your vault; what changes with size is how **crowded** the “maybe” zone is.

- With **few notes** (for example **~25** Markdown files), **most indexed files may already sit among the top candidates** for many queries. **Conservative** vs **Broad** often shows up as **which borderline rows** stay or drop off—not always a dramatic reshuffle of the whole list.
- Differences get **easier to see** when **many notes could plausibly match** (lots of topics, similar titles, or vague queries), so **several scores cluster near the cutoff**. That often becomes more common as you move from **tens** of notes toward **on the order of 100+**, but it is **not a hard threshold**: a small set of **very overlapping** notes can behave like a large library, and a huge set of **very distinct** notes might still look stable on a sharp query.
- **Short queries** are handled a bit more cautiously, which also limits how much the list moves when you flip strictness.

**Tip for a small vault:** Enable **Advanced settings**, turn on **Show semantic scores**, run an **ambiguous `~` query**, and switch **Conservative** ↔ **Broad** while watching **scores and which weak tail items** appear or vanish.

### What the result badges mean

When **Top relevant matches** lists files, enable **Advanced settings**, then turn on **Show match labels in search results** under **Settings → File Settings → Capture & search → Advanced search tuning** to see short labels on each row:

- **Name match** — Query words appear in the file or folder name.
- **In note** + **Often mentioned** — Words appear often in the note body (keyword frequency).
- **Similar topic** + **High** / **Medium** / **Low** — Meaning-based match strength (embeddings).

Hover a label for a short tooltip. **Name match** rows show only one label (no redundant “exact” chip).

### Advanced search tuning (optional)

With **Advanced settings** enabled, the **Advanced search tuning** block is for people who want to **see numbers** or **nudge** behavior without changing code.

- **Show match labels in search results** — When enabled, the match-type and strength labels above appear beside each ranked row. Off by default.
- **Show semantic scores in results** — When enabled, extra numbers appear beside meaning-based rows. Treat them as a **diagnostic**; they are **not** a human-readable “explanation” of why a note was chosen. Off by default.
- **Threshold bias** (−0.15 … +0.15) — A small slider that **raises or lowers** the similarity cutoff **on top of** strictness. **Raise** the bias for **fewer, stricter** meaning matches; **lower** it for **more** marginal matches. Reset toward the middle if things feel unpredictable.
- **Max semantic expansion** (4 … 30) — Caps **how many** embedding hits are considered when the app **extends** a normal file-name search with extra semantic suggestions. **Lower** values keep the blend closer to “names only”; **higher** values allow more semantic neighbors (still ranked).

**Practical workflow:** Start from **Balanced**. If results are too fuzzy, try **Conservative** or a slightly **higher** threshold bias. If you get almost nothing, try **Broad** or a slightly **lower** bias, and check that notes are **indexed** (enable **Advanced settings**, then see **Embeddings index** in the same Settings panel: **Recheck** missing count, **Index missing** for vectors, **Refresh search text** if hybrid name search needs body text). Rephrase longer queries before chasing slider extremes.

---

## ![Folder](lucide://FolderInput?color=%23fb923c&size=22) Bringing files in from disk

You have **two** complementary paths—pick the one that matches how much metadata you want to set **right now**.

### Bulk Markdown (migration / many files at once)

1. Enable **Advanced settings** on **Account**, then open **![Settings](lucide://Settings?color=%23c4b5fd&size=18) Settings → File Settings**.
2. Under **Bulk Markdown import**, click **Import Markdown from folder…**.
3. Choose a folder on your computer. The app looks at the **top level only**—each **`.md` file** sitting directly in that folder (not inside subfolders) becomes a candidate.
4. Confirm when asked. Matching files are copied into your **vault root**, then the list refreshes. There is **no** per-file Save dialog in this path: files land with their **existing** bodies and whatever front matter they already had; you can tidy categories and YAML later with **Edit details…** or a normal **Save** workflow on each note if you want richer metadata.

### Single file with full metadata (`.md` or `.pdf`)

- In the Files workspace sidebar, click **Add file…** (![Upload](lucide://Upload?color=%23c4b5fd&size=18)). The OS picker allows **one** file per use.
- **Markdown** — Contents are loaded into the **Save** dialog (classified path) so you set category, tags, and placement before anything is written.
- **PDF** — The app **extracts text** locally (maximum **20 pages**) and opens the **Save** dialog with a suggested title from the PDF name. You still choose category/tags like any new note. **Scanned PDFs**, PDFs **without selectable text**, or **longer documents** may fail with a clear message rather than creating an unusable note.

### Drag-and-drop & paste

- Drag **`.md`** onto the list (or a folder row) to copy into the vault. Drag **`.pdf`** onto the same areas to queue the **Save** dialog after extraction (one PDF after another if you drop several).
- **Paste-import** copies **Markdown** files from Explorer/Finder (see **The file list** above)—fast when you already copied files from the desktop.

*(There isn’t an “always-watch this folder” import in Settings in this guide’s scope—imports are deliberate actions you trigger.)*

## ![Organize](lucide://Folder?color=%23fb923c&size=22) Import, move, and organize

- Drag **`.md`** files from Explorer or Finder onto the list (or onto a folder row) to **copy** Markdown into your vault at that location.
- Drag **`.pdf`** files the same way to start the **Save** dialog after **text extraction**.
- Drag **rows** in the list to **move** files or folders; drop on a folder or the empty root area.
- **Right-click** a row for rename, delete, or **New subfolder** when the menu applies.

---

## ![Q&A](lucide://MessageCircleQuestion?color=%23fb923c&size=22) Common questions (Q&A)

### Do I need LLM API keys?

No. Chat send, **Compress…**, **Save to vault…**, and AI taxonomy prefill use your **DeskMemory account** (Settings → Account). Provider API keys are not required for shipped AI features on desktop.

### Why doesn’t meaning-based search find my chat threads?

**Chat drafts** live in a **local app database**, not as `.md` files in your vault. Meaning-based search only runs over **vault Markdown** that you have indexed. To make a conversation searchable as vault memory, use **Save to vault…** from chat (see [Saving a chat thread to the vault](#saving-a-chat-thread-to-the-vault)).

### Do attached vault files appear inside my chat message text?

**No.** What you type is saved as your **user** message. Selected vault files are read from disk and sent as **Vault context** on the **system** side when you press **Send** (see [Chat with AI (gateway)](#chat-with-ai-gateway)).

### What happens to my open chats when I restart the app?

**Open** chats and messages are **restored** from the local SQLite store (gateway chat sessions). Closing a chat from the **Open chats** rail or successfully **saving to the vault** ends that session (save also records the export and removes it from the rail).

### Why is **Compress…** disabled, and what is the bar above it?

**Compress** only runs when there is a **first user** message, at least one **follow-up** turn, and roughly **12,000 characters** in the **tail** (everything after that first user message). The thin bar fills toward that minimum. After you compress, your first user block stays verbatim; later turns are replaced by **one** assistant summary (see [Compressing a long chat thread](#compressing-a-long-chat-thread)).

### What is the amber “Long thread” banner?

When the **sum of all message text** in the current chat reaches about **150,000 characters**, a dismissible **amber banner** appears below the chat header. It explains that the full thread is resent on every message, so replies can get **slower** and less focused, and it suggests **Compress…** (with a shortcut when compress is already allowed) or **Save to vault…**. It is a **heads-up**, not an error—sending is not blocked. **Dismiss** hides it until the total falls **below** 150k (then it can appear again if you grow past the limit) or you **switch chats** (each switch clears the dismiss flag).

### What is the “Please compress this chat” dialog?

At about **200,000 characters** in the same tab, a **dialog** opens with the same guidance in more detail, plus **Compress…** (when available), **New chat**, and **Not now**. **Not now** hides the dialog until the thread drops below 200k, you switch chats, or you **send another message** while still over 200k (then it can appear again). Sending is still allowed.

### What does **Save to vault…** do to my chat?

After a **successful** save through the normal flow, that chat **closes** (removed from **Open chats**) and you get a **toast** with the new file path. The new note is an ordinary vault file. If **Silent save** is on (after the reviewed-save gate), the dialog may be skipped but the file is still written and you still get feedback—see [Vault save automation](#vault-save-automation).

### Why can’t I turn on **Silent save** yet?

**Silent save** stays off until you have completed enough **reviewed** saves from the chat → vault **Save** dialog for that vault (the counter on **Vault save automation**). That way you practice checking category and tags before the app skips the form.

### Why does the sidebar only show Markdown?

The library is designed as a **Markdown vault**. Other file types in the same folder on disk are **not** listed, which keeps search, import, and delete rules predictable (see [First launch and your folder](#first-launch-and-your-folder)).

### What is the difference between **Save** (in the editor) and the **Save** dialog for new notes?

The **Save** button next to Source/Preview writes the **currently open** file **in place**. The **Save** dialog (same form **New file**, **Add file…**, PDF drop, paste-new, and chat export use) creates or replaces a **new** organized path with title, type, category, tags, and versioning rules for **masters**. Chat **Save to vault…** reuses that dialog after the gateway draft (see [Saving](#saving)).

### Why did my PDF import fail?

DeskMemory extracts **text that already exists inside the PDF** (selectable text). Imports are limited to **20 pages** so one vault note does not overwhelm search or AI context—split or export a shorter PDF and try again. **Scanned pages** without OCR, protected files, or odd encodings may also fail—try a PDF you can copy-paste from in another viewer, or paste the text into a new Markdown note manually.

### When should I use **Settings → Import Markdown from folder…** versus **Add file…**?

**Import Markdown from folder…** is for bringing in **many** top-level Markdown files quickly (migration). **Add file…** is for **one** `.md` or `.pdf` when you want the full Save form **every time** (category, tags, placement).

### Does drag-and-drop use the bulk Settings import?

**No.** Drag-and-drop and **Add file…** always go through the **per-file or per-batch** behaviours described in [Bringing files in from disk](#bringing-files-in-from-disk)—Markdown copies **as files**; PDFs open **Save** after extraction. Only the **Library** bulk action skips the Save form for each Markdown file.

### Why do semantic results look empty for a `~` query?

Notes need to be **indexed** for meaning-based search. Enable **Advanced settings**, open **Settings → File Settings**, and use **embeddings** controls (**Recheck**, **Index missing**) to index or recheck missing files. You can also adjust **semantic strictness** from the sidebar next to **Top relevant matches**, or try a slightly **broader** strictness or lower **threshold bias** with advanced on ([Tuning meaning-based search](#tuning-meaning-based-search)).

### What are the amber or sky banners at the top of the app?

When signed in, DeskMemory shows **billing and quota alerts** on every screen: **Payment failed** (amber), **Subscription cancelled** (sky, with access-until date), and a compact **Monthly quota reached** strip (red). CTAs open the **web dashboard** in your browser—see [Billing and quota alerts](#billing-and-quota-alerts).

### How does **Web search** in chat work?

In **Chat settings**, choose **Web: Auto**, **Always**, or **Off**. **Auto** lets the gateway search when fresh web facts help; **Always** searches every send; **Off** disables search. Successful searches add a **Web sources** block to the assistant reply. Search uses your account quota when it runs.

### What happens when I close a chat from the Open chats rail?

If the chat has messages, DeskMemory asks whether to **Save to vault first…**, **Delete chat without saving**, or **Cancel**. Empty new chats close without the dialog.

### Can I move my library to another folder in Settings?

**No.** With **Advanced settings** on, **Settings → File Settings** shows the path for reference only; the library location is also shown in the top bar. Chat sessions and automation prefs are **per vault path**; keeping one fixed library location avoids splitting data across folders before cloud backup is available.

---

## ![Tips](lucide://Lightbulb?color=%23fbbf24&size=22) Tips

- **![Theme](lucide://Sun?color=%23fbbf24&size=18) ![Night](lucide://Moon?color=%23ea580c&size=18) Theme** — Sun / moon control in the top bar switches light or dark UI.
- **![Help](lucide://CircleHelp?color=%23fb923c&size=18) Help** — Opens this guide; links in the table of contents scroll inside the window; **http** and **https** links open in your browser.
- **Billing banners** — Persistent alerts for payment, cancellation, or quota limits stay visible on Files and Chat until resolved on the web or your period resets ([Billing and quota alerts](#billing-and-quota-alerts)).
- **Toasts** — Short green **success** messages at the bottom clear on their own after a few seconds. Red **errors** stay a bit longer; use **Dismiss** (×) to close immediately when shown.
- **Quitting** — Closing the app window may show a **Yes / No** confirmation. Choose **Yes** to exit. (Desktop / Tauri build only.)

---

For **developers** and deeper product behavior, see the Markdown files under the repository **`Docs/features/`** (source tree only — not bundled as separate files inside the installed app). For chat sessions, **Save to vault**, **Compress**, billing alerts, and SQLite persistence, see **`Docs/features/gateway-chat.md`** and **`Docs/features/chat-history.md`** in the source tree.
