# EFD TextFix — AI Model Test Plan

## 1. Purpose

Evaluate the initial AI model candidate for EFD TextFix before implementation.

The model must correct spelling, grammar, and punctuation, improve text clarity, and rewrite text without changing its original meaning.

## 2. Model Candidate

- Provider: OpenAI API
- Candidate model: GPT-6 Luna
- Status: Pending evaluation
- Production approval: Not granted
- Implementation status: Not started

Model availability and actual API pricing must be verified before production approval.

## 3. Test Scope

The initial evaluation covers English and Russian text.

### Test 1 — Spelling Correction

**Objective:** Correct spelling mistakes without unnecessarily changing the text.

**Expected result:** Spelling errors are corrected, and the original meaning is preserved.

### Test 2 — Grammar Correction

**Objective:** Correct grammatical errors.

**Expected result:** The text is grammatically correct and retains the original tone and meaning.

### Test 3 — Punctuation Correction

**Objective:** Correct punctuation errors.

**Expected result:** Punctuation is corrected without unnecessary rewriting.

### Test 4 — Text Improvement

**Objective:** Improve clarity, readability, and sentence structure.

**Expected result:** The text becomes easier to understand without adding unsupported information.

### Test 5 — Rewrite

**Objective:** Rewrite text in a clearer or more natural style.

**Expected result:** The wording may change, but the original meaning and important details remain intact.

### Test 6 — Meaning Preservation

**Objective:** Verify that the model preserves names, numbers, dates, facts, and the author's intent.

**Expected result:** No important information is invented, removed, or altered.

### Test 7 — Short and Long Inputs

**Objective:** Evaluate responses to short text and longer text near the application's input limit.

**Expected result:** The model processes valid inputs reliably and handles invalid or oversized inputs safely.

### Test 8 — API Cost and Response Time

**Objective:** Measure actual input tokens, output tokens, request cost, and response time.

**Expected result:** The observed cost and performance are suitable for the one-month MVP experiment.

## 4. Evaluation Criteria

For each test, record:

- Test language
- Input text
- Expected result
- Actual model output
- Meaning preserved: Yes / No
- Errors or unexpected changes
- Response time
- Token usage and cost, when available
- Pass / Fail

## 5. Approval Requirements

The model may be approved for the MVP only after:

1. Basic spelling, grammar, and punctuation tests pass.
2. Rewriting preserves the original meaning.
3. English and Russian tests produce acceptable results.
4. Actual API availability and pricing are verified.
5. Actual request costs are reviewed against the $5 total experiment budget.
6. Privacy and security requirements are confirmed.

## 6. Budget Constraints

- Total planned API budget: $5 for the one-month experiment.
- Proposed internal stop threshold: $4.
- Initial global request limit: 300 requests per month.
- Maximum input length: 5,000 characters.
- No text persistence by default.
- API credentials must remain server-side.

These are project limits, not guarantees of provider-side spending enforcement. Additional safeguards must be verified during implementation.

## 7. Current Status

- [x] Initial model candidate selected.
- [ ] Test cases executed.
- [ ] Model quality evaluated.
- [ ] Actual API cost measured.
- [ ] Model approved for production.
- [ ] Implementation started.

**Current decision:** GPT-6 Luna remains a candidate. Production approval is pending evaluation.