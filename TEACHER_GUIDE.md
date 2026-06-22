# Teacher's Guide: Mapper Algorithm Notebook

This guide provides context, discussion questions, and extension activities for educators using this notebook in a classroom.

## Learning Objectives

By the end of this notebook, students should be able to:

1. **Understand why topology matters**: Recognize that two datasets with identical statistics can have completely different structures
2. **Explain the Mapper algorithm**: Describe the four steps (filter → cover → cluster → nerve) in plain English
3. **Tune Mapper parameters**: Predict how changing resolution, overlap, and lens will affect the output
4. **Interpret results**: Read a Mapper graph and extract insights (clusters, branches, outliers)
5. **Apply to real data**: Use Mapper on medical data to discover meaningful patterns

## Background for Teachers

### What is Topological Data Analysis (TDA)?

Topology is the mathematical study of shape and connectivity—properties that stay the same even when you stretch, squeeze, or otherwise deform an object. A coffee mug and a donut are topologically the same (both have one hole), even though they look different.

**TDA applies this to data:** It asks "What is the shape of my dataset?" rather than "What are the summary statistics?" This perspective can reveal:
- Disconnected clusters
- Branching structures
- Loops and cycles
- High-dimensional "holes" (cavities)

**Why does it matter?**
- **Medical/Biology**: Discover disease subtypes within patients diagnosed with the same disease
- **Finance**: Reveal market regimes or hidden risk factors
- **Image/Video**: Detect motion patterns, object categories
- **Networks**: Find structural patterns in social networks, molecules, etc.

### Why Mapper Specifically?

Mapper is one of the most practical TDA tools because:
1. **It's interpretable**: The output is a human-readable graph (not a black-box score)
2. **It's fast**: Can handle thousands of high-dimensional points
3. **It's tunable**: You can adjust parameters to explore different aspects of your data
4. **It's visual**: The output is interactive and compelling

### The Nicolau et al. Study (Real-World Context)

In 2011, Raúl Nicolau and colleagues applied Mapper-like methods to breast cancer gene expression data and discovered a **previously unknown breast cancer subtype**. This group:
- Had a unique gene expression "signature" that previous clustering methods missed
- Had dramatically better survival rates than other breast cancer groups
- Responded differently to treatments

This discovery would not have been possible with traditional statistics alone. It demonstrates TDA's potential to save lives.

---

## Before the Lesson

### Prerequisites
- Students should be comfortable with:
  - 2D scatter plots and what they represent
  - The concept of "clustering" (grouping similar items)
  - Basic data terminology (rows = samples/observations, columns = features)
  - The idea of a function ("input → output")

### Setup (2 hours before class)
1. Test the notebook on your platform (Colab, Binder, or local)
2. Run through all cells to make sure everything works
3. Prepare a shortened URL (bit.ly) or QR code for students
4. If using Binder, access it once to prime the cache (faster for students)
5. Prepare to share your screen for the demo

---

## Lesson Plan (45–60 minutes)

### Hook (5 minutes)
**"Why does this matter?"**

Show students two scatter plots with the same mean, variance, and correlations—but one is in a circle, the other in a line. Ask: "Which is different? How would you describe it?" → "Traditional statistics can't tell the difference. Topology can."

### Explanation (15–20 minutes)

**Section 1–2: The Concept**
- Show the four-step diagram from Section 2
- Use the student-sorting analogy: sort students by height → divide into overlapping groups → cluster them within groups → connect groups that share students

**Key point:** Emphasize the **overlapping bins**. They're the "glue" that holds the graph together.

**Analogy:**
- A street map (Mapper) vs. a satellite photo (raw data)
- A skeleton (Mapper) vs. a full body scan (raw data)
- A metro system (Mapper) vs. GPS coordinates (raw data)

### Hands-On (20–30 minutes)

