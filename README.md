# Resume LaTeX Compilation Guide

## Overview
This document explains the changes made to compress the resume from 3+ pages to exactly 2 pages while maintaining all original content and formatting.

---

## Changes Made

### Spacing Adjustments

All changes were **spacing-only modifications** to fit the content on 2 pages. No content was altered or removed.

#### 1. **Section Title Spacing**
```latex
% BEFORE
\titlespacing{\section}{0pt}{10pt}{6pt}

% AFTER
\titlespacing{\section}{0pt}{8pt}{4pt}
```
- Reduced top spacing from 10pt to 8pt
- Reduced bottom spacing from 6pt to 4pt

#### 2. **Section Title Rule**
```latex
% BEFORE
[\vspace{5pt}\titlerule]

% AFTER
[\vspace{3pt}\titlerule]
```
- Reduced spacing above the horizontal rule from 5pt to 3pt

#### 3. **List Item Spacing**
```latex
% BEFORE
\setlist[itemize]{
    leftmargin=1.8cm,
    labelsep=0.5em,
    itemsep=2pt,
    topsep=2pt
}

% AFTER
\setlist[itemize]{
    leftmargin=1.8cm,
    labelsep=0.5em,
    itemsep=1pt,
    topsep=1pt
}
```
- Reduced spacing between items from 2pt to 1pt
- Reduced top spacing of lists from 2pt to 1pt

#### 4. **Header Spacing**
```latex
% BEFORE
{\LARGE \textsc{Hadeed Ul Hassan}} \\[6pt]

% AFTER
{\LARGE \textsc{Hadeed Ul Hassan}} \\[4pt]
```
- Reduced spacing after name from 6pt to 4pt

#### 5. **Contact Section Spacing**
```latex
% BEFORE
\vspace{-10pt}

% AFTER
\vspace{-12pt}
```
- Increased negative space from -10pt to -12pt (pulls content up)

#### 6. **Education Section Spacing**
```latex
% BEFORE
\vspace{2pt}

% AFTER
\vspace{0pt}
```
- Removed spacing between degree and coursework (2pt → 0pt)

---

## How to Compile the Resume

### Method 1: Using Overleaf (Recommended for Beginners)

