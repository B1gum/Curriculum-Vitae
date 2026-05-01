# Studie-/study diagram

This folder contains the reusable course-grid macros for `study_diagram.tex`.

## Compile

Compile from the root of the `CV/` directory:

```bash
latexmk -xelatex study_diagram.tex
```

or run XeLaTeX directly and, if necessary, convert the produced XDV file:

```bash
xelatex -interaction=nonstopmode study_diagram.tex
xdvipdfmx -o study_diagram.pdf study_diagram.xdv
```

The document expects the same local `fonts/` directory used by the rest of the CV setup.

## Language switch

`study_diagram.tex` defaults to Danish:

```tex
\AtBeginDocument{\selectlanguage{danish}}
```

Change it to English with:

```tex
\AtBeginDocument{\selectlanguage{english}}
```

The built-in labels, course names, semester labels, bachelor/master titles and bottom note use `\StudyDiagramText{Danish}{English}`, so the whole diagram follows this language setting.

## Editing the courses

Edit `study_diagram/mechanics_courses.tex` to change courses, dates, grades and bachelor/master layouts.

Course syntax:

```tex
\course[type=obligatory,status=completed,grade={12}]{5}{Kontrolteori}
```

Semester syntax:

```tex
\begin{semester}[Feb. 2026 -- Jun. 2026]{4. semester}
  ...
\end{semester}
```

Allowed course types:

- `obligatory` - muted yellow
- `elective` - muted green
- `additional` - muted purple
- `support` - CV accent blue

Allowed statuses:

- `completed` - darker fill
- `current` - striped fill
- `planned` - lighter fill

Each semester row should normally add up to 30 ECTS. Course width is proportional to ECTS.
Grades are optional; if `grade={...}` is empty, no grade is printed.
