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

## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
So far, I have been able to confirm that the issue exists and am able to reproduce the issue.

**Next steps:**
For the rest of the week, I will be working on the implementation of the issue fix. 

**Blockers:**
Going from planning to implementation is taking longer than I expected.  

---

### Check-in 2 (end of week)

**PR link:** https://github.com/ascherj/pathreview/pull/1014

**Branch:** fix/149-structural-chunker-silently-drops-documents

**What you built:**
For structural_chunker.py, the fix introduced was on the content branch and the final save. I removed both gates so that the lines are always collected. Furthermore, the current_level variable was removed as it was not being used. 
For test_structural_chunker.py, the functions test_heading_path_format and test_heading_path_breadcrumb both had a boolean flag inside a loop that never got checked. This meant that both passed even if chunk() returned nothing. This was resolved by adding a trailing assertion to both of the functions. 

**Tests added or updated:**
The files that I touched include structural_chunker.py and test_structural_chunker.py. These two files are the ones that contain the actual error itself. Structural_chunker.py is the file that works as a chunker for RAG systems. The test_structural_chunker.py file works to test the functionality of each function found in the structural_chunker.py file. 

**Self-review confirmation:** [X] make check passes  [X] make test-unit passes

**Draft PR feedback received from:** None