# ChatGPT Advice About Third-Party Software 
# (PyCharm example)
## Why this matters
ChatGPT has access to an unfathomable amount of information. The trick to being a good user is to
limit searches to relevant information only. Generic instructions drift as products update. 
Share your exact **About** info so ChatGPT can anchor answers to your version.
## Example
I want to get information about use of PyCharm. The advice is close but off enough to reduce 
productivity. ChatGPT wrote 
>When UI menus move between PyCharm releases, my generic steps can end up “one version behind.” 
> That’s on me.
## Solution
### Will “About” info help?
>Yes. If you give me the exact PyCharm edition + version (e.g., Community 2025.2.1), I’ll target
> instructions to that build and cross-check against JetBrains’ current docs before I answer. 
> I can also give version-split steps when multiple recent builds differ.
### Never Too Much Information
On PyCharm upper ribbon menu select Help-->About-->Copy and Close. 
This will place the About information in the copy buffer.
In ChatGPT paste the 'About' information just retrieved.
From that point on ChatGPT SHOULD only respond to information about using the third party 
product with information relevant to the defined product release.  
## Quick procedure
1. In PyCharm, go to **Help → About → Copy and Close**.
2. Paste that block into ChatGPT.
3. Ask your question. From now on, answers should target that specific build 
(e.g., *PyCharm 2025.2.3 on Windows 11*).
## Notes
- More detail is better: edition, version, OS, and any relevant plugins.
- If menus moved between minor versions, ask for **version-split paths** (“In 2025.2.3 do X; in earlier builds do Y”).
- Keep this habit for any tool (Docker Desktop, VS Code, Git, etc.).
