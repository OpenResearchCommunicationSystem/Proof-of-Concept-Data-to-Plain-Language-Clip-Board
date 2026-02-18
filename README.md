# [-> For Data to Plain Language Clipboard Demo Click Here <-](https://openresearchcommunicationsystem.github.io/Proof-of-Concept-Data-to-Plain-Language-Clip-Board/)

## What this Proof of Concept Solves

#### Broad Problem

- Human Error Cascading
- Utility - Misery Scaling Paradox
- End Use Assumptions Error
- User's Leaving Solution
- Shopping with no Shopping Cart
#### Specific Problems

- The Retyping Tax
- The Screenshot Problem
- HTML Footnote Problem
- HTML Table Cutting
- Split-Screening and Context Switching 
- Third Party Converter Slow Down

## What This Proof of Concept Demonstrates

| What it shows                                                      | Why it matters                                                                  |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| Data entered once, exported in five formats                        | Users stop reformatting the same information for different audiences            |
| Runs entirely in the browser                                       | Near-zero cost to the provider, instant performance, no data leaves the machine |
| Real footnotes (rich text file)                                    | Solves a problem that copy-paste from HTML cannot                               |
| Changes between Data (relationship) and Plain Language (Predicate) | Right presentation for each context, no manual conversion                       |
| Deterministic code, no generative AI                               | Cheaper, faster, more reliable, no hallucination risk                           |
| One clipboard, multiple entries                                    | Users stay in the tool instead of exporting one item at a time                  |
| Graph Friendly CSV export (Node/Edge)                              | Data is graph-ready without manual restructuring                                |
| World Wide Web Standard Provence (PROV-O JSON-LD)                  | Future-forward provenance tracking using a recognized standard                  |
| Demo is a Single Web Page File with no dependances                 | Can be hosted anywhere, works offline, no build tools required                  |

The concept is simple. The implementation is straightforward. The value compounds across every user, every workflow, every day.

The question is not whether this is hard to build. It is not. The question is how much productivity and accuracy is being lost every day because no one has built it yet.

## How to Use This Proof of Concept

The proof of concept is a single HTML file (`standalone/index.html`). It requires no installation, no build tools, no server, and no internet connection after the initial load. Open it in any modern web browser.

### The Interface: Three Sections

**Section 1 — Add New Statement**

Three buttons across the top:

- **Fill and Clip** — Generates a random structured statement and adds it directly to the clipboard. Both Section 2 and Section 3 collapse to default. This demonstrates the fastest possible workflow: one click, data captured.
- **Fill and Display** — Generates a random statement and expands Section 2 to show the preview. This lets you inspect the data before adding it to the clipboard.
- **Manually Enter** — Expands the form fields and Section 2 so you can type your own subject, predicate, object, and source.

**Section 2 — Existing Display (Preview)**

Collapsed by default. Expands when you click Fill and Display or Manually Enter.

Two views, toggled with a button:

- **Table View** — Shows the current statement as a structured table with columns: Subject, Relationship, Object. The Relationship column displays the short code (e.g., `CTO`, `INVESTOR`). The source is shown below the table.
- **Graph View** — Shows the same statement as a visual graph: two nodes (Subject and Object) connected by an edge labeled with the relationship code. This demonstrates how the same structured data supports graph visualization.

An "Add to Clipboard" button sends the previewed statement to the output.

**Section 3 — Output Preview**

Shows all accumulated statements in the clipboard. This is where the plain-language output appears — full sentences with the complete predicate text, not the short codes.

Three citation modes, toggled at the top:

- **Footnote Cite** — Each statement gets a numbered footnote marker, with sources listed as footnotes at the bottom.
- **In-Text Cite** — Sources appear in parentheses at the end of each statement.
- **No Cite** — Statements appear without any source attribution.

### Demonstrating Different Data Types

**Individual Table Entry:**
Click "Fill and Display" or "Manually Enter" to see a single statement displayed as a structured table. This simulates what a user sees when they find one piece of information in a PAI tool — a row of structured data. The proof of concept shows how that row can be instantly converted to a sentence.

**Individual Graph Entry:**
Toggle to Graph view in Section 2. The same statement is now a subject-object pair connected by a labeled edge. This demonstrates that the underlying data supports both tabular and graph representations without any additional processing.

