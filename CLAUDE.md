# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Status

**Mapper Algorithm Jupyter Notebook for High School TDA Education** — Complete and tested in Google Colab.

A single-notebook educational project introducing topological data analysis (Mapper algorithm) to high school students with no coding background. The notebook runs entirely online (Google Colab or Binder) with zero local installation required.

## Getting Started

### Install Dependencies (for local development)
```bash
pip install -r requirements.txt
jupyter notebook mapper_intro.ipynb
```

### Run the Notebook Online (for students)
- **Google Colab**: https://colab.research.google.com/github/ahmad-mokhtar/mapper-learning-module/blob/main/mapper_intro.ipynb
- **Binder**: https://mybinder.org/v2/gh/[username]/[repo]/main?filepath=mapper_intro.ipynb

### Test the Notebook in Colab
1. Open the Colab link
2. Click "Runtime" → "Run all"
3. Verify Section 2 diagram renders
4. Verify Section 6 Mapper graph renders with light gray background and dark text
5. Change parameters in Section 3/4 and re-run Section 5–6 to confirm responsiveness

## Architecture

### Notebook Structure (8 Sections)

**Section 0: Setup**
- Single cell: `!pip install kmapper -q`
- Installs KeplerMapper library

**Section 1: Motivation**
- Conceptual introduction: why topology matters
- Key insight: shape vs. statistics

**Section 2: Algorithm Explanation**
- 4-step Mapper algorithm (Filter → Cover → Cluster → Nerve)
- Auto-generated matplotlib diagram with visual analogies

**Section 3: Parameters**
- Three tunable dials:
  - `filter_choice`: "distance_from_center" | "main_direction" | "how_isolated"
  - `n_intervals`: resolution (5–30)
  - `overlap_pct`: overlap percentage (10–70)
- Clearly marked `# ← CHANGE THESE` for students

**Section 4: Data Loading**
- `DATASET`: "iris" | "breast_cancer"
- Loads built-in scikit-learn datasets (zero download)
- Displays data summary and first 5 rows
- Optional: CSV upload for Colab

**Section 5: Run Mapper**
- Pre-written code (students run, don't write)
- Normalizes data → applies filter → builds cover → clusters → computes graph
- Outputs: number of nodes and edges

**Section 6: Visualization**
- KeplerMapper D3.js interactive graph
- Displayed via data URI (Colab-compatible)
- Custom CSS: light gray background (#f5f5f5), dark text (#333333)
- Nodes colored by class label, sized by cluster density

**Section 7: Guided Exploration**
- 5 structured tasks for students
- Predict → experiment → observe
- Builds intuition about parameter effects

**Section 8: Real-World Context**
- Nicolau et al. (2011) cancer subtype discovery
- Why Mapper is powerful (preserves connectivity, interpretable, flexible)
- Pointers to research and further learning

### Key Design Decisions

| Decision | Rationale |
|---|---|
| **Single notebook** | Students focus on one task; no file management overhead |
| **KeplerMapper** | Best-documented TDA library; beautiful D3.js visualization |
| **Google Colab** | Zero friction for students (click link → run) |
| **Data URI embedding** | Bypasses Colab sandboxing; D3.js renders properly |
| **Light gray background** | Better readability and visual appeal vs. dark default |
| **Pre-written code** | Students focus on concepts, not syntax; lower barrier to entry |
| **Real medical data** | Iris for learning, Breast Cancer for meaningful context |
| **Three filter functions** | Explore different topological perspectives on the same data |

### Data Flow

1. Student opens Colab link
2. Sections 0–2: Setup and concept
3. Section 3: Set parameters (filter, resolution, overlap)
4. Section 4: Choose dataset (Iris or Breast Cancer)
5. Section 5: Run Mapper algorithm
   - Input: `X_scaled` (normalized data), `lens` (filter), `cover` (bins), `clusterer` (DBSCAN)
   - Output: `graph` (dict with 'nodes' and 'links'), `color_values` (class labels)
6. Section 6: Visualize
   - KeplerMapper generates D3.js HTML
   - Inject CSS for styling
   - Encode as data URI
   - Display in IFrame
7. Section 7: Explore by repeating 3–6 with different parameters
8. Section 8: Reflect on findings

### Dependencies

- **kmapper** (≥2.1.0): Mapper algorithm implementation
- **scikit-learn** (≥1.0.0): Datasets, preprocessing, PCA, DBSCAN, kNN
- **pandas** (≥1.3.0): Data display
- **numpy** (≥1.21.0): Array operations
- **matplotlib** (≥3.4.0): Section 2 diagram generation

All are actively maintained and stable.

### Visualization Technology

- **Backend**: KeplerMapper (wraps D3.js)
- **Format**: Interactive HTML with D3.js force-directed layout
- **Rendering**: Data URI + IFrame (Colab-compatible)
- **Styling**: Injected CSS for light gray background and dark text
- **Interactivity**: Hover for details, click/drag to reposition, zoom

### Known Issues & Fixes

| Issue | Fix | Status |
|---|---|---|
| TypeError in Section 6 (old code) | Use `save_file=False` | ✓ Fixed |
| Black visualization page | Switch from `HTML()` to data URI + IFrame | ✓ Fixed |
| D3.js not rendering in IFrame | Use base64 data URI instead of file path | ✓ Fixed |
| Dark background hard to read | Inject CSS for light gray + dark text | ✓ Fixed |

## Testing

### Automated Testing
Not applicable (notebook-based project with visual output).

### Manual Testing Checklist
- [ ] Notebook runs top-to-bottom in Colab without errors
- [ ] Section 2 diagram renders correctly
- [ ] Section 6 Mapper graph displays with light gray background
- [ ] Changing `filter_choice` produces visibly different graphs
- [ ] Changing `n_intervals` changes node count
- [ ] Changing `overlap_pct` to 10% breaks connectivity
- [ ] Switching `DATASET` updates graph appropriately
- [ ] CSV upload works (Colab only)

## Maintenance Notes

- **KeplerMapper API**: Monitor for breaking changes (check GitHub releases)
- **Colab compatibility**: Test on each major Colab update
- **Browser compatibility**: Works in Chrome, Firefox, Safari
- **Mobile support**: Notebook responsive on tablets; full interactivity on desktop

## Documentation Files

- **README.md**: Quick start and troubleshooting for students
- **TEACHER_GUIDE.md**: Learning objectives, discussion questions, extension activities
- **DEPLOYMENT_GUIDE.md**: How to share (Colab, Binder, local)
- **SETUP_CHECKLIST.md**: Pre-class preparation
- **SUMMARY.md**: Complete project overview
- **.gitignore**: Excludes `.ipynb_checkpoints/`, Python artifacts, IDE config
