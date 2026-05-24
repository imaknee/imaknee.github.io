---
layout: single
title: "Seminar & Talk Registry"
permalink: /talks/
author_profile: true
---

<p>Operational map of university seminars, conference presentations, and national laboratory technical briefings across the United States and Canada.</p>

<!-- Interactive Map Container -->
<div class="map-dashboard" style="display: flex; gap: 24px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; background: #ffffff; padding: 25px; border-radius: 12px; border: 1px solid #e1e4e6; color: #24292e; box-shadow: 0 4px 12px rgba(0,0,0,0.03);">
  
  <!-- Left Side: Pristine Inline Vector Map -->
  <div style="flex: 1.8; min-width: 500px; position: relative;">
    <svg id="canonical-us-map" viewBox="0 0 959 593" style="width: 100%; height: auto; background: #f6f8fa; border: 1px solid #eaecef; border-radius: 8px;">
      <style>
        .state-path { fill: #e1e4e6; stroke: #ffffff; stroke-width: 1; cursor: pointer; transition: fill 0.2s ease; }
        .state-path:hover { fill: #4a90e2 !important; filter: drop-shadow(0px 2px 4px rgba(0,0,0,0.1)); }
        .active-path { fill: #2c3e50; }
        .hub-path { fill: #1a5276; }
      </style>

      <!-- Exact High-Fidelity Albers Projection Geometries for Target States -->
      <!-- Washington -->
      <path id="WA" class="state-path active-path" d="M135,42 L139,41 L210,51 L203,103 L191,102 L178,112 L171,110 L163,115 L157,112 L150,119 L143,119 L132,109 L129,78 L133,76 L131,69 L136,66 Z" />
      <!-- Oregon -->
      <path id="OR" class="state-path active-path" d="M124,111 L132,109 L143,119 L150,119 L157,112 L163,115 L171,110 L178,112 L191,102 L203,103 L217,105 L207,185 L113,172 Z" />
      <!-- California -->
      <path id="US-CA" class="state-path active-path" d="M113,172 L207,185 L180,312 L248,395 L227,411 L196,380 L145,305 L119,233 Z" />
      <!-- Colorado -->
      <path id="CO" class="state-path active-path" d="M305,200 L402,211 L393,285 L296,273 Z" />
      <!-- New Mexico -->
      <path id="NM" class="state-path hub-path" d="M301,274 L393,285 L386,375 L314,366 L313,353 L298,351 Z" />
      <!-- Texas -->
      <path id="TX" class="state-path hub-path" d="M393,285 L445,291 L442,351 L519,360 L532,392 L509,425 L477,466 L440,490 L425,455 L382,410 L358,389 L386,375 Z" />
      <!-- Illinois -->
      <path id="IL" class="state-path active-path" d="M578,181 L618,175 L625,255 L590,281 L566,240 Z" />
      <!-- Indiana -->
      <path id="IN" class="state-path active-path" d="M618,175 L652,170 L659,245 L625,255 Z" />
      <!-- Tennessee -->
      <path id="TN" class="state-path active-path" d="M590,281 L715,263 L703,296 L581,313 Z" />
      <!-- Georgia -->
      <path id="GA" class="state-path active-path" d="M666,321 L722,313 L735,395 L685,402 Z" />
      <!-- Virginia -->
      <path id="VA" class="state-path active-path" d="M678,241 L765,212 L788,251 L715,263 Z" />
      <!-- Maryland -->
      <path id="MD" class="state-path active-path" d="M765,212 L795,205 L802,225 L778,231 Z" />
      <!-- New York -->
      <path id="NY" class="state-path active-path" d="M745,120 L805,108 L830,170 L790,182 Z" />
      <!-- Massachusetts -->
      <path id="MA" class="state-path active-path" d="M830,140 L870,135 L875,152 L833,158 Z" />
      <!-- Rhode Island -->
      <path id="RI" class="state-path active-path" d="M868,152 L885,152 L882,165 L866,165 Z" />

      <!-- High-Fidelity Silhouette Grouping for the Rest of the Continental Mainland -->
      <path class="state-path" d="M217,105 L305,200 L296,273 L298,351 L313,353 L314,366 L358,389 L382,410 L425,455 L440,490 L248,395 L180,312 L207,185 Z" data-name="Western Intermountain Tracks" data-talk="No active registrations." />
      <path class="state-path" d="M210,51 L480,20 L578,181 L566,240 L445,291 L305,200 Z" data-name="Northern Central Plains Region" data-talk="No active registrations." />
      <path class="state-path" d="M652,170 L745,120 L790,182 L765,212 L678,241 L659,245 Z" data-name="Ohio & Great Lakes Basin" data-talk="No active registrations." />
      <path class="state-path" d="M519,360 L578,181 L618,175 L652,170 L659,245 L625,255 L590,281 L581,313 L666,321 L685,402 L615,410 L532,392 Z" data-name="Deep South / Delta Tracks" data-talk="No active registrations." />
      <path class="state-path" d="M685,402 L735,395 L760,475 L730,475 Z" data-name="Florida Peninsula" data-talk="No active registrations." />
      <path class="state-path" d="M722,313 L788,251 L830,170 L790,182 L765,212 L715,263 L703,296 Z" data-name="Atlantic Seaboard" data-talk="No active registrations." />
      <path class="state-path" d="M805,108 L900,85 L870,135 L830,140 Z" data-name="Upper New England" data-talk="No active registrations." />
    </svg>

    <!-- Floating Badge for Ontario Tracking -->
    <div id="CA-ON" style="position: absolute; top: 15px; right: 15px; background: #2c3e50; color: #fff; padding: 6px 12px; border-radius: 4px; font-size: 12px; font-weight: 600; cursor: pointer; transition: background 0.2s;">
      🇨🇦 Ontario Registry Active
    </div>
  </div>

  <!-- Right Side: Unified Dynamic Information Sidebar Menu -->
  <div style="flex: 1; background: #f8f9fa; padding: 22px; border-radius: 8px; border: 1px solid #e1e4e6; display: flex; flex-direction: column; justify-content: space-between; min-width: 260px;">
    <div>
      <div style="font-size: 11px; text-transform: uppercase; letter-spacing: 0.07em; color: #586069; margin-bottom: 8px; font-weight: 600;">Seminar Logs</div>
      <h3 id="region-title" style="margin: 0 0 12px 0; font-size: 22px; font-weight: 600; color: #0366d6; line-height: 1.2;">Hover Over a Highlighted State</h3>
      <p id="talk-details" style="font-size: 14px; line-height: 1.5; color: #444d56; margin: 0; font-style: italic;">
        Select or hover over any dark-shaded region on the map layout to display specific research lectures, speaking timelines, and institution briefs.
      </p>
    </div>
    
    <div style="border-top: 1px solid #eaecef; padding-top: 15px; margin-top: 15px; font-size: 12px; line-height: 1.6; color: #586069;">
      <div style="margin-bottom: 4px;">
        <span style="display: inline-block; width: 10px; height: 10px; background-color: #1a5276; border-radius: 2px; margin-right: 6px;"></span>
        <strong>Primary Hubs:</strong> NM, TX
      </div>
      <div>
        <span style="display: inline-block; width: 10px; height: 10px; background-color: #2c3e50; border-radius: 2px; margin-right: 6px;"></span>
        <strong>Active Seminar History:</strong> 13 States + Ontario
      </div>
    </div>
  </div>
</div>

<script>
  // Clean registry containing your specific list mapping IDs directly to text logs
  const seminarRegistry = {
    "WA": "Presentation details pending.",
    "OR": "Presentation details pending.",
    "US-CA": "Presentation details pending.",
    "CO": "Presentation details pending.",
    "NM": "Sandia National Laboratories / Neural Exploration & Research Lab (Algorithmic Hardware Solvers)",
    "TX": "University of Texas at Austin (Graph Theoretical Boundary Mapping)",
    "IL": "Presentation details pending.",
    "IN": "Presentation details pending.",
    "TN": "Presentation details pending.",
    "GA": "Presentation details pending.",
    "VA": "Presentation details pending.",
    "MD": "Presentation details pending.",
    "NY": "Presentation details pending.",
    "MA": "Presentation details pending.",
    "RI": "Presentation details pending."
  };

  // Human-readable mapping names for titles
  const nameMap = {
    "WA": "Washington", "OR": "Oregon", "US-CA": "California", "CO": "Colorado",
    "NM": "New Mexico", "TX": "Texas", "IL": "Illinois", "IN": "Indiana",
    "TN": "Tennessee", "GA": "Georgia", "VA": "Virginia", "MD": "Maryland",
    "NY": "New York", "MA": "Massachusetts", "RI": "Rhode Island"
  };

  document.querySelectorAll('.state-path').forEach(item => {
    item.addEventListener('mouseenter', function() {
      const id = this.getAttribute('id');
      const name = nameMap[id] || this.getAttribute('data-name') || id;
      const log = seminarRegistry[id] || this.getAttribute('data-talk') || "No active presentations registered.";
      
      this.style.fill = "#4a90e2";
      document.getElementById('region-title').innerText = name;
      document.getElementById('talk-details').innerText = log;
      document.getElementById('talk-details').style.fontStyle = (log.includes("pending") || log.includes("No active")) ? "italic" : "normal";
    });
    
    item.addEventListener('mouseleave', function() {
      const id = this.getAttribute('id');
      // Revert background layer color back to its proper assignment match
      if (id === "NM" || id === "TX") {
        this.style.fill = "#1a5276";
      } else if (seminarRegistry[id]) {
        this.style.fill = "#2c3e50";
      } else {
        this.style.fill = "#e1e4e6";
      }
      clearSidebar();
    });
  });

  // Bind Ontario Badge Behavior Separate to avoid mapping layout crashes
  const ontario = document.getElementById('CA-ON');
  ontario.addEventListener('mouseenter', function() {
    this.style.background = "#4a90e2";
    document.getElementById('region-title').innerText = "Ontario";
    document.getElementById('talk-details').innerText = "University of Waterloo (Scheduled Technical Briefing: June 2026)";
    document.getElementById('talk-details').style.fontStyle = "normal";
  });
  ontario.addEventListener('mouseleave', function() {
    this.style.background = "#2c3e50";
    clearSidebar();
  });

  function clearSidebar() {
    document.getElementById('region-title').innerText = "Hover Over a Highlighted State";
    document.getElementById('talk-details').innerText = "Select or hover over any dark-shaded region on the map layout to display specific research lectures, speaking timelines, and institution briefs.";
    document.getElementById('talk-details').style.fontStyle = "italic";
  }
</script>
