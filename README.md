 Code Review Guide (Assignment 2 Focus)
To assist with grading and verification, the core architectural components for User Story 1: Interactive Tapping have been isolated below from index.html.
1. Front-End Viewport Layer (The Interactive SVG Map)
The physical boundaries of the court are mapped using native HTML5 SVG path elements. Each path uses an onclick listener to pass its unique string identifier to the state engine:


```
<g id="heatmap-zones">
    <path data-zone="Paint Low" onclick="selectZone('Paint Low')" class="court-sensor" d="M170,0 H330 V60 H170 Z" />
    <path data-zone="Paint Mid" onclick="selectZone('Paint Mid')" class="court-sensor" d="M170,60 H330 V130 H170 Z" />
    <path data-zone="Paint High" onclick="selectZone('Paint High')" class="court-sensor" d="M170,130 H330 V190 H170 Z" />
</g>
```

    2. State Management Layer (The Capture Script)
When a zone path is tapped, this function processes the input token, handles haptic feedback, manages the selection toggle logic, and triggers the UI rendering updates:

```
function selectZone(zoneId) {
    triggerHaptic(10);
    selectedZone = (selectedZone === zoneId) ? 'Overall' : zoneId;
    selectedElbowSide = 'Center';
    soloInputMakes = 0;
    updateDisplay();
}
```

