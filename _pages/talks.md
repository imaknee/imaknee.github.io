---
layout: single
title: "Seminar & Talk Registry"
permalink: /talks/
author_profile: true
---

<p>Operational map of university seminars, conference presentations, and national laboratory technical briefings across the United States and Canada.</p>

<!-- Interactive Map Container -->
<div class="map-dashboard" style="display: flex; gap: 24px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; background: #ffffff; padding: 25px; border-radius: 12px; border: 1px solid #e1e4e6; color: #24292e; box-shadow: 0 4px 12px rgba(0,0,0,0.03);">
  
  <!-- Left Side: Local SVG Map Wrapper -->
  <div style="flex: 1.8; min-width: 500px; position: relative;">
    
    <!-- Pulling the perfect local vector asset from your repository -->
    <object id="us-vector-map" type="image/svg+xml" data="/assets/images/us-map.svg" style="width: 100%; height: auto; pointer-events: all; border: 1px solid #eaecef; border-radius: 8px; background: #f6f8fa;">
    </object>

    <!-- Custom Floating Box to Capture Ontario Presentations -->
    <div id="CA-ON" class="canada-node" style="position: absolute; top: 15px; right: 15px; background: #2c3e50; color: #fff; padding: 6px 12px; border-radius: 4px; font-size: 12px; font-weight: 600; cursor: pointer; transition: background 0.2s;" data-name="Ontario" data-talk="University of Waterloo (Scheduled Technical Briefing: June 2026)">
      🇨🇦 Ontario Registry Active
    </div>
  </div>

  <!-- Right Side: Dynamic Presentation Readout Panel -->
  <div style="flex: 1; background: #f8f9fa; padding: 22px; border-radius: 8px; border: 1px solid #e1e4e6; display: flex; flex-direction: column; justify-content: space-between; min-width: 260px;">
    <div>
      <div style="font-size: 11px; text-transform: uppercase; letter-spacing: 0.07em; color: #586069; margin-bottom: 8px; font-weight: 600;">Seminar Logs</div>
      <h3 id="region-title" style="margin: 0 0 12px 0; font-size: 22px; font-weight: 600; color: #0366d6; line-height: 1.2;">Hover Over an Active State</h3>
      <p id="talk-details" style="font-size: 14px; line-height: 1.5; color: #444d56; margin: 0; font-style: italic;">
        Hover your cursor over any highlighted state or the Ontario badge to pull up the corresponding research lectures and institutional briefs.
      </p>
    </div>
    
    <div style="border-top: 1px solid #eaecef; padding-top: 15px; margin-top: 15px; font-size: 12px; line-height: 1.6; color: #586069;">
      <span style="display: inline-block; width: 10px; height: 10px; background-color: #2c3e50; border-radius: 2px; margin-right: 6px;"></span>
      <strong>Monitored Tracks:</strong> 15 US States + Ontario
    </div>
  </div>
</div>

<!-- Smart Script to Bind Interactive Behavior directly to your Local SVG Elements -->
<script>
  // Your exact distribution list of active states mapped to clean text fields
  const seminarData = {
    "WA": "Presentation details pending.",
    "OR": "Presentation details pending.",
    "CA": "Presentation details pending.",
    "CO": "Presentation details pending.",
    "NM": "Sandia National Laboratories / Neural Exploration & Research Lab (Algorithmic Hardware Solvers)",
    "TX": "University of Texas at Austin (Graph Theoretical Boundary Mapping)",
    "IL": "Presentation details pending.",
    "IN": "Presentation details pending.",
    "VA": "Presentation details pending.",
    "MD": "Presentation details pending.",
    "GA": "Presentation details pending.",
    "TN": "Presentation details pending.",
    "NY": "Presentation details pending.",
    "MA": "Presentation details pending.",
    "RI": "Presentation details pending."
  };

  const nameMap = {
    "WA": "Washington", "OR": "Oregon", "CA": "California", "CO": "Colorado",
    "NM": "New Mexico", "TX": "Texas", "IL": "Illinois", "IN": "Indiana",
    "VA": "Virginia", "MD": "Maryland", "GA": "Georgia", "TN": "Tennessee",
    "NY": "New York", "MA": "Massachusetts", "RI": "Rhode Island"
  };

  const mapObject = document.getElementById('us-vector-map');

  // Wait for the local file to load inside the container
  mapObject.addEventListener('load', function() {
    const svgDoc = mapObject.contentDocument;
    
    // Global style override inside the clean template
    const styleElement = svgDoc.createElementNS("http://www.w3.org/2000/svg", "style");
    styleElement.textContent = "path { transition: fill 0.2s ease-in-out !important; cursor: pointer !important; fill: #e1e4e6 !important; }";
    svgDoc.documentElement.appendChild(styleElement);

    // Target your exact 15 states using the official Wikipedia ID schemas
    Object.keys(seminarData).forEach(stateCode => {
      // Wikipedia uses lowercase for paths, uppercase for some layer labels
      const stateElement = svgDoc.getElementById(stateCode.toLowerCase()) || svgDoc.getElementById(stateCode);
      
      if (stateElement) {
        // Shade the active state layer dark blue-grey initially
        stateElement.style.setProperty('fill', '#2c3e50', 'important');
        
        // Interactivity triggers
        stateElement.addEventListener('mouseenter', function() {
          stateElement.style.setProperty('fill', '#4a90e2', 'important');
          updateSidebar(nameMap[stateCode], seminarData[stateCode]);
        });
        
        stateElement.addEventListener('mouseleave', function() {
          stateElement.style.setProperty('fill', '#2c3e50', 'important');
          resetSidebar();
        });
      }
    });
  });

  // Standalone interactive handling for Ontario block
  const ontarioNode = document.getElementById('CA-ON');
  ontarioNode.addEventListener('mouseenter', function() {
    this.style.background = "#4a90e2";
    updateSidebar("Ontario", this.getAttribute('data-talk'));
  });
  ontarioNode.addEventListener('mouseleave', function() {
    this.style.background = "#2c3e50";
    resetSidebar();
  });

  function updateSidebar(title, description) {
    document.getElementById('region-title').innerText = title;
    document.getElementById('talk-details').innerText = description;
    document.getElementById('talk-details').style.fontStyle = (description.includes("pending")) ? "italic" : "normal";
  }

  function resetSidebar() {
    document.getElementById('region-title').innerText = "Hover Over an Active State";
    document.getElementById('talk-details').innerText = "Hover your cursor over any highlighted state or the Ontario badge to pull up the corresponding research lectures and institutional briefs.";
    document.getElementById('talk-details').style.fontStyle = "italic";
  }
</script>
