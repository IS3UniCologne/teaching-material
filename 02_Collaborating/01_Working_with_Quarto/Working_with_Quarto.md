# Working with Quarto

Welcome to the Quarto tutorial! When you are working on team reports for your assignments, you will want your final submissions to look professional. **Quarto** is the perfect tool for this.

Think of Quarto like a sophisticated printing press for your digital workspaces (like Jupyter Notebooks). It takes your Python code, your explanations, and your charts, and magically turns them into beautiful HTML web pages, polished PDFs, or even academic journal articles.

In this tutorial, we will learn how to:
1. Install Quarto.
2. Prepare your Jupyter Notebook for Quarto.
3. Render your notebook into HTML and PDF.
4. Use templates for manuscript and journal articles.

---

## 1. What is Quarto and How to Install It?

Quarto is an open-source publishing system. It's a standalone tool that reads your code notebooks and formats them based on instructions you give it.

### Installation

1. Go to the [Quarto Download Page](https://quarto.org/docs/get-started/).
2. Download the version for your operating system (Windows, Mac, or Linux).
3. Run the installer and follow the standard instructions.

To check if Quarto was installed correctly, open your terminal (or command prompt) and type:

```bash
quarto --version
```

If it prints a version number, you are good to go!

---

## 2. Preparing Your Jupyter Notebook

For Quarto to know how to format your report (e.g., what the title is, who the author is, and whether you want a PDF or HTML), you need to add a special block of text to the very top of your notebook. This is called **YAML Front Matter**.

### Adding YAML Front Matter

Open your Jupyter Notebook, create a new cell at the absolute top, and change the cell type to **Raw** (or Markdown). Add the following structure:

```yaml
---
title: "Our Awesome Team Report"
author: "Team Alpha: Alice, Bob, and Charlie"
format:
  html:
    code-fold: true
  pdf: default
jupyter: python3
---
```

**What does this do?**
- `title` and `author`: Sets the header for your document.
- `format`: Tells Quarto which formats you care about.
  - `html: code-fold: true` creates a webpage where your code blocks are hidden behind a toggle button, keeping the report clean!
  - `pdf: default` tells it to also be ready to create a PDF.

*(Note: We have included an `example_report.ipynb` file in this folder. Open it to see this in action!)*

---

## 3. Rendering Your Report

Once your notebook is ready, it's time to let Quarto do its magic. You do this from your terminal.

1. Open your terminal.
2. Navigate to the folder where your workspace (notebook) is located.

### To generate an HTML report:
Type this command:
```bash
quarto render your_notebook.ipynb --to html
```
Quarto will process the file and create a `your_notebook.html` file right next to it. You can open this in any web browser.

### To generate a PDF report:
Type this command:
```bash
quarto render your_notebook.ipynb --to pdf
```
*(Note: Creating PDFs usually requires a TeX installation. If Quarto complains about a missing TeX engine, it will usually offer to install `TinyTeX` for you. Just follow the prompt or run `quarto install tinytex` in your terminal.)*

---

## 4. Using Academic Journal/Manuscript Templates

In our courses, you might be asked to format your report like a real scientific paper. Quarto makes this incredibly easy using **extensions** and **templates**.

Instead of manually formatting fonts and margins, you can use templates provided by major journals (like IEEE, ACM, or Elsevier).

### How to use a Journal Template

Let's say you want to format your report using the Elsevier journal style. In your terminal, inside your project folder, run:

```bash
quarto use template quarto-journals/elsevier
```

Quarto will:
1. Download the necessary toolkit and styling files for that journal.
2. Ask you if you want to create a new folder and a starter document.

Once downloaded, you can modify the YAML at the top of your notebook to use this format. It will look something like this:

```yaml
---
title: "Our Academic Report"
author: "Alice, Bob, and Charlie"
format:
  elsevier-pdf:
    keep-tex: true
    journal:
      name: "Journal of Data Science"
      formatting: preprint
---
```

When you render this using `quarto render your_notebook.ipynb`, Quarto will automatically apply all the complex formatting, double-columns, and standard fonts required by that journal!

You can find a list of available journal templates in the [Quarto Journal Formats documentation](https://quarto.org/docs/extensions/listing-journals.html).

---

## Summary
- **Quarto** transforms your code workspaces into beautiful reports.
- Add **YAML Front Matter** to the top of your `.ipynb` file.
- Use `quarto render` in the terminal to generate HTML or PDFs.
- Use `quarto use template` to quickly apply professional academic formatting.

Try rendering the `example_report.ipynb` included in this folder to see it working!
