Code Development Guidelines
⚠️ CRITICAL: These guidelines MUST be followed for every feature addition, bug fix, or modification.

Pre-Development Analysis (MANDATORY)
Before implementing ANY new functionality, you MUST perform a comprehensive analysis of existing code:

1. Search for Existing Functionality
Always search the codebase using multiple patterns to identify any existing or partial implementations:

# Search for function names (current and variations)
grep -r "functionName\|function_name\|FunctionName" .

# Search for CSS classes and IDs  
grep -r "\.class-name\|#element-id" .

# Search for HTML elements and attributes
grep -r "onclick.*functionName\|data-.*\|id.*element" .

# Search for JavaScript event handlers
grep -r "addEventListener\|onclick\|onchange\|toggle" .

# Search for related keywords and comments
grep -ri "feature.*name\|todo.*feature\|fixme.*feature" .
2. Analysis Decision Matrix
For each piece of existing code found:

Found Code Status	Action Required
Complete & Working	→ Extend/modify existing code
Partial Implementation	→ Complete existing code OR replace entirely
Broken/Incomplete	→ Fix existing code OR replace entirely
Duplicate Functions	→ Consolidate into single implementation
No Existing Code	→ Create new implementation
3. Cleanup Requirements
When adding new functionality, you MUST:

✅ Remove ALL duplicate functions
✅ Remove unused CSS styles
✅ Remove commented-out code blocks
✅ Update related documentation/comments
✅ Ensure consistent naming conventions
✅ Verify no dead code remains

Implementation Process
Step 1: Comprehensive Code Analysis
# Example: Before adding evidence section functionality
grep -r "evidence\|Evidence" .
grep -r "toggle.*section\|toggleSection" .
grep -r "\.evidence\|#evidence" .
grep -r "notes.*editor\|Editor" .
grep -r "quill\|Quill" .
Step 2: Document Findings
Create a mental or written inventory:

Functions found: toggleEvidenceSection() (incomplete)
CSS found: .evidence-* (missing)
HTML found: evidence section structure (present)
JavaScript found: Quill editor init (partial)
Step 3: Make Implementation Decision
EXTEND: Build upon existing partial implementation
REPLACE: Remove old code and create new implementation
REFACTOR: Improve existing working code
Step 4: Execute with Cleanup
Implement the solution
Remove ALL duplicate/old functionality
Test thoroughly
Update documentation
Code Integration Patterns
Pattern 1: Extending Existing Code
// GOOD: Extend existing function
function existingToggleFunction(id) {
    // Add new functionality to existing function
    const element = document.getElementById(id);
    // ... enhanced logic
}

// BAD: Create duplicate function
function newToggleFunction(id) { /* duplicate logic */ }
Pattern 2: Replacing Incomplete Code
// 1. REMOVE incomplete function:
// function toggleEvidenceSection(contentId) { /* incomplete */ }

// 2. REPLACE with complete implementation:
function toggleEvidenceSection(contentId) {
    // Complete, robust implementation
    // ... full functionality
}
Pattern 3: CSS Consolidation
/* GOOD: Single, complete CSS section */
.evidence-section {
    /* All evidence-related styles here */
}

/* BAD: Scattered, duplicate styles */
.evidence { /* incomplete */ }
.evidence-section { /* duplicate */ }
Common Mistakes to Avoid
❌ Anti-Pattern: Ignoring Existing Code
// WRONG: Adding new function without checking for existing
function newFeatureFunction() { /* ... */ }

// MISSED: Existing partial implementation
function featureFunction() { /* incomplete but exists */ }
❌ Anti-Pattern: Creating Duplicates
// WRONG: Multiple functions for same purpose
function toggleContent() { /* version 1 */ }
function toggleSection() { /* version 2 - duplicate! */ }

// RIGHT: Single, comprehensive function  
function toggleSection(type, id) { /* handles all cases */ }
❌ Anti-Pattern: Leaving Dead Code
// WRONG: Leaving old code commented out
// function oldToggleFunction() { /* old version */ }

// RIGHT: Remove completely and use version control for history
Quality Assurance Checklist
Before submitting changes, verify:

 No duplicate functions exist
 No unused CSS classes remain
 No commented-out code blocks
 All related functionality is consolidated
 Function names are consistent and clear
 Documentation reflects current implementation
 All features work as expected
 No JavaScript console errors
Case Study: Evidence Section Issue
What Went Wrong:

❌ Failed to search for existing toggleEvidenceSection function
❌ Added new implementation without removing old one
❌ Created duplicate, conflicting functionality
❌ Left old CSS and HTML incomplete
What Should Have Happened:

✅ Search: grep -r "toggleEvidence\|evidence.*section" .
✅ Find: Existing incomplete function
✅ Analyze: Function present but incomplete
✅ Decide: Replace incomplete function entirely
✅ Implement: Complete functionality in single function
✅ Cleanup: Remove old incomplete function
✅ Verify: No duplicates remain
Emergency Code Cleanup
If you discover duplicate/conflicting code:

STOP current implementation
IDENTIFY all related functions/code
CHOOSE the most complete/correct version
REMOVE all duplicates and incomplete versions
CONSOLIDATE functionality into single implementation
TEST thoroughly
DOCUMENT the cleanup in commit message
Remember: Prevention > Correction
It is ALWAYS better to spend extra time analyzing existing code than to create conflicts that require emergency cleanup later.

Focus on identifying actual issues and creating strategic and targeted fixes over non-strategic debugging and logging.