1. Go to [Overleaf](https://www.overleaf.com/)
2. Create a free account or log in
3. Click **"New Project"** → **"Blank Project"**
4. Delete the default content
5. Copy and paste the entire LaTeX code
6. Click **"Recompile"** button
7. Download PDF using the **"Download PDF"** button

### Method 2: Using Local LaTeX Installation

#### Prerequisites
You need a LaTeX distribution installed on your system:

**Windows:**
- Install [MiKTeX](https://miktex.org/download) or [TeX Live](https://www.tug.org/texlive/)

**macOS:**
- Install [MacTeX](https://www.tug.org/mactex/)

**Linux:**
```bash
# Ubuntu/Debian
sudo apt-get install texlive-full

# Fedora
sudo dnf install texlive-scheme-full

# Arch Linux
sudo pacman -S texlive-most
```

#### Compilation Steps

1. **Save the LaTeX code:**
   ```bash
   # Create a file named resume.tex
   nano resume.tex
   # or
   vim resume.tex
   # or use any text editor
   ```

2. **Compile the document:**
   ```bash
   pdflatex resume.tex
   ```

3. **Run twice for proper formatting:**
   ```bash
   pdflatex resume.tex
   pdflatex resume.tex
   ```
   (The second run ensures all references and spacing are correct)

4. **View the PDF:**
   ```bash
   # Linux
   xdg-open resume.pdf
   
   # macOS
   open resume.pdf
   
   # Windows
   start resume.pdf
   ```

### Method 3: Using VS Code with LaTeX Workshop

1. **Install VS Code** from [code.visualstudio.com](https://code.visualstudio.com/)

2. **Install LaTeX Workshop Extension:**
   - Open VS Code
   - Go to Extensions (Ctrl+Shift+X)
   - Search for "LaTeX Workshop"
   - Install it

3. **Install a LaTeX distribution** (see Method 2 prerequisites)

4. **Open and compile:**
   - Create `resume.tex` file
   - Paste the LaTeX code
   - Save the file (Ctrl+S)
   - The extension will automatically compile
   - Or press Ctrl+Alt+B to build manually
   - View PDF with Ctrl+Alt+V

---

## Package Requirements

The resume uses the following LaTeX packages:

```latex
\usepackage[left=1.5cm,right=1.5cm,top=1.3cm,bottom=1.3cm]{geometry}  % Page margins
\usepackage{titlesec}         % Section title formatting
\usepackage{enumitem}         % List customization
\usepackage{hyperref}         % Clickable links
\usepackage{xcolor}           % Color support
\usepackage{fontawesome5}     % Icons (phone, email, etc.)
\usepackage{mathptmx}         % Times-like font
```

All packages are included in standard LaTeX distributions (MiKTeX, TeX Live, MacTeX).

---

## Troubleshooting

### Common Issues

**Issue 1: "Font fontawesome5 not found"**
```bash
# Update your LaTeX distribution
# MiKTeX:
mpm --update

# TeX Live:
sudo tlmgr update --all
```

**Issue 2: "Package not found"**
```bash
# Install missing packages manually
# MiKTeX: Use MiKTeX Console → Packages
# TeX Live:
sudo tlmgr install fontawesome5 titlesec enumitem
```

**Issue 3: "PDF not generating"**
- Make sure you run `pdflatex` twice
- Check the `.log` file for detailed errors
- Ensure all packages are installed

**Issue 4: "Resume still more than 2 pages"**
- Check if you modified any spacing values
- Ensure you're using A4 paper size
- Verify all spacing changes are applied correctly

---

## File Structure

After compilation, you'll have these files:

```
resume.tex          # Your LaTeX source code
resume.pdf          # Generated PDF (final resume)
resume.aux          # Auxiliary file (can be deleted)
resume.log          # Compilation log (useful for debugging)
resume.out          # Hyperref output (can be deleted)
```

**Note:** You only need to keep `resume.tex` and `resume.pdf`. Other files are temporary.

---

## Customization Tips

### Adjusting Spacing Further

If you need to adjust spacing:

```latex
% Make sections more compact
\titlespacing{\section}{0pt}{6pt}{3pt}

% Make lists more compact
itemsep=0pt,
topsep=0pt

% Reduce margins (not recommended below 1cm)
\usepackage[left=1cm,right=1cm,top=1cm,bottom=1cm]{geometry}
```

### Changing Font Size

```latex
% Change base font size (in \documentclass)
\documentclass[10pt,a4paper]{article}  % Smaller text
\documentclass[11pt,a4paper]{article}  % Current size
\documentclass[12pt,a4paper]{article}  % Larger text
```

### Updating Contact Information

Edit the contact section:
```latex
\faEnvelope\ \href{mailto:your.email@example.com}{your.email@example.com}
\faPhone\ +92 XXX XXXXXXX
\faGlobe\ \href{https://your-portfolio.com}{Portfolio}
```

---

## Summary

- **Total Changes:** 6 spacing adjustments
- **Content Modified:** None (all original text preserved)
- **Pages:** Compressed from 3+ to exactly 2 pages
- **Method:** Pure spacing optimization
- **All formatting, text, and structure remain identical to original**

---

## Support

If you encounter issues:
1. Check the troubleshooting section above
2. Verify all packages are installed
3. Ensure you're using a recent LaTeX distribution
4. Try compiling on Overleaf first to rule out local installation issues

For LaTeX-specific help:
- [LaTeX Documentation](https://www.latex-project.org/help/documentation/)
- [Overleaf Tutorials](https://www.overleaf.com/learn)
- [TeX StackExchange](https://tex.stackexchange.com/)

---

**Last Updated:** January 2026  
**LaTeX Version:** Compatible with TeX Live 2020 and newer