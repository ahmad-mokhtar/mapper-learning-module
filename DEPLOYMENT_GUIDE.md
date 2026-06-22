# Deployment Guide: Mapper Notebook for Students

This guide explains how to deploy the notebook so students can access it with one click.

## Deployment Options (Ranked by Ease)

### 1. Google Colab (Recommended for Classrooms)

**Pros:**
- Zero setup for students (Google account + link)
- Full Python environment (all pip installs work)
- Can save work to Google Drive
- Collaborative editing like Google Docs
- Free tier is plenty for classroom use

**Setup:**
1. Push this repository to GitHub
2. Share this link with students:
   ```
   https://colab.research.google.com/github/[your-username]/[your-repo]/blob/main/mapper_intro.ipynb
   ```
3. Students click the link → "Open in Colab" → run cells

**What students see:**
- Notebook loads in 10 seconds
- All libraries auto-install when the first code cell runs
- Graph renders inline
- Can save a copy to their own Google Drive to modify

**Tip:** Create a shortened URL (bit.ly, tinyurl) so students can easily type or scan a QR code to access it.

---

### 2. Binder (Best for "Zero Account" Sharing)

**Pros:**
- No login required (anonymous access)
- One-click: click URL → environment loads with all dependencies
- Great for workshops, GitHub-shared projects
- All dependencies listed in `requirements.txt` are pre-installed

**Cons:**
- Takes 1-2 minutes to build the environment (first load)
- Sessions timeout after 6 hours of idle time (no persistent storage)
- Free tier is slower than Colab

