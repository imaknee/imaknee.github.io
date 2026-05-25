---
layout: single
title: "Seminar & Talk Registry"
permalink: /talks/
author_profile: true
---



<p>Map of most recent university seminars and conference presentations across the United States and Canada.</p>

<!-- Interactive Map Container -->
<div class="map-dashboard" style="display: flex; gap: 24px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; background: #ffffff; padding: 25px; border-radius: 12px; border: 1px solid #e1e4e6; color: #24292e; box-shadow: 0 4px 12px rgba(0,0,0,0.03);">
  
  <!-- Left Side: Local SVG Map Wrapper -->
  <div style="flex: 1.8; min-width: 500px; position: relative;">
    
    <!-- Pulling the perfect local vector asset from your repository -->
    <object id="us-vector-map" type="image/svg+xml" data="/assets/images/us-map.svg" style="width: 100%; height: auto; pointer-events: all; border: 1px solid #eaecef; border-radius: 8px; background: #f6f8fa;">
    </object>

    <!-- Custom Floating Box to Capture Ontario Presentations -->
    <div id="CA-ON" class="canada-node" style="position: absolute; top: 15px; right: 15px; background: #2c3e50; color: #fff; padding: 6px 12px; border-radius: 4px; font-size: 12px; font-weight: 600; cursor: pointer; transition: background 0.2s;" data-name="Ontario" data-talk="University of Waterloo (Scheduled Technical Briefing: June 2026)">
      🇨🇦 Ontario
    </div>
  </div>

  <!-- Right Side: Dynamic Presentation Readout Panel -->
  <div style="flex: 1; background: #f8f9fa; padding: 22px; border-radius: 8px; border: 1px solid #e1e4e6; display: flex; flex-direction: column; justify-content: space-between; min-width: 260px;">
    <div>
      <div style="font-size: 11px; text-transform: uppercase; letter-spacing: 0.07em; color: #586069; margin-bottom: 8px; font-weight: 600;">Seminar Logs</div>
      <h3 id="region-title" style="margin: 0 0 12px 0; font-size: 22px; font-weight: 600; color: #0366d6; line-height: 1.2;">Hover Over an Active State</h3>
      <p id="talk-details" style="font-size: 14px; line-height: 1.5; color: #444d56; margin: 0; font-style: italic;">
        Hover your cursor over any highlighted state to pull up the most recent research lecture
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
    "WA": "2025 ModSim Workshop<br>'Is Neuromorphic Computing Ready for Prime Time'",
    "OR": "2018 NICE Conference<br>'Is Neuromorphic Algorithms for Scientific Computing'",
    "CA": "2025 Gage Lab Symposium<br>2025 IEEE NER<br>2019 UC Irvine CNLM Colloquium<br>2014 UC Irvine Neurobiology of Learning and Memory",
    "CO": "2023 Workshop on Scalable Algorithms for Large-Scale Heterogeneous Systems<br>'Pursuit of the Brain's Ubiquitous Stochasticity'",
    "NM": "2026 Energy Consequences of Information Workshop<br>2018 University of New Mexico Applied Math Seminar<br>",
    "TX": "2023 Texas A&M TEES Talk<br>'Full Stack Neuromorphic'<br>2019 University of Texas San Antonio AI Summit<br>2019 University of Texas Austin Bio-Inspired Computing Colloquium",
    "IL": "2024 IEEE BRAIN Discovery and Neurotechnology Workshop<br>2014 University of Illinois Urbana Champaign",
    "IN": "2026 Purdue PN3 Symposium<br>'The Dawn of Neuromorphic Algorithms'",
    "VA": "2012 Virginia Tech Carilion Research Institute",
    "MD": "2024 NIH Wednesday Afternoon Lecture Series<br>'How Neuromorphic Computing Can Help Us Understand the Brain'",
    "GA": "2025 Georgia Tech CRNCH Summit<br>'A Probabilistic Future for Neuromorphic Computing'",
    "TN": "2022 ICONS Conference",
    "NY": "2019 NICE Conference<br>'Mosaics'",
    "MA": "2012 Boston University Biomedical Engineering Seminar Series<br>'Adult Hippocampal Neurogenesis: Memory Resoultion, Pattern Separation, or Both?",
    "RI": "2023 Mathematics of Scientific Machine Learning<br>'A Probabilistic Future for Neuromorphic Computing'",
    "UT": "2018 University of Utah Snowbird Symposium."
  };

  const nameMap = {
    "WA": "Washington", "OR": "Oregon", "CA": "California", "CO": "Colorado",
    "NM": "New Mexico", "TX": "Texas", "IL": "Illinois", "IN": "Indiana",
    "VA": "Virginia", "MD": "Maryland", "GA": "Georgia", "TN": "Tennessee",
    "NY": "New York", "MA": "Massachusetts", "RI": "Rhode Island", "UT": "Utah"
  };

  const mapObject = document.getElementById('us-vector-map');

  // Wait for the local file to load inside the container
  mapObject.addEventListener('load', function() {
    const svgDoc = mapObject.contentDocument;
    
    // Global style override inside the clean template
    const styleElement = svgDoc.createElementNS("http://www.w3.org/2000/svg", "style");
    styleElement.textContent = "path { transition: fill 0.2s ease-in-out !important; cursor: pointer !important; fill: #e1e4e6 !important; }";
    svgDoc.documentElement.appendChild(styleElement);
    styleElement.textContent = "polygon { transition: fill 0.2s ease-in-out !important; cursor: pointer !important; fill: #e1e4e6 !important; }";
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
    // CHANGED: innerHTML allows the panel to parse links and line breaks perfectly
    document.getElementById('talk-details').innerHTML = description; 
    
    document.getElementById('talk-details').style.fontStyle = (description.includes("pending")) ? "italic" : "normal";
  }
  function resetSidebar() {
    document.getElementById('region-title').innerText = "Hover Over an Active State";
    document.getElementById('talk-details').innerText = "Hover your cursor over any highlighted state or the Ontario badge to pull up the corresponding research lectures and institutional briefs.";
    document.getElementById('talk-details').style.fontStyle = "italic";
  }
</script>

## Select Online Seminars

[2026 Purdue PN3 "Dawn of Neuromorphic Algorithms"](https://www.youtube.com/live/KkSbs-JsaPc?si=Sa4G6IRV0mwUb1r5&t=19494)

[2025 IEEE NER "Is Neuromorphic Computing Ready to Deliver on its Promise to Advance Neuroscience"](https://youtu.be/ljsdScNvrKg?si=hPnZYYM0eSu6nwta&t=167)

[2024 NIH Wednesday Afternoon Lecture Series "How Neuromorphic Computing Can Help Us Understand the Brain"](https://oir.nih.gov/wals/2024-2025-wals-season/how-neuromorphic-computing-can-help-understand-brain)

[2023 Open Neuromorphic: Programming Scalable Neuromorphic Algorithms with Fugu](https://www.youtube.com/watch?v=UDM9Mbd0Vaw&t=8s)
