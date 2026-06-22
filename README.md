# Mapper Algorithm: An Introduction to Topological Data Analysis

A Jupyter notebook designed for high school students to explore the **Mapper algorithm** from topological data analysis (TDA) using real medical data.

## Quick Start

### For Students (Zero Installation Required)

**Option 1: Google Colab (Recommended)**

Click this link to open the notebook directly in Google Colab (no installation, just a Google account):

```
https://colab.research.google.com/github/[your-github-username]/[your-repo]/blob/main/mapper_intro.ipynb
```

Then:
1. Click "Runtime" → "Run all" to run all cells at once, or
2. Run cells one at a time from top to bottom
3. Edit the parameters in Section 3 and Section 4 to experiment

**Option 2: Binder (No Account Required)**

Click this link to open on Binder (no login, but may take a minute to load):

```
https://mybinder.org/v2/gh/[your-github-username]/[your-repo]/main?filepath=mapper_intro.ipynb
```

### For Educators

If you want to modify or adapt the notebook:

1. **Clone or download this repository**
2. **Install dependencies** (if running locally):
   ```bash
   pip install -r requirements.txt
   ```
3. **Open the notebook**:
   ```bash
   jupyter notebook mapper_intro.ipynb
   ```

## What's in the Notebook?

The notebook covers:

- **Section 1**: Why topology matters in data
- **Section 2**: The 4 steps of the Mapper algorithm (with diagrams)
- **Section 3**: Three tunable parameters:
  - **Filter function** (lens): How to rank/project data
  - **Resolution**: How finely to slice the data
  - **Overlap**: How much neighboring slices should overlap
- **Section 4**: Two built-in datasets (Iris flowers, Wisconsin Breast Cancer) + CSV upload option
- **Section 5**: Runs Mapper with your chosen parameters
- **Section 6**: Interactive visualization (D3.js graph)
- **Section 7**: Guided exploration tasks for students
- **Section 8**: Real-world context (Mapper in medical research)

## Datasets Included

1. **Iris Flowers** (150 samples, 4 features)
   - Fast, easy to understand
   - Good for learning the basics

2. **Wisconsin Breast Cancer** (569 samples, 30 features)
   - Real medical data
   - Reveals meaningful structure: benign vs. malignant patients

## System Requirements

- **Online (Colab/Binder)**: A web browser. That's it.
- **Local (if running on your computer)**:
  - Python 3.7+
  - Jupyter Notebook or JupyterLab
  - Libraries: kmapper, scikit-learn, pandas, numpy, matplotlib

## Troubleshooting

### On Google Colab:
- **"Module not found" error**: The `!pip install kmapper` cell at the top may not have completed. Run it again.
- **Graph doesn't display**: Try reloading the page and re-running the notebook.

### On Binder:
- **Takes a long time to load**: Binder builds the environment on demand. It may take 1-2 minutes. Be patient.
- **"Module not found" error**: This shouldn't happen if using Binder (all dependencies are pre-installed), but if it does, run the `!pip install kmapper` cell.

### Running locally:
- Install all dependencies: `pip install -r requirements.txt`
- Make sure Jupyter is installed: `pip install jupyter`
- If visualization doesn't show in Jupyter, enable the nbconvert extension: `jupyter nbconvert --to notebook --execute mapper_intro.ipynb`

## Parameters Explained (for Students)

### Filter Function (The Lens)
How do we "sort" the data before dividing it?

- **distance_from_center** (L2 norm): Each point gets a score based on how far it is from the center. Reveals radial/spherical structure.
- **main_direction** (PCA): Project onto the first principal component (the direction of most variation). Good for seeing linear trends.
- **how_isolated** (kNN distance): Measures how far each point is from its neighbors. Reveals clusters and outliers.

### Resolution (n_intervals)
How many slices should we cut the data into?
- 3-5: Coarse, simple picture
- 10: Default, good balance
- 15-30: Fine detail, more complex graph
- Higher values reveal finer structure but can add noise

### Overlap (overlap_pct)
How much should neighboring slices overlap (as a percentage)?
- 10-20%: Sparse, graph may disconnect
- 30-50%: Common, good balance
- 60-100%: Dense, might over-smooth structure

## Real-World Applications

Mapper has been used to:
- **Discover cancer subtypes** in genomic data (Nicolau et al., 2011)
- **Analyze protein structures** in structural biology
- **Study patient stratification** in disease progression
- **Reveal hidden patterns** in high-dimensional datasets

See Section 8 of the notebook for more details.

## References

- **KeplerMapper Documentation**: https://kepler-mapper.scikit-tda.org/
- **Nicolau et al. (2011)**: "Topology based data analysis identifies a subgroup of breast cancers with a unique mutational profile and excellent survival" — *PNAS*, 108(17):7265-7270
- **Singh, Memoli, & Carlsson (2007)**: "Topological methods for data analysis and visualization of high-dimensional datasets" — *IEEE Symposium on Information Visualization*
- **Carlsson, G. (2009)**: "Topology and data" — *Bulletin of the American Mathematical Society*

## License

This notebook is provided as an educational resource. Feel free to adapt it for your classroom or research.

## Questions or Suggestions?

If you have suggestions for improving this notebook, please open an issue or pull request!

---

**Happy mapping! 🗺️**
