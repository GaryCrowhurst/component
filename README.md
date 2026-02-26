# MV Component Explorer

Interactive motor vehicle component learning tool for Level 1 students. Learners identify, photograph, and describe vehicle system components at adjustable difficulty levels.

## Quick Start

1. Host on GitHub Pages (or open `index.html` locally)
2. Click a preset system or load your own JSON file
3. Select a difficulty level
4. Complete the missing fields, take photos, and check your answers

## URL Parameters

Load a system directly via URL:
```
https://yourusername.github.io/mv-explorer/?system=systems/transmission-system.json
```

## Creating New Systems

Copy `systems/template.json` and fill in your components. Place the file in the `systems/` folder.

### JSON Structure

```json
{
  "system": {
    "title": "System Name",
    "description": "System description",
    "level_descriptions": {
      "1": "Level 1 description",
      "2": "Level 2 description",
      "3": "Level 3 description"
    },
    "components": [...]
  }
}
```

### Component Fields

| Field | Description |
|-------|-------------|
| `id` | Unique identifier (use kebab-case, e.g. `clutch-assembly`) |
| `name` | Component name |
| `image` | URL or path to component image (leave `""` for learner to photograph) |
| `function` | What the component does |
| `operation` | How the component works |
| `hints` | Object with `name`, `function`, `operation` hint strings |
| `level_visibility` | Controls what is shown/hidden per level |

### Level Visibility

Controls which fields are **provided** (shown as read-only) vs **required** (learner must complete):

```json
"level_visibility": {
  "1": { "name": true, "image": true, "function": true, "operation": false },
  "2": { "name": true, "image": false, "function": false, "operation": false },
  "3": { "name": false, "image": false, "function": false, "operation": false }
}
```

- `true` = provided to the learner (read-only, shown in blue)
- `false` = learner must complete this field

### Partial Information Strategy

You can provide different info for different components to keep learners engaged:

- **Component A**: Provide name + image, learner writes function + operation
- **Component B**: Provide image only, learner identifies and describes everything
- **Component C**: Provide name + function, learner photographs and explains operation
- **Component D**: Provide everything (reference card at Level 1)

## Adding Preset Buttons

Edit `index.html` and add buttons in the `preset-systems` div:

```html
<button class="preset-btn" onclick="loadPreset('systems/braking-system.json')">
  🛑 Braking System
</button>
```

## Features

- **3 Difficulty Levels**: Guided → Developing → Independent
- **Photo Capture**: Camera integration for mobile devices
- **Hints System**: Toggle hints per field to scaffold learning
- **Progress Tracking**: Real-time completion percentage
- **Save/Load**: Progress saved to browser storage
- **Print Mode**: Clean printable worksheet layout
- **Export**: Download learner responses as text file
- **Mobile-First**: Fully responsive design

## Printing

Click the 🖨 Print button for a clean worksheet layout. Provided fields show with a blue background; blank fields have writing space for learners.

## GitHub Pages Deployment

1. Push this folder to a GitHub repository
2. Go to Settings → Pages → Deploy from main branch
3. Access at `https://yourusername.github.io/repo-name/`

## Licence

Created for educational use by CodeEdAI.
