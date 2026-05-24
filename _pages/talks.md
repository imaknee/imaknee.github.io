---
layout: single
title: "Seminar & Talk Registry"
permalink: /talks/
author_profile: true
---

<p>Operational map of university seminars, conference presentations, and national laboratory technical briefings across the United States and Canada.</p>

<!-- Interactive Map Container -->
<div class="map-dashboard" style="display: flex; gap: 20px; font-family: sans-serif; background: #f9f9f9; padding: 20px; border-radius: 8px; border: 1px solid #e0e0e0; color: #333;">
  
  <!-- Left Side: Clean Inline SVG Map (Targeted Regions Highlighted) -->
  <div style="flex: 1.5; min-width: 300px;">
    <svg id="north-america-map" viewBox="0 0 1000 600" style="width: 100%; height: auto; background: #eef5f9; border-radius: 6px;">
      <style>
        .state { fill: #d1dbe0; stroke: #fff; stroke-width: 1.5; cursor: pointer; transition: fill 0.2s ease; }
        .state:hover { fill: #7faec5 !important; }
        .active-state { fill: #347a9f; }
      </style>

      <!-- Canada Subsections -->
      <path id="CA-ON" class="state active-state" d="M350,220 L450,220 L430,280 L320,260 Z" data-name="Ontario" data-talk="University of Waterloo (Upcoming June 2026)" />
      
      <!-- US Subsections (Simplified Vector Shapes for Pristine Rendering) -->
      <path id="US-NM" class="state active-state" d="M280,380 L360,380 L360,470 L280,460 Z" data-name="New Mexico" data-talk="Sandia National Laboratories (Computational Frameworks)" />
      <path id="US-TX" class="state active-state" d="M360,470 L480,480 L440,580 L330,520 Z" data-name="Texas" data-talk="UT Austin (Complexity Boundaries Analysis)" />
      
      <!-- Placeholder Background Rest of North America Map Elements -->
      <path id="US-REST" class="state" d="M100,200 L300,180 L320,380 L100,350 Z" data-name="Western Regions" data-talk="No recent presentations registered." />
      <path id="US-EAST" class="state" d="M480,300 L650,280 L600,450 L480,430 Z" data-name="Eastern Seaboard" data-talk="No recent presentations registered." />
    </svg>
  </div>

  <!-- Right Side: Sidebar Dynamic Tooltip & Registry List -->
  <div style="flex: 1; background: #fff; padding: 15px; border-radius: 6px; border: 1px solid #dcdcdc; display: flex; flex-direction: column; justify-content: space-between;">
    <div>
      <h3 id="region-title" style="margin-top: 0; color: #111;">Hover Over a Highlighted Region</h3>
      <p id="talk-details" style="font-style: italic; color: #666;">Move your cursor over an active state or province to pull up the most recent academic or institutional seminar brief.</p>
    </div>
    
    <div style="border-top: 1px solid #eee; padding-top: 10px; margin-top: 10px; font-size: 13px; color: #555;">
      <strong>Active Locations:</strong> Ontario (CA), New Mexico (US), Texas (US).
    </div>
  </div>
</div>

<!-- Simple Vanilla Script for Hover Actions -->
<script>
  document.querySelectorAll('.state').forEach(item => {
    item.addEventListener('mouseenter', function() {
      document.getElementById('region-title').innerText = this.getAttribute('data-name');
      document.getElementById('talk-details').innerText = this.getAttribute('data-talk');
    });
    item.addEventListener('mouseleave', function() {
      document.getElementById('region-title').innerText = "Hover Over a Highlighted Region";
      document.getElementById('talk-details').innerText = "Move your cursor over an active state or province to pull up the most recent academic or institutional seminar brief.";
    });
  });
</script>