**Setup:**
1. Push this repository to GitHub
2. Create a Binder link using the [Binder badge generator](https://mybinder.org/):
   - GitHub username: [your-username]
   - Repository: [your-repo]
   - Branch: main
   - Path to notebook: mapper_intro.ipynb
3. Binder generates a URL like:
   ```
   https://mybinder.org/v2/gh/[username]/[repo]/main?filepath=mapper_intro.ipynb
   ```
4. Share this link with students

**What students see:**
- Notebook loads (takes ~1-2 min for Binder to build environment)
- All libraries already installed (no `!pip install` needed)
- Environment is read-only (can view/run but can't modify permanently)

---

### 3. Kaggle Notebooks (Alternative)

**Pros:**
- Stable, no disconnects
- Integrated with Kaggle datasets
- Free GPU available
- Persistent notebooks

**Cons:**
- Requires Kaggle account
- Less familiar interface to beginners
- Slower than Colab for simple tasks

**Setup:**
1. Create a Kaggle account
2. New → Notebook
3. Upload `mapper_intro.ipynb`
4. Add libraries in notebook's built-in settings
5. Make it public, share the link

---

### 4. Local Installation (For In-Person Classes)

If students have their own laptops and you're teaching in-person:

**Setup:**
```bash
# Students run this once on their laptop:
git clone https://github.com/[username]/[repo].git
cd [repo]
pip install -r requirements.txt
jupyter notebook mapper_intro.ipynb
```

**Pros:**
- Full control, no dependency on cloud
- Works offline
- Can save/modify locally

**Cons:**
- Requires Python installation (not beginner-friendly)
- Different machines may have issues
- Best suited for a computer lab with pre-setup machines

---

## Recommendation by Scenario

| Scenario | Best Choice |
|---|---|
| **Remote class, first time coding** | Google Colab |
| **Workshop, need zero signup** | Binder |
| **Follow-up work, want students to iterate** | Google Colab (save to Drive) |
| **In-person lab with pre-setup machines** | Local (or Colab as backup) |
| **Need persistent storage/GPU** | Kaggle |

---

## GitHub Setup (Required for Colab/Binder)

1. **Create a GitHub repository** (free account at github.com)
2. **Push these files**:
   ```bash
   git clone https://github.com/[your-username]/[your-repo].git
   cd [your-repo]
   # Copy mapper_intro.ipynb, README.md, requirements.txt here
   git add .
   git commit -m "Add Mapper TDA notebook"
   git push origin main
   ```
3. **Generate a Colab link**:
   - Open https://colab.research.google.com/github/[your-username]/[your-repo]
   - Look for `mapper_intro.ipynb` → click it → right-click "Open link"

---

## Testing Checklist

Before sharing with students, verify:

- [ ] Notebook runs end-to-end on your platform (Colab, Binder, local)
- [ ] `!pip install kmapper` completes without error
- [ ] Iris dataset loads and produces a graph
- [ ] Breast cancer dataset loads and produces a graph
- [ ] Interactive graph renders (not just a blank area)
- [ ] Parameter changes (resolution, overlap, lens) affect the graph
- [ ] All markdown text is readable (no garbled characters)

**Quick test on Colab:**
1. Open the Colab link
2. Click "Runtime" → "Run all"
3. Scroll down—should see two rendered graphs without errors

---

## Sharing with Students

### Email Template
```
Subject: Try out the Mapper Algorithm (Topological Data Analysis)

Hi everyone,

I'd like you to explore how data scientists reveal hidden patterns in data using the Mapper algorithm.

Just click this link and run the notebook in your browser (no installation needed):
[Colab/Binder link here]

Try changing the parameters (filter, resolution, overlap) to see how they affect the graph. 
Can you find the best settings to reveal the structure in the medical data?

Questions? Let me know!
```

### In-Person Class
- Print QR codes linking to the notebook
- Put QR code on slides / whiteboard
- Students scan → Colab opens → start coding immediately

---

## Troubleshooting for Common Issues

### "ModuleNotFoundError: No module named 'kmapper'"
- Make sure the first code cell (`!pip install kmapper -q`) ran successfully
- Try running it again
- If on Binder, refresh the page

### Graph doesn't display
- Try scrolling up/down
- Reload the page (Ctrl+R / Cmd+R)
- On Colab: click "Runtime" → "Restart runtime" → re-run all cells

### Session disconnected (Colab)
- Colab disconnects after ~30 min idle or browser closes
- Just refresh and run cells again
- All progress in code cells is preserved

### Binder takes forever to load
- This is normal on first load (~1-2 min)
- If it times out, refresh and try again
- Binder is free but shared infrastructure

### Can't upload CSV file
- Make sure you're on Google Colab (not Binder, which doesn't have file upload from UI)
- Look for folder icon on left sidebar
- Select "Upload" option
- Choose your CSV file

---

## Customization for Your Context

Want to adapt the notebook for your students?

### Add more datasets
- Add another `elif` in Section 4 with a new dataset
- Any pandas DataFrame works: just provide `X` (features) and `y` (labels)

### Change the tone/language
- Notebook is written for high school; adapt as needed
- All text is in markdown cells (easy to edit)

### Add your own examples
- Add cells after Section 6 with specific prompts for your class
- Or modify Section 7 (Guided Exploration) to match your curriculum

### Make it interactive
- Add ipywidgets sliders for parameters (advanced)
- Students can change parameters without editing code

---

## Student Feedback (What to Ask)

After students use the notebook, ask:

1. Did you understand how Mapper works?
2. Which filter function (lens) made most sense to you?
3. Could you predict how changing resolution/overlap would affect the graph?
4. What surprised you about the breast cancer dataset?
5. Can you think of other datasets where Mapper could reveal hidden structure?

---

## Support & Documentation

- **KeplerMapper docs**: https://kepler-mapper.scikit-tda.org/
- **Topological Data Analysis intro**: https://www.youtube.com/watch?v=Qclwe-5YWho (Gunnar Carlsson TED talk)
- **Nicolau et al. 2011**: The original breast cancer Mapper paper (cited in notebook Section 8)

---

**Ready to deploy? Start with Google Colab—it's the fastest way to get students exploring!**
