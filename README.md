# OIL Across Domains - Visual Version

This experiment studies how participants learn reward contingencies based on **visual features** (colored circle/icons) in a reinforcement learning paradigm.

## Experiment Overview

In this version, participants learn which **colored circle** are most rewarding, regardless of where those circles appear spatially.

### Learning Target
- **Focus**: Visual features (colored circle/icons)
- **Instruction**: "Learn which colors are rewarding"
- **Strategy**: Choose based on circle appearance, ignore positions

## Experimental Design

### Stimulus Set
- **4 colored circles**: Blue, Red, Green, Purple
- **4 positions**: Left, Middle-left, Middle-right, Right
- **2 circles per trial**: Randomly selected and positioned

### Response Mapping
- **S key**: Left position
- **F key**: Middle-left position  
- **H key**: Middle-right position
- **K key**: Right position

### Trial Structure
1. **Fixation** (1000ms): Empty circle positions
2. **State cue** (1000ms): "Eye" icon indicating visual-based learning
3. **Stimulus** (6000ms): 2 circles in random positions
4. **Choice**: Participant selects one circle
5. **Feedback** (750ms): Shows selected circle
6. **Reward** (1000ms): Coin or no coin
7. **Inter-trial interval**: Brief pause

## Technical Details

### Circle Positioning
Circles are positioned using CSS custom properties:
```javascript
root.style.setProperty('--left_location', window.screen.width / 2 - 540 + "px");
root.style.setProperty('--right_location', window.screen.width / 2 - 540 + "px");
root.style.setProperty('--middle_left_location', window.screen.width / 2 - 250 + "px");
root.style.setProperty('--middle_right_location', window.screen.width / 2 - 250 + "px");
root.style.setProperty('--top_location', window.screen.height / 2 - 100 + "px");
```

### Reward Structure
- Uses `icon_to_fb_row` variable mapping
- Each color/icon has its own reward probability
- Probabilities change slowly over time
- Participants must track which colors are currently most rewarding

### Color Mapping
```javascript
const colorNames = ['blue', 'red', 'green', 'purple'];
```

## File Structure

```
oil_across_domains_visual/
├── index.html              # Main experiment file
├── css/
│   ├── jspsych.css         # jsPsych default styles
│   └── my_exp.css          # Custom experiment styles
├── images/
│   ├── practice/           # Practice trial circles (pink, black, brown, orange)
│   ├── test/               # Experimental circles (blue, red, green, purple)
│   ├── instructions/       # Instruction images
│   ├── color_blindness/    # Color blindness test images
│   └── examples/           # Example images for instructions
└── jspsych/               # jsPsych library files
```

## Running the Experiment

### Local Development
1. Open `index.html` in a web browser
2. Ensure browser is in fullscreen mode (F11)
3. Set browser zoom to 100%
4. Verify keyboard is in English layout

### Online Deployment
1. Upload entire folder to web server
2. Ensure all image files are accessible
3. Test on target platform (Prolific, Pavlovia, etc.)

## Data Collection

The experiment records:
- **Response times**: Time to make each choice
- **Choices**: Which colored circle was selected
- **Rewards**: Whether choice was rewarded
- **Trial information**: Block, trial number, phase
- **Participant ID**: For external platform linking

## Key Variables

### JavaScript Variables
- `icon_to_fb_row`: Maps colors/icons to reward matrix rows
- `key_to_index`: Maps keyboard keys to position indices
- `icon_locs`: Tracks which circles are in which positions
- `locs`: Current trial's circle positions

### CSS Classes
- `.location_left`: Left position styling
- `.location_middle_left`: Middle-left position styling
- `.location_middle_right`: Middle-right position styling
- `.location_right`: Right position styling

## Customization

### Modifying Colors
Edit the `colorNames` array in `index.html`:
```javascript
const colorNames = ['blue', 'red', 'green', 'purple'];
```

### Adjusting Positions
Modify CSS custom properties in the JavaScript initialization:
```javascript
root.style.setProperty('--left_location', window.screen.width / 2 - 540 + "px");
// Adjust the pixel values to change positioning
```

### Changing Reward Structure
Modify the `FB_matrix` arrays to adjust reward contingencies for each color/icon.

## Browser Requirements

- **Fullscreen mode**: Required for proper display
- **JavaScript enabled**: Required for functionality
- **100% zoom**: Recommended for consistency
- **English keyboard**: Required for proper key mapping

## Troubleshooting

### Common Issues
1. **Circles not appearing**: Check image file paths
2. **Positioning problems**: Ensure fullscreen and 100% zoom
3. **Keyboard not responding**: Verify English keyboard layout
4. **Loading errors**: Check browser console for JavaScript errors

### Color Blindness Screening
The experiment includes color blindness tests. Participants who fail are excluded from the study.

## Experimental Logic

### Learning Task
Participants must learn that:
- **Colors matter**: The same color can be rewarding regardless of position
- **Positions don't matter**: The same position can be rewarding or not depending on circle color
- **Rewards change**: Which colors are rewarding changes over time

### Optimal Strategy
- Track reward history for each color/icon
- Choose colors that have been recently rewarding
- Ignore circle positions when making decisions

## Key Differences from Spatial Version

### Visual vs Spatial Learning
- **Visual**: Learn which colors are rewarding
- **Spatial**: Learn which positions are rewarding

### Color Set
- **Visual**: Blue, Red, Green, Purple
- **Spatial**: Blue, Red, Green, Yellow

### Variable Mapping
- **Visual**: `icon_to_fb_row`
- **Spatial**: `location_to_fb_row`

### Experimental Instructions
- **Visual**: "Learn which colors are rewarding"
- **Spatial**: "Learn which positions are rewarding"
