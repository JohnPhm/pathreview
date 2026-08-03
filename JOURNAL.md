## Week 7 — Issue selection

**Issue link:** (https://github.com/ascherj/pathreview/issues/149)

**Issue title:** Structural chunker silently drops documents that contain no headings

**Tier:** [X] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
StructuralChunker is not supposed to return an empty list for any document without a heading. It is essentially excluding the entire document from the RAG index instead of trying another strategy. A successful fix would have the chunker either return an error message, alerting the user of what is happening, or it should try another method for chunking. 

**Branch name:** fix/149-structural-chunker-silently-drops-documents

**Setup confirmation:** [X] App runs locally at localhost:5173

**Cohort ledger:** [X] Issue added to cohort ledger

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** https://github.com/ascherj/pathreview/commit/c365e22c1a92590de989216cae2b763a77fe7b4a

**Reproduction summary:**
[1–2 sentences: How did you reproduce the issue? What did you observe?] 
To reproduce the issue, I used one of the included unit tests within the pathreview project. Under the tests subfolder (pathreview/tests/unit/test_structural_chunker.py) and with the virtual environment activated, I ran the command "python3 -m pytest tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings -v", which specifically uses the test_document_with_no_headings function in the structural_chunker python file. Running the test function, it returns an AssertionError (assert 0>= 1). 

**PLAN.md link:** https://github.com/JohnPhm/pathreview/blob/fix/149-structural-chunker-silently-drops-documents/PLAN.md

**Walkthrough video (recommended):** [link to your Loom video, ≤2 min — recommended, not graded]

**Blockers or open questions:**
Going into week 9, I am still confused on how to write and modify unit tests to confirm that my fixes to the structural chunker works correctly. 