**Multiple Accumulated Statements:**
Click "Fill and Clip" or add entries via "Fill and Display" several times. Section 3 accumulates all statements into a single clipboard. This demonstrates the one-clipboard-multiple-entries concept — the user does not have to export and re-enter the tool for each item.

---

## Export Formats Explained

### Plain Text Copy

The copy button places the entire clipboard contents on the system clipboard as formatted text with bullet points and citations (based on the selected citation mode). The user can paste directly into any application.

This is the simplest export and covers the most common need: getting sourced statements into a document quickly.

### Rich Text Format — Why Not Just Text?

RTF (Rich Text Format) is the answer to the footnote problem described earlier.

Plain text cannot carry footnotes. HTML footnotes do not survive copy-paste into word processors. But RTF is the native format of Microsoft Word and is supported by virtually every word processor. RTF has a specification for real footnotes — the kind that appear at the bottom of the page with superscript markers in the body text.

When you export as RTF from this proof of concept, you get a `.doc` file that opens in Microsoft Word with properly formatted footnotes. Not fake footnotes. Not endnotes. Not parenthetical references. Actual page-bottom footnotes with superscript markers.

This is something that no amount of copy-paste from a web browser can achieve. It requires generating the RTF format directly, which is exactly what this tool does.

### CSV Single Table — The Flat Export

The single-table CSV exports all statements in a flat structure:

```
Subject,Relationship,Object,Source
Amara Okafor,FORMER_CEO,Helios Dynamics,"Corporate Filing, 2024"
```

This is the format most people expect when they think "spreadsheet." Every statement is one row. Every field is one column. It opens directly in Excel, Google Sheets, or any data tool.

Use this when the downstream consumer needs to filter, sort, or pivot the data in a spreadsheet.

### CSV Node/Edge — The Graph Export

The node/edge CSV is different. It splits the data into two sections:

**Nodes:**
```
NodeID,Label
1,Amara Okafor
2,Helios Dynamics
```

**Edges:**
```
SourceNodeID,TargetNodeID,Relationship
1,2,FORMER_CEO
```

