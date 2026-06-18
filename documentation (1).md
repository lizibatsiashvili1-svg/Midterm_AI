# Course Transfer Planner — Documentation

**Student:** Lizi Batsiashvili  
**Current Program:** Civil Engineering (ENG)  
**University:** Ilia State University  

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [How to Use the Application](#how-to-use-the-application)
3. [Course List](#course-list)
4. [Equivalency Algorithm](#equivalency-algorithm)
5. [Target Programs and Their Courses](#target-programs-and-their-courses)
6. [Future Improvements: Automatic Syllabus Comparison](#future-improvements-automatic-syllabus-comparison)

---

## Project Overview

This single-page web application helps a Civil Engineering student plan a transfer to one of three other undergraduate programs at Ilia State University. It displays all courses from the student's transcript, marks each as passed or not passed, and — when the user selects a target program and clicks "Transfer" — generates an equivalency table showing which of the student's completed courses correspond to courses in the new program.

**Technologies used:** HTML, CSS, JavaScript (all in one file, no external dependencies).

---

## How to Use the Application

1. Open `index.html` in any modern browser.
2. The course table loads automatically with all courses and their pass/fail status.
3. Use the search bar to filter courses by name.
4. Select a target program from the dropdown menu.
5. Click the **Transfer** button to see the equivalency table.
6. The equivalency table shows which of your passed courses match courses in the target program. Courses with no match show **N/A**.

---

## Course List

The table below lists all courses from the transcript. Courses marked **Yes** have been passed. Courses marked **No** have not yet been passed or are in progress.

| Course | Passed |
|--------|--------|
| Academic Techniques (ENG) | Yes |
| Calculus I (ENG) | Yes |
| Calculus II (ENG) | Yes |
| Calculus III (ENG) | Yes |
| English Language Course C1-1 (ENG) | Yes |
| English Language Course C1-2 (ENG) | Yes |
| Introduction to Modern Thought I (ENG) | Yes |
| Introduction to Modern Thought II (ENG) | Yes |
| Applied Hydraulics (Including Lab) (ENG) | Yes |
| Applied Mechanics (Statics) (ENG) | Yes |
| Applied Mechanics II (Dynamics) (ENG) | Yes |
| Basics of Physics II (ENG) | Yes |
| Biology for Engineers (ENG) | Yes |
| Civil Engineering Computer Applications (GIS) (ENG) | Yes |
| Civil Engineering and Society (ENG) | No |
| Computer Graphics for the Built Environment (ENG) | Yes |
| Construction and Culture (ENG) | Yes |
| Design of Steel Structures (ENG) | No |
| Ecology - Ecosystem (ENG) | Yes |
| Economic Thinking (ENG) | Yes |
| Entrepreneurship (ENG) | Yes |
| Environmental Engineering (ENG) | Yes |
| Fluid Mechanics (ENG) | Yes |
| Geotechnical Engineering (Including Lab) (ENG) | Yes |
| Highway Engineering (ENG) | No |
| Introduction to Artificial Intelligence (ENG) | No |
| Introduction to Civil Engineering (ENG) | Yes |
| Introduction to Engineering Materials (ENG) | Yes |
| Introduction to General Chemistry (ENG) | Yes |
| Introduction to Solid Mechanics (Including Lab) (ENG) | Yes |
| Introduction to Transportation Engineering (ENG) | Yes |
| Numerical Analysis (ENG) | Yes |
| Physics I Including Lab (ENG) | Yes |
| Principles of Engineering Economy (ENG) | Yes |
| Probability and Statistics (ENG) | Yes |
| Project Management for Engineers (ENG) | No |
| Reinforced Concrete Design (ENG) | Yes |
| Senior Design Project Conception (ENG) | No |
| Soil Mechanics and Foundations (ENG) | Yes |
| Structural Analysis I (ENG) | Yes |
| Structural Analysis II (ENG) | Yes |
| Surveying for Civil Engineering and Construction (ENG) | Yes |
| Water Treatment Engineering (Incl. Wastewater) (ENG) | No |
| Basics of Physics I (Including Lab) (ENG) | Yes |
| Computational and Statistical Methods (ENG) | Yes |
| Introduction to Linear Algebra (ENG) | Yes |
| Principles of Numerical Methods (ENG) | Yes |
| Introduction to Programming (ENG) | Yes |

---

## Equivalency Algorithm

The equivalency algorithm follows a **rule-based keyword matching** approach with three priority tiers:

### Tier 1 — Exact or Near-Exact Name Match

If the course name in the Civil Engineering program is identical (or nearly identical, ignoring minor wording differences like "(ENG)" or "(Including Lab)") to a course name in the target program, the match is made directly.

**Examples:**
- `Calculus I (ENG)` → `Calculus I`
- `Basics of Physics II (ENG)` → `Basics of Physics II`
- `Introduction to Linear Algebra (ENG)` → `Introduction to Linear Algebra`

### Tier 2 — Subject Domain Match

If names differ but the courses cover the same subject domain (mathematics, physics, programming, statistics), they are considered equivalent. This is determined by matching key terms in course titles.

**Rules applied:**
- `Probability and Statistics` ↔ `Computational and Statistical Methods` (both cover statistical analysis)
- `Numerical Analysis` ↔ `Principles of Numerical Methods` (same mathematical topic)
- `Physics I Including Lab` ↔ `Basics of Physics I (Including Lab)` (same content, different naming)
- `Introduction to Programming` ↔ `Introduction to Programming` (CS50 equivalent)
- `Entrepreneurship` ↔ `Basics of Entrepreneurship` (same topic)

### Tier 3 — No Equivalent (N/A)

If a Civil Engineering course has no subject counterpart in the target program — typically highly domain-specific courses like Reinforced Concrete Design, Geotechnical Engineering, or Structural Analysis — the equivalency is marked **N/A**.

**Examples of N/A:**
- `Reinforced Concrete Design (ENG)` → N/A (no structural design course in CS/EE programs)
- `Geotechnical Engineering (Including Lab) (ENG)` → N/A
- `Surveying for Civil Engineering and Construction (ENG)` → N/A

### Algorithm Summary Table

| Match Type | Condition | Result |
|------------|-----------|--------|
| Exact name match | Title words overlap ≥ 80% | Direct equivalency |
| Domain match | Same subject keyword (calculus, physics, programming, statistics) | Equivalency with note |
| Partial match | Related topics (e.g., mechanics, fluids) | Equivalency where target program has the course |
| No match | Highly domain-specific civil engineering content | N/A |

---

## Target Programs and Their Courses

### Computer Engineering (International)

Key courses: Calculus I–III, Physics I–II, Introduction to Programming, Computer Organization, Algorithms and Data Structures, Circuit Analysis, Embedded Systems, Operating Systems, Computer Networks, Digital Circuits, IT Project Management, Introduction to Cybersecurity, Senior Design Project.

### Computer Science

Key courses: Calculus I–III, Physics I–II, Introduction to Programming, Mathematical Foundation of Computing, Algorithms and Data Structures, Computer Networks, Operating Systems, Databases, Machine Learning, Web Programming, Senior Design Project.

### Electrical and Electronic Engineering

Key courses: Calculus I–III, Physics I–II, Introduction to Programming, Circuit Analysis I–II, Signals and Systems, Digital Circuits, Embedded Systems, Applied Mechanics (Statics), Fluid Mechanics, Senior Design Project.

---

## Future Improvements: Automatic Syllabus Comparison

The current application uses a manually defined rule-based mapping. The most significant improvement would be to replace this with an **AI-powered automatic syllabus comparison system**. Below is a detailed description of such a system.

### Concept

Instead of a human deciding which courses are equivalent, the system would automatically load the syllabi (course descriptions, learning objectives, topics covered, textbooks) for both programs and use AI to compare them — producing an equivalency table with confidence scores.

### Algorithm Description

#### Step 1 — Data Collection

The system would scrape or load syllabi from the university's course catalog:

```
fetch("https://bte.iliauni.edu.ge/...syllabus/MATH150.pdf")
  → extract: title, learning outcomes, weekly topics, textbooks, prerequisites
```

Each syllabus would be parsed into a structured JSON object:

```json
{
  "code": "MATH150",
  "title": "Calculus I",
  "outcomes": ["Understand limits", "Differentiate functions", ...],
  "topics": ["Limits", "Derivatives", "Integrals", ...],
  "textbooks": ["Stewart Calculus, 8th edition"]
}
```

#### Step 2 — Text Embedding

Each syllabus would be converted into a **semantic vector** (numerical representation of meaning) using a language model such as OpenAI's text-embedding-3 or a local model:

```
embed("Calculus I: limits, derivatives, integrals, continuity...")
  → [0.82, 0.14, 0.67, ...] (1536-dimensional vector)
```

Courses with similar content would have vectors that are close together in this high-dimensional space, even if their names are completely different.

#### Step 3 — Cosine Similarity Matching

For each course in Program A, the system computes the **cosine similarity** between its vector and every course vector in Program B:

```
similarity(Civil_Calculus_I, CompEng_Calculus_I) = 0.97  ✓ strong match
similarity(Civil_Calculus_I, CompEng_Circuit_Analysis) = 0.21  ✗ no match
similarity(Civil_Fluid_Mechanics, CompEng_Embedded_Systems) = 0.18  ✗ no match
```

A threshold (e.g., 0.75) is used to decide whether a match is strong enough to be called an equivalency. Matches above the threshold are presented as equivalencies; those below are marked N/A.

#### Step 4 — AI Reasoning Layer

For borderline cases (similarity 0.60–0.75), an AI language model (such as Claude or GPT-4) is asked to reason about whether the courses cover overlapping content:

> *"Course A covers: numerical methods for ODEs, finite difference methods, error analysis. Course B covers: computational methods in engineering, numerical integration, iterative solvers. Are these equivalent?"*

The AI produces a yes/no answer with a short justification, which is displayed to the user as a tooltip.

#### Step 5 — Output

The system produces the equivalency table with three columns:

| Your Course | Equivalent Course | Confidence |
|-------------|------------------|------------|
| Calculus I  | Calculus I       | 97%        |
| Fluid Mechanics | N/A         | —          |
| Probability and Statistics | Computational and Statistical Methods | 81% |

### Why This Matters

Manual equivalency decisions are time-consuming, inconsistent across advisors, and often unfair to students. An AI-based system would:

- **Scale** to any two programs at any university
- **Be consistent** — the same algorithm produces the same result every time
- **Be explainable** — the AI can justify each match
- **Be updatable** — when syllabi change, the system re-runs automatically
- **Handle cross-language programs** — embedding models are multilingual

This kind of system already exists in research form and is beginning to appear in commercial transfer credit evaluation tools. Implementing it at Ilia State University would significantly reduce administrative burden and improve the student transfer experience.