**Section 3–6: Run the Notebook**
- Have students open the Colab link on their devices
- Walk them through each section:
  - Section 0: Run the setup cell
  - Section 1–2: Read the concepts (no coding yet)
  - Section 3: Explain the three parameters (filter, resolution, overlap)
  - Section 4: Choose a dataset (start with Iris for speed)
  - Section 5: Run Mapper (they don't write this code, just run it)
  - Section 6: Admire the graph together

**First graph:**
- Point out the structure: 3 clusters (one for each iris species)
- Ask: "Can you see the three branches? Why three?"

### Guided Discovery (15–20 minutes)

**Section 7: Exploration Tasks**

Guide students through the exploration one at a time:

1. **Change resolution to 3**: "What happens? Why fewer nodes?"
2. **Set overlap to 10%**: "Graph breaks apart. Why is overlap the 'glue'?"
3. **Try lens = 'main_direction'**: "Same data, different structure revealed. Why?"
4. **Switch to breast cancer data**: "Now you're analyzing real medical data. What do you see?"

### Wrap-Up (5–10 minutes)

**Reflection Questions:**
- Which was easier to understand: the algorithm or the parameters?
- Could you explain Mapper to a friend?
- What real-world data would you want to analyze with Mapper?

---

## Discussion Questions

### Conceptual

**On topology:**
- "Why is the shape of data important? Can't we just use statistics like mean and standard deviation?"
  - *Answer: Shape reveals structure that statistics miss. Two datasets can have the same mean/std but opposite topologies.*

- "What's the difference between Mapper and clustering algorithms like k-means?"
  - *Answer: k-means just partitions data into groups. Mapper shows how groups connect and interact.*

**On the Mapper steps:**
- "Why do we need overlapping bins? What happens if overlap = 0%?"
  - *Answer: Overlap connects clusters. Without it, the graph breaks into isolated islands.*

- "How is the filter function like a 'lens'? What would happen if we picked the wrong lens?"
  - *Answer: Different lenses highlight different patterns. There's no single 'right' lens—it depends what you want to see.*

**On the parameters:**
- "If I increase resolution, what happens? Is higher always better?"
  - *Answer: Higher resolution = more detail, but also more noise. You need to find the sweet spot.*

### Medical/Real-World

- "Looking at the breast cancer graph, what does the color pattern tell you?"
  - *Answer: Blue clusters = mostly benign, red = mostly malignant. Well-separated colors = two distinct groups.*

- "The Nicolau et al. study found a new breast cancer subtype. How might Mapper have revealed what clustering methods missed?"
  - *Answer: The new subtype was rare and surrounded by larger groups. Mapper's topological lens made it visible as a distinct branch.*

- "What other medical datasets do you think Mapper could analyze?"
  - *Possible answers: heart disease progression, diabetes patient types, Alzheimer's stages, cancer gene expression, drug response patterns*

### On Parameters

- "Why might a biologist choose 'eccentricity' as the filter function instead of distance-from-center?"
  - *Answer: Eccentricity reveals rare/outlier subtypes. If you're looking for rare disease phenotypes, this lens is useful.*

- "You ran the same data with two different lenses and got different graphs. Which is 'correct'?"
  - *Answer: Neither is 'correct'—they're different views. A good practice is to run multiple lenses and see which reveals the most biologically meaningful structure.*

---

## Extension Activities

### 1. Explore Other Datasets (25–40 min)
Have students load and analyze different datasets:
- **Wine dataset** (scikit-learn): 178 wines, 13 features → reveals grape varieties
- **Digits dataset** (scikit-learn): Handwritten digit images → reveals digit classes
- **Penguin dataset** (seaborn): 344 penguins → reveals species and sex differences
- **Student-provided CSV**: Have students bring or create a dataset and explore it

**Activity:** "Run Mapper with three different lenses. Which reveals the clearest structure? Why?"

### 2. Predict-Then-Experiment (15–20 min)
**Before running:** Students predict what will happen if they:
- Double the resolution
- Reduce overlap to 20%
- Switch lenses
- Change to a different dataset

**Then:** Run and compare predictions to reality. Discuss surprises.

### 3. Write Your Own Summary (10–15 min)
Students write a 1-page summary:
- What is Mapper in your own words?
- What surprised you about the breast cancer data?
- Where else could Mapper be used?
- What question would you ask if you could analyze any dataset?

### 4. Research Project (45–90 min)
**Choose a medical dataset** (UCI ML Repository, Kaggle, etc.) and prepare a presentation:
- What data did you choose? Why?
- What patterns did Mapper reveal?
- What do you think these patterns mean biologically/medically?
- What was surprising?
- How would a doctor or researcher use these findings?

**Datasets to suggest:**
- Heart disease (UCI): 303 patients
- Diabetes (UCI): 768 patients
- Parkinson's disease (UCI): 147 patients
- Autism/ASD (Kaggle): various datasets

### 5. The Parameter Sensitivity Study (30–45 min)
**Systematic exploration:** Students vary one parameter at a time and document how the graph changes:

| Filter | Resolution | Overlap | # Nodes | # Edges | Structure |
|---|---|---|---|---|---|
| distance_from_center | 5 | 50% | ? | ? | ? |
| distance_from_center | 10 | 50% | ? | ? | ? |
| distance_from_center | 15 | 50% | ? | ? | ? |
| main_direction | 10 | 50% | ? | ? | ? |
| how_isolated | 10 | 50% | ? | ? | ? |

**Analysis:** "Which parameter has the biggest impact on the graph? Which combinations reveal the clearest structure?"

### 6. Compare Mapper to Other Methods (30–45 min)
**For advanced students:** Compare Mapper's output to:
- k-means clustering (scikit-learn)
- Hierarchical clustering (scipy)
- t-SNE or UMAP visualization

Questions:
- What does each method reveal about the data?
- Where do they agree? Disagree?
- When would you use Mapper over other methods?

---

## Common Misconceptions

**"Mapper finds 'the true structure' of the data"**
- *Correction: Mapper reveals one perspective of the structure, dependent on the chosen lens, resolution, and overlap. Always try multiple settings.*

**"More resolution is always better"**
- *Correction: Very high resolution adds noise. You need to balance detail with interpretability.*

**"If two datasets have the same Mapper graph, they're equivalent"**
- *Correction: Same topology ≠ same data. The graph shows structure, not the actual values or distances.*

**"The colors in the graph tell you the 'true' classification"**
- *Correction: Colors show a label from the data, but Mapper doesn't use those labels—it discovers structure independently. The fact that color patterns align with structure is meaningful, but doesn't guarantee correctness.*

---

## Assessment Ideas

### Formative (During the Lesson)
- Ask students to predict what the graph will look like before running a cell
- Ask them to explain why changing a parameter changed the output
- Ask them to describe the structure they see (branches, loops, clusters)

### Summative (After the Lesson)
1. **Concept check**: Students write one paragraph explaining Mapper in their own words
2. **Parameter interpretation**: Show a graph and ask students to infer likely parameter settings
3. **Real-world application**: Students propose a medical dataset and explain what Mapper might reveal
4. **Research project**: Analyze a dataset and present findings

---

## Safety & Privacy Notes

- **Datasets included**: Both are public, de-identified benchmark datasets (commonly used in ML education)
- **Google Colab**: Remind students that their work saves to their Google Drive (their data, their account)
- **Binder**: Remind students that Binder sessions are temporary (don't rely on it for long-term work)
- **Custom data**: If students upload their own CSV, emphasize: "Never upload real patient data or personally identifiable information"

---

## Time Budget

| Activity | Time |
|---|---|
| Hook + motivation | 5 min |
| Explain concepts (Sections 1–2) | 15 min |
| Explain parameters (Section 3) | 5 min |
| Run Mapper on Iris (Sections 4–6) | 10 min |
| Guided exploration (Section 7) | 15 min |
| Wrap-up discussion | 10 min |
| **Total** | **~60 min** |

For a 45-minute period: skip the research project and reduce exploration to 2-3 tasks.
For a 90-minute period: add an extension activity (compare datasets, sensitivity study, etc.).

---

## Accessibility & Inclusivity

- **For students with visual impairments**: Describe the graph structure in words. Ask them to interpret patterns by listening to descriptions.
- **For students with limited English**: Use the simple language in the notebook, and allow them to discuss in their native language before reporting findings.
- **For students with math anxiety**: Emphasize: "No advanced math required. Just understanding steps and observing patterns."
- **For advanced students**: Suggest extension activities, parameter sensitivity studies, or introducing concepts like persistent homology.

---

## Resources for Further Learning

**For Teachers:**
- Stanford Online "Introduction to Topological Data Analysis" course
- Gunnar Carlsson (founder of Ayasdi, leader in TDA) TED talk: "Topology and Data"
- Gurjeet Singh's TDA tutorial videos on YouTube

**For Students:**
- KeplerMapper documentation: https://kepler-mapper.scikit-tda.org/
- Nicolau et al. 2011 paper (cited in notebook)
- 3Blue1Brown's "The Essence of Topology" video (mathematical background)

**Tools to Explore After This Notebook:**
- `giotto-tda`: More advanced TDA library (persistent homology)
- `ripser`: Fast computation of persistent homology
- `gudhi`: French TDA library with many algorithms

---

**Happy teaching! Questions? Suggestions for improvements? Please share them!**
