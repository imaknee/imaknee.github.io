---
layout: single
title: "Seminar & Talk Registry"
permalink: /talks/
author_profile: true
---

<p>Operational map of university seminars, conference presentations, and national laboratory technical briefings across the United States and Canada.</p>

<!-- Interactive Map Container -->
<div class="map-dashboard" style="display: flex; gap: 24px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; background: #ffffff; padding: 25px; border-radius: 12px; border: 1px solid #e1e4e6; color: #24292e; box-shadow: 0 4px 12px rgba(0,0,0,0.03);">
  
  <!-- Left Side: Scaled SVG Map with Recognizable Geographic Features -->
  <div style="flex: 1.6; min-width: 450px;">
    <svg id="north-america-map" viewBox="0 0 1000 650" style="width: 100%; height: auto; background: #f6f8fa; border-radius: 8px; border: 1px solid #eaecef;">
      <style>
        .state { fill: #e1e4e6; stroke: #ffffff; stroke-width: 1.2; cursor: pointer; transition: all 0.2s ease-in-out; }
        .state:hover { fill: #6cb6db !important; filter: drop-shadow(0px 2px 4px rgba(0,0,0,0.15)); }
        .active-state { fill: #226083; }
        .border-line { fill: none; stroke: #ffffff; stroke-width: 1.5; }
      </style>

      <!-- CANADA: Ontario (Curved baseline wrapping the Great Lakes) -->
      <path id="CA-ON" class="state active-state" 
            d="M560,180 L660,200 L680,240 L695,255 L685,275 L650,290 L610,295 L590,280 L580,250 L540,240 L530,210 Z" 
            data-name="Ontario" data-talk="University of Waterloo (Scheduled Technical Briefing: June 2026)" />
      
      <!-- USA: New Mexico (Distinct square with slight western offset and sharp borders) -->
      <path id="US-NM" class="state active-state" 
            d="M340,430 L410,430 L410,510 L335,505 Z" 
            data-name="New Mexico" data-talk="Sandia National Laboratories / Neural Exploration & Research Lab (Algorithmic Hardware Solvers)" />
      
      <!-- USA: Texas (Distinctive panhandle, western crook, Gulf Coast curve, and eastern boot) -->
      <path id="US-TX" class="state active-state" 
            d="M410,430 L450,432 L450,480 L520,485 L530,515 L510,545 L485,575 L455,595 L445,565 L415,530 L400,515 L410,510 Z" 
            data-name="Texas" data-talk="University of Texas at Austin (Graph Theoretical Boundary Mapping)" />

      <!-- BACKGROUND REFS: Quick structural baseline context paths for surrounding geography -->
      <!-- Western/Pacific States Block -->
      <path class="state" d="M120,250 L280,240 L340,290 L340,430 L335,505 L220,490 L130,420 Z" data-name="Pacific & West Region" data-talk="No active presentations registered." />
      <!-- Plains/Midwest Block -->
      <path class="state" d="M280,240 L530,210 L540,240 L500,380 L450,432 L410,430 L340,290 Z" data-name="Plains & Midwest Region" data-talk="No active presentations registered." />
      <!-- South/East Coast Block -->
      <path class="state" d="M500,380 L580,380 L690,320 L760,350 L720,480 L610,510 L530,515 L520,485 Z" data-name="Eastern & Southern Seaboard" data-talk="No active presentations registered." />
      <!-- Rest of Canada North/West -->
      <path class="state" d="M150,100 L560,180 L540,240 L280,240 L120,250 Z" data-name="Western Canada & Territories" data-talk="No active presentations registered." />
    </svg>
  </div>

  <!-- Right Side: Sidebar Dynamic Tooltip & Registry Panel -->
  <div style="flex: 1; background: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #e1e4e6; display: flex; flex-direction: column; justify-content: space-between;">
    <div>
      <div style="font-size: 11px; text-transform: uppercase; letter-spacing: 0.05em; color: #586069; margin-bottom: 8px; font-weight: 600;">Interactive Registry</div>
      <h3 id="region-title" style="margin: 0 0 12px 0; font-size: 20px; font-weight: 600; color: #0366d6;">Hover Over a Highlighted Region</h3>
      <p id="talk-details" style="font-size: 14px; line-height: 1.5; color: #444d56; margin: 0; font-style: italic;">
        Move your mouse cursor over an active state or province on the map to display the corresponding institutional seminar summary.
      </p>
    </div>
    
    <div style="border-top: 1px solid #eaecef; padding-top: 15px; margin-top: 15px; font-size: 13px; color: #6a737d;">
      <span style="display: inline-block; width: 10px; height: 10px; background-color: #226083; border-radius: 2px; margin-right: 6px;"></span>
      <strong>Active Locations:</strong> Ontario, New Mexico, Texas.
    </div>
  </div>
</div>

<!-- Simple Vanilla Script for Seamless State Swapping -->
<script>
  document.querySelectorAll('.state').forEach(item => {
    item.addEventListener('mouseenter', function() {
      const name = this.getAttribute('data-name');
      const talk = this.getAttribute('data-talk');
      
      document.getElementById('region-title').innerText = name;
      document.getElementById('talk-details').innerText = talk;
      // Remove italic layout style when real text populates
      document.getElementById('talk-details').style.fontStyle = (talk.includes("No active")) ? "italic" : "normal";
    });
    
    item.addEventListener('mouseleave', function() {
      document.getElementById('region-title').innerText = "Hover Over a Highlighted Region";
      document.getElementById('talk-details').innerText = "Move your mouse cursor over an active state or province on the map to display the corresponding institutional seminar summary.";
      document.getElementById('talk-details').style.fontStyle = "italic";
    });
  });
</script>
