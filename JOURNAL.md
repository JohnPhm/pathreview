## Week 7 — Issue selection

**Issue link:** (https://github.com/ascherj/pathreview/issues/149)

**Issue title:** Structural chunker silently drops documents that contain no headings

**Tier:** [X] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
StructuralChunker is not supposed to return an empty list for any document without a heading. It is essentially excluding the entire document from the RAG index instead of trying another strategy. A successful fix would have the chunker either return an error message, alerting the user of what is happening, or it should try another method for chunking. 

**Branch name:** fix/149-structural-chunker-silently-drops-documents

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger
