# 🔲 Quick Quadify (Clean) - Complete Usage Guide

![image](https://github.com/Dahandla/Quick_Quadify_/blob/c621753a6bc6f808bb67b1d6576fb5a8a15f9aea/resources/Quickquadify.png
)


## 🚀 Why This Add-On is Exciting & Different

### The Problem It Solves

Traditional retopology in Blender is **painfully slow**:
- **Manual retopology** - Drawing quad topology by hand takes hours or days
- **Inconsistent topology** - Human error creates ngons, triangles, and poor edge flow
- **No automation** - Every mesh requires starting from scratch
- **Complex workflows** - Multiple tools, modifiers, and manual conforming
- **Shading issues** - Poor topology creates ugly shading artifacts

### What Makes This Different

🔥 **One-Click Quad Remeshing**
- Automatically converts any mesh to clean quad topology
- Uses Blender's powerful QuadriFlow algorithm
- No manual vertex placement needed
- Perfect for game assets, animation, and rendering

⚡ **Automatic Conforming**
- Shrinkwrap modifier automatically conforms quad mesh to original
- Preserves all surface details and shape
- Two methods: Nearest Surface Point (default) or Project (all axes)
- Adjustable offset for fine-tuning

🛠️ **Smart Shading Setup**
- **Weighted Normal** modifier (enabled by default) - smooth shading without artifacts
- **Corrective Smooth** (optional) - removes unwanted bumps and creases
- All modifiers applied automatically (or kept live for tweaking)

🔧 **Mesh Repair Built-In**
- Auto-repairs loose vertices, degenerate faces, and duplicate geometry
- Removes problematic geometry before remeshing
- Prevents QuadriFlow failures from bad mesh data

📊 **Production-Ready Results**
- Clean quad topology perfect for animation and rigging
- Preserves original mesh as hidden backup
- Can apply modifiers or keep them live
- Smooth shading ready out of the box

---

## 📦 Installation

1. **Install the add-on:**
   - `Edit` → `Preferences` → `Add-ons` → `Install...`
   - Select the `quick_quadify_clean.py` file
2. **Enable the add-on:**
   - Search for "Quick Quadify (Clean)"
   - Check the checkbox to enable
3. **Access the panel:**
   - Press `N` in the 3D Viewport (or `View` → `Sidebar`)
   - Click the **"Quadify"** tab in the sidebar

**Note:** Requires Blender 4.0+ with QuadriFlow support (included in official Blender builds).

---

## 🎬 Quick Start (2 Steps)

### Step 1: Select Your Mesh

Select the high-poly or sculpted mesh you want to convert to quads. This can be:
- A sculpted character
- A high-poly prop
- An imported mesh with messy topology
- Any mesh that needs clean quad topology

### Step 2: Click "Quadify Active Mesh"

That's it! The add-on will:
1. ✅ Auto-repair any mesh issues
2. ✅ Create a backup of your original (hidden)
3. ✅ Generate clean quad topology using QuadriFlow
4. ✅ Add Shrinkwrap to conform to original
5. ✅ Add Weighted Normal for smooth shading
6. ✅ Apply all modifiers (or keep them live)

**Result:** A new mesh named `{OriginalName}_QUAD` with perfect quad topology!

---

## 📖 Detailed Workflow

### Workflow 1: Character Retopology

**Scenario:** You have a sculpted character and need clean quad topology for animation.

1. **Select Character Mesh**
   - Your sculpted or high-poly character
   - Ensure it's the active object (orange outline)

2. **Configure Settings**
   - **Target Faces**: `15,000-30,000` for characters (good balance)
   - **Conform Method**: `Nearest Surface Point` (default)
   - **Offset**: `0.002` (default)
   - ✅ **Weighted Normal**: Enabled (smooth shading)
   - ✅ **Detach (Apply Modifiers)**: Enabled (bakes conforming)

3. **Quadify**
   - Click **"Quadify Active Mesh"**
   - Wait 10-60 seconds (depends on complexity)

4. **Result**
   - Clean quad mesh with perfect topology
   - Smooth shading applied
   - Original hidden as backup
   - Ready for UV unwrapping and rigging

### Workflow 2: Quick Game Asset Retopology

**Scenario:** You need a low-poly game-ready version of a high-poly model.

1. **Select High-Poly Mesh**
   - Your detailed model

2. **Configure for Low-Poly**
   - **Target Faces**: `5,000-10,000` (game-ready)
   - **Conform Method**: `Nearest Surface Point`
   - **Offset**: `0.001-0.002` (closer conforming)
   - ✅ **Weighted Normal**: Enabled
   - ✅ **Detach (Apply Modifiers)**: Enabled

3. **Quadify**
   - Click button, wait for processing

4. **Result**
   - Low-poly quad mesh
   - Perfect for baking normal maps
   - Ready for game engine

### Workflow 3: High-Detail Retopology

**Scenario:** You need maximum detail preservation for close-up renders.

1. **Select Source Mesh**
   - Your detailed sculpt or model

2. **Configure for High Detail**
   - **Target Faces**: `50,000-100,000` (high detail)
   - **Conform Method**: `Nearest Surface Point`
   - **Offset**: `0.002-0.005` (preserves detail)
   - ✅ **Weighted Normal**: Enabled
   - ✅ **Corrective Smooth**: Enabled (removes artifacts)
   - **CS Factor**: `0.2-0.3`
   - **CS Iter**: `5-10`

3. **Quadify**
   - Processing may take 1-5 minutes for high face counts

4. **Result**
   - High-detail quad mesh
   - Smooth shading without artifacts
   - Perfect for hero props

---

## 🎛️ Settings Explained

### Remesh & Conform

**Target Faces**
- Number of faces in the final quad mesh
- **5,000-10,000**: Low-poly game assets
- **15,000-30,000**: Mid-poly characters (default: 18,000)
- **50,000-100,000**: High-detail props
- **100,000+**: Maximum detail (slow)

**Conform Method**
- **Nearest Surface Point** (default): Best for organic shapes, characters
- **Project (All Axes)**: Better for hard-surface, mechanical objects

**Offset**
- Distance to offset quad mesh from original
- **0.001-0.002**: Tight conforming (default: 0.002)
- **0.005-0.01**: Loose conforming (for meshes with gaps)
- **0.01-0.05**: Maximum offset (for very separated meshes)

### Shading

**Weighted Normal** (Enabled by default)
- Smooths shading without artifacts
- Eliminates ugly faceting on curved surfaces
- **Keep Sharp**: Preserves sharp edges (recommended: enabled)
- **Weight**: Strength of effect (default: 50, range: 1-100)

**Corrective Smooth** (Optional)
- Removes unwanted bumps and creases
- **CS Factor**: Smoothing strength (default: 0.2, range: 0.0-1.0)
- **CS Iter**: Number of iterations (default: 5, range: 0-50)
- **Use when**: Quad mesh has small bumps or artifacts

### Detach

**Detach (Apply Modifiers)**
- **Enabled** (default): Bakes modifiers into mesh geometry
  - Conforming is permanent
  - No modifiers to manage
  - Clean, final geometry
- **Disabled**: Keeps modifiers live
  - Can adjust Shrinkwrap offset
  - Can tweak Weighted Normal settings
  - Modifiers can be removed later

**Delete Hidden Backup**
- **Enabled**: Permanently deletes original mesh backup
- **Disabled** (default): Keeps original hidden (safe)
- **Recommendation**: Keep disabled until you're sure the quad mesh is good

### Prep

**Auto-Repair Mesh** (Enabled by default)
- Automatically fixes mesh issues before remeshing:
  - Removes loose vertices
  - Removes degenerate faces
  - Merges duplicate vertices
  - Fixes face normals
- **Disable only if**: You've already manually fixed the mesh

---

## 🛠️ Tools Reference

### Quadify Active Mesh
**What it does:**
- Creates clean quad topology from any mesh
- Adds conforming and shading modifiers
- Creates backup of original
- Applies modifiers (if enabled)

**When to use:** Every time you need clean quad topology

**Processing time:** 10 seconds - 5 minutes (depends on target faces and mesh complexity)

---

## 🔧 Troubleshooting

### Problem: "QuadriFlow operator is not available"

**Cause:** Your Blender build doesn't have QuadriFlow support.

**Solution:**
- Download official Blender from blender.org
- QuadriFlow is included in official builds
- Some third-party builds may not include it

### Problem: Mesh Turns Inside-Out

**Cause:** Original mesh had flipped normals.

**Solution:**
1. Select original mesh (the backup)
2. Edit Mode → Select All → Mesh → Normals → Recalculate Outside
3. Re-run Quadify

### Problem: Too Few Faces in Result

**Cause:** Target Faces value too low.

**Solution:**
- Increase "Target Faces" value
- Start with 5,000 for testing
- Gradually increase to desired detail

### Problem: Mesh Doesn't Conform to Original

**Cause:** Shrinkwrap offset too large or method wrong.

