# Use of Guardrails
## ⚠️ The Core Problem
ChatGPT admits that "I have memory, but I don't always prioritize it over general best practices, even when I should"
### Why?
Training biases the AI toward common patterns used in training on what most developers want to do:

-  Assume Python is global
-  Assume pip install is fine
-  Use embeddable Python as a portability shortcut

This can lead the AI assistant to offering guidance that is “technically correct” in 80% of cases — but directly contradicts specific needs in some projects.
## Work Around
The usefulness of a guardrail is determined by whether the system follows it.
The usefulness of a GUARDRAILS.md file is determined by whether ChatGPT has read and will obey it.

Create a GUARDRAILS.md file for any VS Code project that wants alternate behavior. ChatGP will not honor the rules in the just because it is in the project.  However, storing it in the project:
1. Allows differnt projects with differnt needs to configure for those needs.
2. It is simple to insert the document into ChatGPT from this file placement becaue a VS Code sessioj is usually open when conversing with the AI assistent.  
## Example
The OWB (Ontology WorkBench) project will become a deliverable selfcontained project.
1. Python version delivered with the product to reduce technical load on OWB non-technical users.
    1. This mean replacing several common python practices
        1. No use of a standad PATH environment variable to find Python.
        2. Tools installed with Python (e.g. pip) need an alternent path.
        3. The typical "embedded" Python pratice is a reduced funtionaliaty version (e.g. no pip.exe)
2. OWB project can be developed on an alternate machine or offline with no setup hassle.
## Understanding Guardrails
This workaround come with several quwerks.
### Context ≠ Enforcement
ChatGPT states "I know your preferences (venv, local installs, zero pollution), but unless I reconstruct and elevate them at the start of every decision, my guidance may still default to “quickest path” or “common case.”"

We write a single Markdown snippet or checklist that ChatGPT will treat as non-negotiable execution policy for all environment-related tasks. 

This is an example GUARDRAIL.md file
``` markdown
# OWB-Site Development Guardrails

These constraints apply specifically to the `owb-site` project and are intended to ensure environment isolation, reproducibility, and system hygiene.

1. **Local Python Only**  
   Python must be installed under the `owb-site` project folder (e.g., `owb-site/python/`). Do not rely on global or system-wide Python installations.

2. **Virtual Environment Required**  
   A virtual environment must be created using the local Python install and must reside within `owb-site/.venv`.

3. **Isolated Package Installation**  
   All Python packages (MkDocs, plugins, etc.) must be installed inside the `.venv`. No global `pip install` commands.

4. **No Global PATH Modification**  
   No changes may be made to the system `PATH`. Project tools should be invoked through `.venv\Scripts\` or wrapper scripts only.

5. **No Embeddable Python (Unless Fully Capable)**  
   The embeddable Python distribution must not be used unless it supports both `venv` and `pip` (not currently true for the 'standard embedded' verion. Use the full Python install).

6. **Declarative Dependencies**  
   All required packages must be listed in `requirements.txt` and installable via `pip install -r requirements.txt` within the local venv.

7. **Offline Build Guarantee**  
   The MkDocs site must be able to build and serve locally without needing internet access after the initial setup is complete.
```

### Placement
The GUARDRAIL.md file lives in the VS Code project root folder, for any project that needs no-default ChatGPT developer assistent behavior.

### Activation

Use a BAT or PS1 file to activate the features.

-  Set the Python path environment variable to the embedded location.
-  Set a path environment variable to the venv location
-  Check if venv exists. If not create it
-  Activate the venv
-  Any other work nedded. In the case of the OWB site start mkdocs server.
