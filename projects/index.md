---
layout: default
title: Projects
permalink: /projects/
---

## Projects

### I. [Mill Marginalia](https://millmarginalia.org/)

![mill-marginalia](../assets/mill-marginalia.jpg)

**Public Humanities / Digital Humanities Project - Fall '23 - Spring '24**
* A multi-faceted open access digital resource showcasing the manuscript marginalia written in texts by both J. S. Mill and his father, enabling researchers and students to read these alongside scholarly writing about these materials.*
![mill-marginalia-viz](../assets/mm-viz.jpg)
As a research assistant on this digitization project, Reliance devloped a visualization dashboard, digitized marginalia, and contributed to the development of technical documentation and articles to the [blog](https://blog.millmarginalia.org/)
  
- Utilized Power BI and MS Excel for data analysis, cleaning, and visualization
- Engaged with Adobe for marginalia digitization
- Documented marginalia digitization processes

## II. [Documentation for Georeferenced Maps](https://adhc.lib.ua.edu/mapathon-day-02-georeferencing-maps-in-qgis/)
**Public Humanities / Digital Humanities Project - Summer '24**
![georeferencing-image](../assets/georeferencing.jpg)

*A mapathon-focused series aimed at providing a practical guide for mapathon participants on practical elements that will enable them complete the georeferencing task on a scanned image of a map.*

- Utilized Scribe for georeferencing documentation
- Engaged Geographic Information Systems tools- QGIS for georeferncing Tuscaloosa maps


## III. [Digital Storytelling & Critical Digital Literacy](https://criticaldigitalliteracies.omeka.net/)

![cdl.omeka-image](../assets/cdl.omeka.png)
**GenAI Literacy / Rhetoric and Composition / Pedagogical Research / Web Design Project - Spring '25**

*This project explores digital storytelling and embodiment in AI technologies. This website was built as part of my master's capstone advancing critical embodiment in AI (mis)representations.*

- Built using Omeka, Canva, and MS PowerPoint 
- Prompt engineering via Wepik AI, Adobe AI, Dall-E
- Content analysis of AI misrepresentations in Wepik AI, Adobe AI, Dall-E

## IV. Mapping Epidemic Discourse in Nigeria

**Risk Communications / Health Humanities / Independent Project - Summer '25**

*Spatial analysis and visualization of Malaria incidence in Nigeria with focus on the South Eastern region*

![cdl.omeka-image](../assets/malaria-analysis_SE%202019.png)
![cdl.omeka-image](../assets/malaria-analysis_SE_2020.png)

- Engaged QGIS, ArcGIS, and MS PowerPoint 
- Built data collection forms using ODK / KoboCollect

## V. Portfolio Design and Development  
**Web Design Project — Ongoing**  
*Building a personal academic portfolio with GitHub Pages and Jekyll.*

Designed this digital portfolio to reflect professional identity and showcase interdisciplinary research, teaching, and creative work. The site emphasizes accessibility, clean typography, and responsive design principles.

## VI. Rehumanizing Data: An Interactive Word-Cone

**Digital Humanities / Interactive Design — Spring '26**

*An interactive 3D visualization built with p5.js (WebGL). Words from a research paper abstract are placed on a rotating cone surface, exploring how embodied spatial form can rehumanize abstracted data.*

**Controls:** Click and drag to rotate · Double-click to toggle auto-rotation

<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.11.3/p5.min.js" crossorigin="anonymous" referrerpolicy="no-referrer"></script>

<div id="sketch-container" style="width:100%;max-width:800px;aspect-ratio:8/7;margin:2rem auto;overflow:hidden;border:1px solid #dee2e6;border-radius:4px;"></div>

<script>
const rehumanizingSketch = (p) => {
  let rotX = 0.3;
  let rotY = 0;
  let autoRotate = true;
  let dragging = false;
  let lastX, lastY;
  let font;

  const lines = [
    "In a data-driven",
    "neoliberalist world, terms such",
    "as data-driven, big data, metadata,",
    "data analytics, statistics, demographics,",
    "bio-data, and website analytics reduce bodies",
    "to numbers and data points, promote surveillance,",
    "erase lived experiences, and foster marginalization by",
    "ignoring the lived experiences of individuals at the margins",
    "and decentering the sociopolitical, economic, and cultural contexts",
    "that shape their identities. Beyond quantification and data points,",
    "data are capta and bodies are creators and repositories of knowledge.",
    'Building on Sutherland et al.\'s "Feminist Data Manifest-NO,"',
    "this work pays attention to statements four, nineteen, twenty,",
    "twenty-six, and twenty-nine. This paper argues that",
    "DH principles can antidote datafication.",
  ];

  p.preload = () => {
    font = p.loadFont("https://cdnjs.cloudflare.com/ajax/libs/topcoat/0.8.0/font/SourceCodePro-Regular.otf");
  };

  p.setup = () => {
    let c = document.getElementById('sketch-container');
    let canvas = p.createCanvas(c.offsetWidth, c.offsetHeight, p.WEBGL);
    canvas.parent('sketch-container');
    p.textFont(font);
    p.textAlign(p.CENTER, p.CENTER);
  };

  p.draw = () => {
    p.background(250, 249, 246);
    if (autoRotate) rotY += 0.008;

    let totalHeight = 400;
    let tipY = -totalHeight / 2;
    let baseY = totalHeight / 2;
    let maxRadius = 250;

    let nearFlip = p.abs(p.abs(rotX) - p.PI);
    let flatness = p.constrain(p.map(nearFlip, 0.25, 0, 0, 1), 0, 1);

    if (flatness > 0.85) {
      let lineSpacing = 26;
      let totalH = (lines.length - 1) * lineSpacing;
      let startY = -totalH / 2;

      p.textSize(18);
      p.fill(26, 26, 24);
      p.noStroke();
      p.text("Rehumanizing Data", 0, startY - 80);

      p.textSize(11);
      p.fill(100);
      p.text("How Digital Humanities Can Serve as an Antidote to Datafication", 0, startY - 58);

      p.textSize(10);
      p.fill(160);
      p.text("A B S T R A C T", 0, startY - 36);

      p.textSize(13);
      p.fill(26, 26, 24);
      for (let i = 0; i < lines.length; i++) {
        p.text(lines[i], 0, startY + i * lineSpacing);
      }

      p.textSize(10);
      p.fill(160);
      p.text("ethics of care · digital humanities · datafication · critical embodiment", 0, startY + totalH + 28);

    } else {
      p.rotateX(rotX);
      p.rotateY(rotY);

      p.push();
      p.translate(0, tipY - 60, 0);
      p.rotateY(-rotY);
      p.rotateX(-rotX);
      p.textSize(18);
      p.fill(26, 26, 24);
      p.noStroke();
      p.text("Rehumanizing Data", 0, 0);
      p.textSize(11);
      p.fill(100);
      p.text("How Digital Humanities Can Serve as an Antidote to Datafication", 0, 22);
      p.pop();

      p.noFill();
      p.stroke(180, 200, 185, 120);
      p.strokeWeight(0.4);
      for (let r = 0; r <= 12; r++) {
        let t = r / 12;
        let y = p.lerp(tipY, baseY, t);
        let radius = t * maxRadius;
        p.beginShape();
        for (let a = 0; a <= p.TWO_PI; a += 0.15) {
          p.vertex(p.cos(a) * radius, y, p.sin(a) * radius);
        }
        p.endShape(p.CLOSE);
      }

      for (let i = 0; i < lines.length; i++) {
        let t = i / (lines.length - 1);
        let y = p.lerp(tipY + 10, baseY - 10, t);
        let radius = t * maxRadius;
        let words = lines[i].split(" ");

        for (let w = 0; w < words.length; w++) {
          let a = (w / words.length) * p.TWO_PI + i * 0.4;
          let x = p.cos(a) * radius;
          let z = p.sin(a) * radius;
          let facing = p.cos(a + rotY);
          let alpha = p.map(facing, -1, 1, 30, 255);

          p.push();
          p.translate(x, y, z);
          p.rotateY(-rotY);
          p.rotateX(-rotX);
          p.textSize(p.map(t, 0, 1, 9, 14));
          p.fill(45, 90, 61, alpha);
          p.noStroke();
          p.text(words[w], 0, 0);
          p.pop();
        }
      }

      p.push();
      p.translate(0, tipY, 0);
      p.fill(45, 90, 61);
      p.noStroke();
      p.sphere(3);
      p.pop();

      p.push();
      p.translate(0, baseY, 0);
      p.stroke(45, 90, 61, 80);
      p.strokeWeight(1);
      p.noFill();
      p.beginShape();
      for (let a = 0; a <= p.TWO_PI; a += 0.1) {
        p.vertex(p.cos(a) * maxRadius, 0, p.sin(a) * maxRadius);
      }
      p.endShape(p.CLOSE);
      p.pop();
    }
  };

  p.mousePressed = () => {
    dragging = true;
    autoRotate = false;
    lastX = p.mouseX;
    lastY = p.mouseY;
  };

  p.mouseDragged = () => {
    if (dragging) {
      rotY += (p.mouseX - lastX) * 0.01;
      rotX += (p.mouseY - lastY) * 0.01;
      rotX = p.constrain(rotX, -p.PI, p.PI);
      lastX = p.mouseX;
      lastY = p.mouseY;
    }
  };

  p.mouseReleased = () => {
    dragging = false;
  };

  p.doubleClicked = () => {
    autoRotate = !autoRotate;
  };

  p.windowResized = () => {
    let c = document.getElementById('sketch-container');
    p.resizeCanvas(c.offsetWidth, c.offsetHeight);
  };
};

new p5(rehumanizingSketch, 'sketch-container');
</script>


- Implemented in Markdown and HTML using Jekyll and GitHub Pages  
- Customized minimal theme with navigation bar, tags, and integrated analytics  
- Version controlled using Git and GitHub  

💻 **Source Code:** [GitHub Repository](https://relianceenwerem.github.io/my-portfolio/)