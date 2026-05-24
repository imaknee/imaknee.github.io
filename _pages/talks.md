---
layout: single
title: "Seminar & Talk Registry"
permalink: /talks/
author_profile: true
---

<p>Operational map of university seminars, conference presentations, and national laboratory technical briefings across the United States and Canada.</p>

<!-- Interactive Map Container -->
<div class="map-dashboard" style="display: flex; gap: 24px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; background: #ffffff; padding: 25px; border-radius: 12px; border: 1px solid #e1e4e6; color: #24292e; box-shadow: 0 4px 12px rgba(0,0,0,0.03);">
  
  <!-- Left Side: Complete Custom High-Fidelity Regional SVG Map -->
  <div style="flex: 1.8; min-width: 500px;">
    <svg id="north-america-map" viewBox="0 0 1000 650" style="width: 100%; height: auto; background: #f6f8fa; border-radius: 8px; border: 1px solid #eaecef;">
      <style>
        .state { fill: #e1e4e6; stroke: #ffffff; stroke-width: 1.2; cursor: pointer; transition: all 0.2s ease-in-out; }
        .state:hover { fill: #4a90e2 !important; filter: drop-shadow(0px 2px 4px rgba(0,0,0,0.15)); }
        .active-state { fill: #2c3e50; }
        .home-state { fill: #1a5276; } /* Highlighted base hubs */
      </style>

      <!-- CANADA -->
      <!-- Ontario -->
      <path id="CA-ON" class="state active-state" d="M560,180 L660,200 L680,240 L695,255 L685,275 L650,290 L610,295 L590,280 L580,250 L540,240 L530,210 Z" data-name="Ontario" data-talk="University of Waterloo (Scheduled Technical Briefing: June 2026)" />
      
      <!-- WEST COAST -->
      <!-- Washington -->
      <path id="US-WA" class="state active-state" d="M130,250 L220,245 L225,290 L185,295 L165,285 L138,280 Z" data-name="Washington" data-talk="Presentation details pending." />
      <!-- Oregon -->
      <path id="US-OR" class="state active-state" d="M130,280 L165,285 L185,295 L225,290 L230,350 L140,355 Z" data-name="Oregon" data-talk="Presentation details pending." />
      <!-- California -->
      <path id="US-CA" class="state active-state" d="M140,355 L230,350 L195,470 L245,530 L220,540 L150,470 Z" data-name="California" data-talk="Presentation details pending." />

      <!-- MOUNTAIN / SOUTHWEST / SOUTH -->
      <!-- Colorado -->
      <path id="US-CO" class="state active-state" d="M275,360 L345,360 L345,420 L275,415 Z" data-name="Colorado" data-talk="Presentation details pending." />
      <!-- New Mexico -->
      <path id="US-NM" class="state home-state" d="M340,430 L410,430 L410,510 L335,505 Z" data-name="New Mexico" data-talk="Sandia National Laboratories / Neural Exploration & Research Lab (Algorithmic Hardware Solvers)" />
      <!-- Texas -->
      <path id="US-TX" class="state home-state" d="M410,430 L450,432 L450,480 L520,485 L530,515 L510,545 L485,575 L455,595 L445,565 L415,530 L400,515 L410,510 Z" data-name="Texas" data-talk="University of Texas at Austin (Graph Theoretical Boundary Mapping)" />

      <!-- RUST BELT / MIDWEST -->
      <!-- Illinois -->
      <path id="US-IL" class="state active-state" d="M515,290 L555,285 L560,360 L530,380 L510,340 Z" data-name="Illinois" data-talk="Presentation details pending." />
      <!-- Indiana -->
      <path id="US-IN" class="state active-state" d="M555,285 L590,280 L600,350 L560,360 Z" data-name="Indiana" data-talk="Presentation details pending." />

      <!-- APPALACHIA / MID-ATLANTIC -->
      <!-- Tennessee -->
      <path id="US-TN" class="state active-state" d="M530,380 L645,365 L635,395 L520,410 Z" data-name="Tennessee" data-talk="Presentation details pending." />
      <!-- Georgia -->
      <path id="US-GA" class="state active-state" d="M595,415 L650,410 L660,480 L615,485 Z" data-name="Georgia" data-talk="Presentation details pending." />
      <!-- Virginia -->
      <path id="US-VA" class="state active-state" d="M605,345 L690,320 L710,355 L645,365 Z" data-name="Virginia" data-talk="Presentation details pending." />
      <!-- Maryland -->
      <path id="US-MD" class="state active-state" d="M690,320 L715,315 L720,330 L705,335 Z" data-name="Maryland" data-talk="Presentation details pending." />

      <!-- NORTHEAST -->
      <!-- New York -->
      <path id="US-NY" class="state active-state" d="M670,230 L720,220 L745,275 L710,285 Z" data-name="New York" data-talk="Presentation details pending." />
      <!-- Massachusetts -->
      <path id="US-MA" class="state active-state" d="M745,250 L780,245 L785,260 L748,265 Z" data-name="Massachusetts" data-talk="Presentation details pending." />
      <!-- Rhode Island -->
      <path id="US-RI" class="state active-state" d="M780,260 L795,260 L792,270 L778,270 Z" data-name="Rhode Island" data-talk="Presentation details pending." />

      <!-- BACKGROUND REGIONAL BLOCKS (Unvisited areas providing geographic map context) -->
      <!-- Rest of the West / Great Basin -->
      <path class="state" d="M220,245 L275,360 L275,415 L335,505 L245,530 L195,470 L230,350 Z" data-name="Mountain West Region" data-talk="No active presentations registered." />
      <!-- Northern Plains / Dakotas -->
      <path class="state" d="M220,245 L530,210 L515,290 L345,290 L275,360 Z" data-name="Northern Plains Region" data-talk="No active presentations registered." />
      <!-- Southern Plains / Ozarks -->
      <path class="state" d="M345,360 L515,290 L510,340 L530,380 L520,410 L450,432 L345,420 Z" data-name="Mid-South Region" data-talk="No active presentations registered." />
      <!-- Deep South Coast -->
      <path class="state" d="M520,410 L635,395 L595,415 L615,485 L530,515 L520,485 Z" data-name="Gulf Coast Region" data-talk="No active presentations registered." />
      <!-- Florida -->
      <path class="state" d="M615,485 L660,480 L690,560 L660,560 Z" data-name="Florida" data-talk="No active presentations registered." />
      <!-- Carolinas & Ohio Valley -->
      <path class="state" d="M590,280 L670,230 L710,285 L690,320 L605,345 L600,350 Z" data-name="Ohio Valley & Carolinas" data-talk="No active presentations registered." />
      <!-- Northern New England / Canada East -->
      <path class="state" d="M660,200 L820,180 L780,245 L745,250 L720,220 Z" data-name="Northeast Coast / Eastern Canada" data-talk="No active presentations registered." />
      <!-- Northwest Territories / Western Canada -->
      <path class="state" d="M130,250 L530,210 L560,180 L150,100 Z" data-name="Western Canada & Territories" data-talk="No active presentations registered." />
    </svg>
  </div>

  <!-- Right Side: Unified Dynamic Information Sidebar Menu -->
  <div style="flex: 1; background: #f8f9fa; padding: 22px; border-radius: 8px; border: 1px solid #e1e4e6; display: flex; flex-direction: column; justify-content: space-between; min-width: 260px;">
    <div>
      <div style="font-size: 11px; text-transform: uppercase; letter-spacing: 0.07em; color: #586069; margin-bottom: 8px; font-weight: 600;">Seminar Logs</div>
      <h3 id="region-title" style="margin: 0 0 12px 0; font-size: 22px; font-weight: 600; color: #0366d6; line-height: 1.2;">Hover Over a Highlighted State</h3>
      <p id="talk-details" style="font-size: 14px; line-height: 1.5; color: #444d56; margin: 0; font-style: italic;">
        Select or hover over any dark-shaded state or province on the map layout to display specific research lectures, speaking timelines, and institution briefs.
      </p>
    </div>
    
    <div style="border-top: 1px solid #eaecef; padding-top: 15px; margin-top: 15px; font-size: 12px; line-height: 1.6; color: #586069;">
      <div style="margin-bottom: 4px;">
        <span style="display: inline-block; width: 10px; height: 10px; background-color: #1a5276; border-radius: 2px; margin-right: 6px;"></span>
        <strong>Primary Hubs:</strong> NM, TX
      </div>
      <div>
        <span style="display: inline-block; width: 10px; height: 10px; background-color: #2c3e50; border-radius: 2px; margin-right: 6px;"></span>
        <strong>Active Seminar History:</strong> ON, WA, OR, CA, CO, IL, IN, TN, GA, VA, MD, NY, MA, RI
      </div>
    </div>
  </div>
</div>

<!-- Simple Vanilla Script for State Selection Dynamics -->
<script>
  document.querySelectorAll('.state').forEach(item => {
    item.addEventListener('mouseenter', function() {
      const name = this.getAttribute('data-name');
      const talk = this.getAttribute('data-talk');
      
      document.getElementById('region-title').innerText = name;
      document.getElementById('talk-details').innerText = talk;
      document.getElementById('talk-details').style.fontStyle = (talk.includes("pending") || talk.includes("No active")) ? "italic" : "normal";
    });
    
    item.addEventListener('mouseleave', function() {
      document.getElementById('region-title').innerText = "Hover Over a Highlighted State";
      document.getElementById('talk-details').innerText = "Select or hover over any dark-shaded state or province on the map layout to display specific research lectures, speaking timelines, and institution briefs.";
      document.getElementById('talk-details').style.fontStyle = "italic";
    });
  });
</script>
