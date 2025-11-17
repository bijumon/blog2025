---
title: ""
draft: true
---

you have a directory layout something like this:  

```
assets/
 ├─ levels/
 │   ├─ level1.tmx
 │   ├─ level2.tmx
 │   └─ ...
 └─ tiled/
     ├─ tileset1.tsx
     ├─ tileset2.tsx
     └─ ...
```

Your `.tmx` maps (levels) reference tilesets in `assets/tiled`.  
You want to load them in Python in a way that respects these dependencies.

Here’s a clean approach:

---

### 1. Use a TMX Parser Library  
You can use **pytmx** or **tiled** (two good Python libraries for reading TMX files).  
Let’s go with `pytmx` since it’s widely used:

```bash
pip install pytmx
```

---

### 2. Load with Correct Base Path

```python
from pathlib import Path
import pytmx

ASSETS_DIR = Path("assets")
LEVELS_DIR = ASSETS_DIR / "levels"
TILED_DIR = ASSETS_DIR / "tiled"

def load_level(name: str):
    """Load a TMX level by name (without extension)."""
    tmx_path = LEVELS_DIR / f"{name}.tmx"
    # pytmx automatically resolves relative paths inside the tmx
    tmx_data = pytmx.TiledMap(tmx_path)
    return tmx_data

# Example usage:
level = load_level("level1")
print(level.width, level.height)
```

💡 **Key point:**  
Tiled stores `<tileset source="...">` as a relative path.  
If your `.tmx` uses `../tiled/tileset.tsx`, then `pytmx` will resolve it automatically — as long as your `tmx_path` is correct.

---

### 3. Handling Custom Path Resolution (Optional)

If you moved files or want to manually control where tilesets are loaded from, you can override `pytmx`’s resource loader:

```python
import pytmx

def custom_loader(filename, *args, **kwargs):
    # Resolve filename relative to assets/tiled
    return (TILED_DIR / Path(filename).name).read_text(encoding="utf-8")

tmx_data = pytmx.TiledMap(LEVELS_DIR / "level1.tmx", load_all=True)
for ts in tmx_data.tilesets:
    print("Tileset:", ts.name)
```

But most of the time, **just keeping relative paths correct in Tiled** is enough.

---

### 4. Sanity Check: Make Sure Your TMX References Are Relative

Open `level1.tmx` and check:

```xml
<tileset firstgid="1" source="../tiled/tileset1.tsx"/>
```

This ensures `pytmx` can resolve the tileset.  
If it uses **absolute paths**, you may need to rewrite them or patch in Python.

---

Would you like me to show you **how to build a small loader that scans `assets/levels/` and loads all TMX files into a dictionary**, so you can easily access them by name? That makes things cleaner for a game.