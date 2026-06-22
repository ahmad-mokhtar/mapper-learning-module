# Setup Checklist: Getting Ready to Share the Mapper Notebook

Use this checklist to prepare the notebook for sharing with students.

## 1. Repository Setup

- [ ] Create a GitHub repository (free at github.com)
  - Name suggestion: `mapper-tda-notebook` or `topological-data-analysis-intro`
  - Description: "Interactive Jupyter notebook introducing the Mapper algorithm to high school students"
  - Make it public (so Colab/Binder can access it)

- [ ] Push files to GitHub:
  ```bash
  git clone https://github.com/[your-username]/[repo-name].git
  cd [repo-name]
  # Copy these files to the directory:
  #   - mapper_intro.ipynb
  #   - README.md
  #   - requirements.txt
  #   - TEACHER_GUIDE.md (optional, for educators)
  #   - DEPLOYMENT_GUIDE.md (optional, for educators)
  git add .
  git commit -m "Initial commit: Mapper TDA notebook for high school students"
  git push origin main
  ```

## 2. Generate Sharing Links

### For Google Colab
- [ ] Visit: `https://colab.research.google.com/github/[your-username]/[your-repo-name]`
- [ ] Find `mapper_intro.ipynb` in the list → click it
- [ ] Verify the notebook loads
- [ ] Copy the URL from the address bar
- [ ] Shorten the URL using bit.ly or TinyURL (optional but recommended)
  - Example short URL: `https://bit.ly/mapper-tda` or similar
- [ ] **Save this as your primary sharing link**

### For Binder (Optional)
- [ ] Visit: `https://mybinder.org/v2/gh/[your-username]/[your-repo-name]/main?filepath=mapper_intro.ipynb`
- [ ] Test: click the link and wait for environment to build
- [ ] Verify the notebook loads and `!pip install kmapper` isn't needed (since `requirements.txt` pre-installed it)
- [ ] Keep this link as a backup option

## 3. Test the Notebook

### On Google Colab
- [ ] Open the Colab link in an incognito/private browser window (simulates first-time user)
- [ ] Run "Runtime" → "Run all"
- [ ] Verify all cells complete without errors
- [ ] Confirm the interactive Mapper graph renders (should see a D3.js visualization)
- [ ] Check that Iris graph has 3 visible clusters
- [ ] Check that Breast Cancer graph has 2 main lobes (blue/red separation)
- [ ] Test changing a parameter (e.g., `n_intervals = 5`) and re-running Sections 5–6
  - Verify the graph changes
- [ ] Test changing the dataset to "breast_cancer" and re-running Sections 4–6
  - Verify the graph updates

### On Binder (if using)
- [ ] Open the Binder link
- [ ] Wait for environment to build (~1-2 min)
- [ ] Run "Cell" → "Run All"
- [ ] Verify all cells complete without errors
- [ ] Confirm graphs render

### Locally (if you'll run it on a local machine)
- [ ] Clone the repo: `git clone https://github.com/[username]/[repo].git`
- [ ] Install dependencies: `pip install -r requirements.txt`
- [ ] Open notebook: `jupyter notebook mapper_intro.ipynb`
- [ ] Run all cells → verify graphs render

## 4. Prepare for Classroom

### Materials
- [ ] Write down the Colab link (and short URL if created)
- [ ] Create a QR code pointing to the link (use qr-code-generator.com)
- [ ] Print QR codes (optional, for in-class setup)
- [ ] Print TEACHER_GUIDE.md (optional, for reference during class)
- [ ] Prepare discussion questions from TEACHER_GUIDE.md Section "Discussion Questions"

### Technology
- [ ] Test that the link works on multiple devices (phone, tablet, laptop)
- [ ] Test that it works on different browsers (Chrome, Safari, Firefox)
- [ ] Verify you can share screen with your class if demonstrating
- [ ] If in-person: ensure students have laptop/tablet access

### Student Instructions
- [ ] Prepare email/handout explaining:
  - What is Mapper?
  - How to access the notebook (link or QR code)
  - What they'll learn
  - How long it takes (~45 min)
  - What to look for (Section 7 exploration tasks)

## 5. Optional Enhancements

- [ ] Add a `LICENSE.md` file (e.g., CC-BY 4.0 for educational content)
- [ ] Add a `.gitignore` file (ignore `*.ipynb_checkpoints/`)
- [ ] Create a GitHub issue template for student questions
- [ ] Set up GitHub Discussions for students to share findings
- [ ] Record a short video walkthrough (for asynchronous learning)
- [ ] Create a discussion forum (Piazza, Discord, Google Classroom) for student questions

## 6. First Run with Students

### Before Class
- [ ] Send link to students a day before (so they can test access)
- [ ] Plan which exploration tasks you'll guide (from Section 7)
- [ ] Prepare 2-3 discussion questions to use

### During Class
- [ ] Have students open the link → wait for notebook to load
- [ ] Demonstrate running Section 0 (setup)
- [ ] Walk through Sections 1–2 (concept)
- [ ] Guide Sections 3–6 (run Mapper together)
- [ ] Have students do Sections 7 independently (or in pairs)
- [ ] Discuss findings as a group

### After Class
- [ ] Collect feedback: "What did you learn? What was confusing?"
- [ ] Save student questions for next offering
- [ ] Note any cells that failed or need updating

## 7. Ongoing Maintenance

- [ ] Check GitHub for issues/questions from students
- [ ] Update the notebook if Mapper API changes (check KeplerMapper docs)
- [ ] Keep `requirements.txt` updated as libraries evolve
- [ ] Add new datasets or features based on student feedback
- [ ] Consider adding more guided exploration tasks

## 8. Documentation Files Included

- [ ] `README.md` — Quick start, datasets, troubleshooting
- [ ] `TEACHER_GUIDE.md` — Learning objectives, discussion questions, extension activities
- [ ] `DEPLOYMENT_GUIDE.md` — How to share (Colab, Binder, local)
- [ ] `SETUP_CHECKLIST.md` — This file

## 9. Troubleshooting Preparation

- [ ] Read through the "Troubleshooting" sections in README.md and DEPLOYMENT_GUIDE.md
- [ ] Practice the most common fixes:
  - Running `!pip install kmapper` again
  - Restarting Colab runtime
  - Refreshing the page
- [ ] Prepare a backup link (in case one platform goes down)

---

## Timeline

**1 week before class:**
- [ ] Create GitHub repo
- [ ] Push files
- [ ] Test on Colab and Binder
- [ ] Generate short URLs

**3 days before class:**
- [ ] Send link to students
- [ ] Prepare discussion questions
- [ ] Print any materials

**1 day before class:**
- [ ] Do a final test run
- [ ] Prepare your demo (which sections you'll show)

**Day of class:**
- [ ] Have backup link ready
- [ ] Have printed copies of troubleshooting tips
- [ ] Start class 5 minutes early to help students access the link

---

## Final Checklist

- [ ] Colab link works ✓
- [ ] Binder link works (if using) ✓
- [ ] All cells run without error ✓
- [ ] Graphs render correctly ✓
- [ ] Students can access the link ✓
- [ ] Teacher materials are organized ✓
- [ ] First lesson is planned ✓

**Ready to share with students? You're all set! 🚀**