**Solution:**
1. Disable "Detach (Apply Modifiers)" to keep modifiers live
2. Reduce "Offset" value (try 0.001)
3. Try "Project (All Axes)" method
4. Adjust Shrinkwrap modifier manually in Properties panel

### Problem: Quad Mesh Has Bumps/Artifacts

**Cause:** QuadriFlow created uneven topology.

**Solution:**
- Enable "Corrective Smooth"
- Set CS Factor to 0.2-0.3
- Set CS Iter to 5-10
- Increase iterations if needed

### Problem: Processing Takes Forever

**Cause:** Target Faces count too high or mesh too complex.

**Solution:**
- Reduce "Target Faces" (try 5,000 first)
- Disable "Auto-Repair Mesh" if already clean
- Use lower face counts for testing, increase for final

### Problem: Quad Mesh Has Holes

**Cause:** Original mesh had holes or non-manifold geometry.

**Solution:**
1. Fix original mesh first:
   - Edit Mode → Select All → Mesh → Clean Up → Fill Holes
   - Or manually fill holes
2. Re-run Quadify

### Problem: Weighted Normal Creates Artifacts

**Cause:** Weighted Normal settings too aggressive.

**Solution:**
- Reduce "WN Weight" (try 25-50)
- Disable "Keep Sharp" if edges are too soft
- Or disable Weighted Normal entirely

---

## 💡 Tips & Best Practices

✅ **Start with lower face counts** - Test with 5,000-10,000 faces first, increase if needed

✅ **Keep backup enabled** - Don't delete until you're sure the quad mesh is perfect

✅ **Use Nearest Surface Point** - Best default for most meshes

✅ **Enable Detach for final** - Apply modifiers for clean geometry

✅ **Keep Detach disabled for testing** - Allows tweaking Shrinkwrap offset

✅ **Use Corrective Smooth for artifacts** - Helps remove bumps and creases

✅ **Auto-Repair is your friend** - Leave enabled unless you've manually fixed everything

✅ **Weighted Normal is essential** - Disable only if you need hard edges

✅ **For game assets** - Use 5,000-15,000 faces, apply modifiers

✅ **For animation** - Use 15,000-30,000 faces, check edge flow

✅ **For high-detail renders** - Use 50,000+ faces, enable Corrective Smooth

---

## 🎯 Common Workflows Summary

| Workflow | Target Faces | Conform Method | Weighted Normal | Corrective Smooth | Detach |
|----------|--------------|----------------|-----------------|-------------------|--------|
| **Game Asset** | 5,000-10,000 | Nearest Surface | ✅ | ❌ | ✅ |
| **Character** | 15,000-30,000 | Nearest Surface | ✅ | ❌ | ✅ |
| **Hero Prop** | 50,000-100,000 | Nearest Surface | ✅ | ✅ | ✅ |
| **Hard Surface** | 10,000-20,000 | Project (All Axes) | ✅ | ❌ | ✅ |
| **Animation** | 15,000-25,000 | Nearest Surface | ✅ | ✅ | ✅ |

---

## 📝 Technical Notes

### QuadriFlow Algorithm

QuadriFlow is Blender's automatic quad remeshing tool. It:
- Converts any topology to clean quad topology
- Optimizes edge flow for animation
- Preserves mesh shape and volume
- Works best with manifold (closed) meshes

### Shrinkwrap Modifier

The Shrinkwrap modifier conforms the quad mesh to the original:
- **Nearest Surface Point**: Moves vertices to nearest point on source
- **Project**: Projects along axes (better for hard-surface)

### Weighted Normal Modifier

Improves shading without artifacts:
- Calculates normals based on face angles
- Smooths shading on curved surfaces
- Preserves sharp edges when enabled

### Processing Flow

1. **Mesh Repair** - Fixes loose verts, degenerate faces
2. **Transform Apply** - Applies rotation and scale
3. **Backup Creation** - Creates hidden copy of original
4. **QuadriFlow Remesh** - Generates quad topology
5. **Shrinkwrap** - Conforms to original
6. **Weighted Normal** - Applies smooth shading
7. **Corrective Smooth** - Removes artifacts (if enabled)
8. **Modifier Apply** - Bakes modifiers (if enabled)
9. **Cleanup** - Hides original, activates quad mesh

---

## 🎬 That's It!

You now have professional quad retopology in Blender with:
- ✅ One-click quad conversion
- ✅ Automatic conforming
- ✅ Smooth shading setup
- ✅ Production-ready results

**Perfect for:**
- Game asset creation
- Character retopology
- Animation-ready meshes
- Clean topology for baking

**Happy Quadifying!** 🔲✨



