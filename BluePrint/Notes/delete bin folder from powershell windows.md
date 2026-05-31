---
tags:
  - all
  - notes
poster: note (6).png
---

![[note (6).png|center|200]]

<center>
  <h1>
    delete bin folder from powershell windows
  </h1>
</center>
<hr>

```powershell
Remove-Item -Path 'C:\$Recycle.Bin' -Recurse -Force
```