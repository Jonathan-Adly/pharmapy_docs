# **Introduction**

---

This repository contains the code for the PharmaPy  Documentation. It is built using mkdocs and the mkdocs material theme. 

File Structure:

* `mkdocs.yml` - contains the list of pages, the styles, and all features used, including the search bar, the copy and paste function for codeblocks, and the color scheme

* `docs/custom.css` - contains the css styling used in the "galenai" color scheme. If changed, update the palette: scheme: attribute in mkdocs.yml

* `docs/index.md` - contains the markdown content for the Introduction page

* `docs/api.md` - contains the markdown content for the Reference API page


---

# Installation

Activate the virtual environment
```
    source .venv/bin/activate
```

After running the virtual environment, run the following commands in the terminal

```
     pip install -r requirements.txt
```

---

# Running

The documentation can be run by using the command <strong>mkdocs serve</strong> and it will run on http://localhost:8000/

---

