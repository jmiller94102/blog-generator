# Master Plan: Blog Generator Project

## 🚀 Project Objective
Build an AI-powered blog/content generator that captures a user's unique writing style and enables seamless content generation and refinement, with robust style validation and a modern, intuitive workflow.

---

## ✅ Progress & Completed Features

- **Style Analysis:**
  - Users can upload writing samples to create a style profile.
  - StyleAnalyzer extracts stylistic metrics (sentence length, tone, vocabulary, etc.).
  - Style profiles are stored in ChromaDB.
- **Content Generation:**
  - Users select style, topic, and other parameters to generate content.
  - Purpose is now a dropdown (inform, persuade, entertain, inspire, connect).
  - Content and metadata are stored in ChromaDB.
- **Refine Workflow:**
  - Users can immediately refine generated content without entering Content ID.
  - Feedback is submitted and new content is generated/refined via LLM.
  - UI merged: "Generate & Refine Content" is a single workflow.
- **Backend Improvements:**
  - Metadata storage in ChromaDB is robust (lists converted to strings).
  - FastAPI endpoints are aligned with frontend form-data expectations.
- **UI/UX:**
  - Streamlit UI is modern, intuitive, and streamlined.
  - All major workflows are accessible from the sidebar.

---

## 🔜 Next Feature: Style Validation & Comparison

### Goal
Automatically validate that generated/refined content matches the user’s style profile, and provide clear feedback (both quantitative and visual) to the user.

### Task Breakdown (Prioritized & Sequential)

1. **Style Analysis of Output**
    - [ ] Add logic to run StyleAnalyzer on generated/refined content.
    - [ ] Store the output style profile for each generated/refined text.
2. **Comparison Logic**
    - [ ] Compare the style profile of the user's sample(s) vs. generated/refined output.
    - [ ] Compute similarity scores (cosine similarity, Euclidean, or custom metric).
    - [ ] Highlight key stylistic attributes and differences.
3. **UI/UX for Validation**
    - [ ] Display side-by-side comparison of sample and output style profiles in Streamlit.
    - [ ] Show similarity score and highlight mismatches.
    - [ ] Optionally, allow user to download or export the comparison.
4. **Feedback Loop & Thresholds**
    - [ ] Set minimum similarity threshold for style match.
    - [ ] Warn user or reject outputs that do not meet threshold.
    - [ ] Allow user to provide feedback on style match quality.
5. **Testing & Documentation**
    - [ ] Add tests for style comparison logic.
    - [ ] Document the validation workflow and update user guides.

---

## 🧹 Clean Up & File Pruning (Pre-Merge)

### Candidate Files for Deletion (Validate Before Deleting)
- `src/blog_generator/api/main.py` (deprecated, use app.py)
- `src/blog_generator/main.py` (legacy entry point, replaced by Streamlit and FastAPI)
- `src/blog_generator/main_cli.py` (old CLI, superseded by UI)
- `src/blog_generator/core/style_cli.py` (manual style analysis, replaced by UI)
- `src/blog_generator/backend.py` (old backend, not referenced)
- `src/blog_generator/app.py` (old app entry, not referenced)
- `src/blog_generator/fix_embeddings.py` (temporary script)
- `src/blog_generator/env_template.py` (if not used)
- `src/blog_generator/content_flow_plot.py` (dev visualization)
- `src/blog_generator/content_generation_flow.html` (legacy visualization)
- `src/blog_generator/TESTING.md` (if not up-to-date)

### Rationale
- These files are either deprecated, replaced by new workflows, or were used for development/testing only. **Validate there are no remaining references before deleting.**

### To Keep
- All files in `src/blog_generator/api/` except `main.py` (use `app.py`)
- All files in `src/blog_generator/core/` except `style_cli.py`
- All files in `src/blog_generator/database/`
- All files in `src/blog_generator/tools/`
- All files in `src/blog_generator/ui_streamlit.py`
- All YAML config and crew/task files
- All utility files in `src/blog_generator/utils/`

---

## 🗂️ Git Repo File List (Post-Cleanup)
- README.md
- src/blog_generator/api/app.py
- src/blog_generator/api/routes.py
- src/blog_generator/api/__init__.py
- src/blog_generator/core/content_generator.py
- src/blog_generator/core/format_adapter.py
- src/blog_generator/core/knowledge_base.py
- src/blog_generator/core/style_analyzer.py
- src/blog_generator/core/style_models.py
- src/blog_generator/database/chroma_client.py
- src/blog_generator/database/models.py
- src/blog_generator/tools/*
- src/blog_generator/ui_streamlit.py
- src/blog_generator/crews/*
- src/blog_generator/flows/*
- src/blog_generator/utils/*
- All relevant data/knowledge/templates as needed

---

## 📅 Next Steps
1. Complete the style validation & comparison feature (see task list above).
2. Validate and delete unnecessary files.
3. Final QA, update docs, and merge branch into main.

---

_Last updated: 2025-04-29_