This format is designed for graph databases and network visualization tools (Gephi, Neo4j, Palantir, i2 Analyst's Notebook, and others). Each unique entity gets one node. Each relationship becomes an edge between two nodes.

Why does this matter? Because if the same person appears in five different statements, a flat table has that name in five rows. A node/edge table has that person as one node with five edges. This is the structure that link analysis, social network analysis, and knowledge graph tools expect.

Providing this export means the user does not have to manually restructure a flat table into a graph format — a tedious and error-prone process that analysts do regularly.

### PROV-O JSON-LD — The Provenance Standard

PROV-O is a W3C (World Wide Web Consortium) standard for provenance — tracking where information came from. JSON-LD is a format for linked data that is both human-readable and machine-parsable.

The PROV-O JSON-LD export from this proof of concept represents each statement as a provenance record:

- Each subject-predicate-object assertion is a `prov:Entity`
- Each source attribution uses `prov:wasDerivedFrom`
- The output follows the W3C PROV ontology specification

**Why this matters now:**

Most users will never directly consume a PROV-O file. But this export sets up several future-forward capabilities:

1. **Interoperability.** PROV-O is a recognized standard. Systems that speak PROV-O can exchange provenance information without custom adapters or format negotiations.

2. **Audit trails.** In regulated environments, proving where a piece of information came from — and tracking that provenance through every system it passes through — is not optional. PROV-O provides a machine-readable chain of attribution.

3. **Knowledge graphs.** As organizations build knowledge graphs from PAI data, having provenance baked into the data model from the start means you do not have to retrofit attribution later.

4. **Linked data ecosystems.** JSON-LD is the format that powers structured data on the web (it is what Google uses for rich search results, among other things). Exporting in JSON-LD means the data is ready to participate in the broader linked data ecosystem.

5. **Reproducibility.** A PROV-O record does not just say "here is a fact." It says "here is a fact, here is where it came from, and here is when it was asserted." This supports reproducibility and verification at scale.

By including this export in a proof of concept, we demonstrate that structured data with provenance can be a first-class output — not an afterthought bolted on later.


## The Problem Nobody Talks About

Public Available Information (PAI) and Commercial Aggregated Information (CAI) tools are powerful. They surface structured data — names, roles, organizations, connections, timelines — from vast amounts of information. But there is a gap between what these tools *produce* and what the people downstream actually *need*.

That gap is filled, every single day, by humans retyping information they are already looking at.

## What Happens When Humans Retype Data

### The Retyping Tax

A user finds what they need in a PAI tool. It's sitting right there on screen — a name, a role, an organization, a source. Now they need to put it into a report, a briefing, an email, a slide deck.

So they start typing. By hand. From one window into another.

This is not a rare event. A single analyst may run hundreds or thousands of workflows per day. Each one produces data that has to go somewhere. Even if the retyping only takes a few seconds each time, multiply that across an entire team, across every workflow, across every day. That is not a minor inefficiency. It is an operational burden that scales with every user and every use case.

Every time a human retypes something, there is a chance they get it wrong. A misspelled name. A transposed number. A role attributed to the wrong person. These are not dramatic failures — they are quiet ones. They slip through review. They propagate into downstream products. They erode trust in the output.

### The Screenshot Problem

When retyping feels too slow or too risky, users do something worse: they take a screenshot.

A screenshot converts usable data and text into a picture. That picture cannot be searched. It cannot be copied. It cannot be parsed, validated, or automatically formatted. If anyone downstream needs to actually *use* that information — in a database, a report, a spreadsheet — they have to retype it from the image. The error chain starts again.

Screenshots are a symptom. They tell you that the tool did not give the user a good way to get information out.

Users should never have to screenshot data or text. It is unprofessional, it destroys machine-readability, and it creates exactly the kind of error cascade that structured tools are supposed to prevent.

### Split-Screening and Context Switching

When users cannot get data out of a tool in a useful format, they split their screen. One window has the PAI tool. Another has the report. Another has a spreadsheet. Maybe another has an email.

Every time the user switches windows, they lose focus. Every switch introduces a chance to copy the wrong value, paste into the wrong cell, or simply lose track of where they were. The tool that was supposed to make them faster is now the reason they are slow.

If the tool had given them a clipboard — a simple way to collect and export structured information — they would never have to leave.

### The Footnote Problem

Try this: find a piece of information on a web page that includes a source citation. Copy it. Paste it into Microsoft Word.

The footnote is gone.

HTML footnotes do not survive the clipboard. They are rendered by the browser, but when you copy text from a web page, the footnote markers and the footnote content are stripped. The user gets the text without the attribution.

For anyone working in a field where source attribution matters — intelligence analysis, legal research, journalism, due diligence — this is not a minor inconvenience. It means that every single citation has to be manually reconstructed after pasting. For every piece of information. Every time.

There is zero chance of a copy from HTML preserving footnotes in a word processor. Zero.

### Cutting Tables Into Documents

Users often need one or two rows from a table. But when they copy from a table, they get the whole table — headers, extra columns, formatting artifacts. Then they have to paste it into a document and manually delete everything they do not need. They reshape the table into text. They reformat. They clean up.

This is work the tool should have done. If the tool offered the data as a sentence — "Amara Okafor is the former CEO of Helios Dynamics (Source: Corporate Filing, 2024)" — the user would copy one line and move on.

### No one Can Predict What the End User Wants (including the End User)

Here is a reality that tools rarely account for: the person using the PAI tool is usually not the final consumer of the information.

An analyst runs the query. But the briefing goes to a manager. The report goes to an executive. The data goes into a product that someone else reads. Each of those downstream consumers has different needs — some want sentences, some want spreadsheets, some want graphs, some want footnotes, some want no citations at all.

If the tool only exports in one format, the user has to manually reformat for every audience. If the tool offers a clipboard with multiple export options — plain text, RTF with footnotes, CSV for spreadsheets, graph-ready node/edge tables — the user picks the right format and moves on.

### The Misery Scales With Utility

This is the cruel irony: the better the PAI tool is, the worse this problem gets.

A tool that surfaces valuable information gets used more often. More use means more workflows. More workflows means more retyping, more screenshots, more split-screening, more manual reformatting. The more valuable the tool, the more time users waste fighting its export limitations.

Every provider should be asking: if a user finds something valuable in our tool, how many steps does it take to get that value into the format they actually need?

### If You Let Them Copy One Thing, Let Them Copy Many

Most tools that offer any clipboard functionality limit it to a single item. Copy one result. Paste it. Go back. Copy the next one.

If you are going to build a clipboard feature, build one that accumulates. Let the user collect multiple statements, review them, and export them all at once. One clipboard, multiple exports. That is what turns a convenience feature into a workflow tool.

---

## A Quick Technical Primer: Front End, Middle, and Back End

To understand why this solution is cheap and scalable, it helps to understand three layers of a web application. This is simplified, but it covers what matters for this conversation.

### Front End

The front end is what runs in the user's web browser. It is the interface — buttons, text fields, tables, graphs. When you open a web page and interact with it, your computer is doing the work of rendering and running that page.

Front-end code runs on the user's machine, using the user's processor and memory. The provider's servers are not involved once the page loads.

### Back End

The back end is what runs on the provider's servers. It handles things like databases, user accounts, access control, and queries against large datasets. When a PAI tool searches millions of records, that search runs on the back end.

Back-end operations cost the provider money. Every query uses server time, network bandwidth, and computing resources. The more users, the more it costs.

### Middle Layer (APIs)

The middle layer is the communication channel between front and back end. When you click a button and the page shows you new data, your browser sent a request to the back end and received a response. That round trip is the middle layer.

### Why This Matters for Our base Solution

Converting structured data into a plain-language sentence — putting a subject, a predicate, and an object into the pattern "[Subject]  [predicate] [Object]" — is a front-end operation. The user's browser does it. The provider's servers are not involved.

This means:

- **Near-zero cost to the provider.** No additional server calls, no database queries, no API traffic. The data is already on screen. The browser just rearranges it into a sentence.
- **Scales to any number of users.** Since the work happens on each user's own machine, adding more users does not add server load.
- **No latency.** The sentence appears instantly. No waiting for a server response.

The only scenario where back-end involvement might be needed is if the system has a very large number of relationship types and the mapping between relationship codes and full predicate text needs to be stored or managed centrally. Even then, this is a small, infrequently-changing lookup table — trivial compared to the core query workload these tools already handle.

**A note to development teams:** This description covers the straightforward case. Real-world implementations depend on how the existing system is architected. Some systems may require more effort to surface structured data on the front end. This proof of concept demonstrates the concept and the value — the implementation path will vary by platform. The point is that the *concept* is simple and the *cost* is low relative to the value it delivers.

---

## Why Code Beats Generative AI for This

The first thin your learn in programing is how to make a sentence. 

```
output = "Hello World!"
run
...Hello World!
```

The second thing you learn is how to put data into a sentence

```
Username = Bob
output = "Hello " + Username + "!"
run
...Hello Bob!
```

That is it. 

Generative AI is powerful. It is also expensive, unpredictable, and occasionally wrong. It hallucinates. It paraphrases when you wanted a direct quote. It adds words you did not ask for. It requires infrastructure, API keys, token costs, and latency.

For the task of assembling a sentence from known components, generative AI is the wrong tool. You already have the subject, the predicate, the object, and the source. You do not need a large language model to arrange four values into a sentence template. You need a line of code.

**Relationship codes vs. full predicate text:**

In this proof of concept, we maintain a simple mapping between short codes and full predicate phrases:

| Code | Full Predicate |
|------|----------------|
| `FORMER_CEO` | is the former CEO of |
| `BOARDMEMBER` | is on the board of |
| `FOUNDER` | founded |
| `LEAD_COUNSEL` | is the lead counsel for |
| `CTO` | is the chief technology officer of |
| `INVESTOR` | is a major investor in |
| `CHAIRPERSON` | serves as chair of |
| `MANAGING_DIRECTOR` | is the managing director of |
| `ADVISOR` | advises |
| `NEW_LEADER` | was recently appointed to lead |

Tables and graphs show the short code — it is compact, scannable, and consistent. Plain-language output uses the full predicate — it reads naturally in a sentence.

Same data. Right presentation for each context. No AI required.

This mapping is deterministic. It produces the same output every time. It cannot hallucinate. It cannot get creative. It does exactly what you told it to do, and it does it for free on the user's browser.

---

By including this export in a proof of concept, we demonstrate that structured data with provenance can be a first-class output — not an afterthought bolted on later.



