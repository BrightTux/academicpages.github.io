---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}


<a style="line-height: 1.5;" href="https://github.com/BrightTux/brighttux.github.io/raw/master/files/cv.pdf"><span style="color: #333333;"><span id="printThis" style="font-size: medium;">Also available in PDF format.</span></span></a>
<h1 class="western" align="center"><b>Clarence Cheong</b></h1>
<p style="line-height: 1.5;" align="center"><span style="font-size: medium;"><b>Curriculum Vitae</b> </span></p>
<p style="line-height: 1.5;" align="center"><span style="font-size: medium;">clarence_han[at]hotmail[dot]com | <a href="http://www.brighttux.github.io/">http://www.brighttux.github.io</a> | <a href="https://scholar.google.com/citations?user=z8n5LTEAAAAJ&hl=en">Google Scholar</a></span></p>




<script>
  console.log("Use printcv() to set certain elements to hidden");
  console.log("Remember to change the scale to 72% before printing")
  
  function printcv()
  {
  console.log("function print called");
  document.getElementById("printThis").style.visibility = "hidden"; 
  document.getElementsByClassName("btn btn--inverse")[0].style.visbility = "hidden";
  console.log("remember to set the scale to 72%");
  }
</script>




Education
======

* M.S. in Information Technology, Multimedia University, 2019 (expected)
  * Thesis Topic: Extraction and Retrieval of Object Semantics for Long-Term Car Park Surveillance Videos

* B.Eng. in Electronics Majoring in Multimedia, Multimedia University, 2012
  * Thesis Topic: Speaker Voice Recognition

* Diploma in Technology, Mechatronics, Tunku Abdul Rahman College, 2008


Work experience
======
* Oct 2016 - Current: Research Scholar
  * Multimedia University, MY
  * Project: SHERLOCK: Video Analytics for Multi-Camera Long-term Surveillance in Smart Cities
  * Supervisor: [Professor John See](http://pesona.mmu.edu.my/~johnsee/)
  
* Nov 2018 - Feb 2019: Freelance Project
  * Project: Retail Store Analytics using Video Feed 
  * Responsibilities: Develop a solution to extract customer's information such as location, clothing preference, entry/exit, visited aisle, payment counter, and etc using video feed.

* Summer 2018: Research Intern
  * National Chung Cheng University, TW
  * Project: Vehicle Trajectory Classification using ML
  * Supervisor: [Professor Wen-Nung, Lie](http://www.dsp.ee.ccu.edu.tw/wnlie/)
  
* Sept 2012 - Sept 2016: Application Management Service Delivery
  * Hewlett Packard Enterprise, MY
  * Responsibilities: Provided 24/7 Service Delivery Support for a local bank’s (CIMB) core payment systems which includes IBG, Direct Debit, Autopay, Remittance as well as PTPTN system. While providing technical support, I would be liaising with the clients and IT operations team. Along with that, during the tenure I was also working on the CIMB 1P (1 Platform) project to develop extraction programs based on client’s requirements.
  * Supervisor: [Chor Pheng Khee](https://my.linkedin.com/in/chor-pheng-khee-652685133)

* Aug 2010 - Jan 2012: Research Assistant
  * Multimedia University, MY
  * Project: Content Management System (CMS) for Multimedia University Staffs to report their R&D progress as well as contributions. The system went live from 2012 and was decommissioned on 2017.
  * Supervisor: [Dr Chin Ji Jian](https://mmuexpert.mmu.edu.my/jjchin)
  
Skills
======
* OpenCV, Docker
* C++, JavaScript, Python, SQL, PHP, VB, HTML, MATLAB, PowerShell, Unix Shell Scripting
* Mainframe
  * COBOL, JCL, CA-7, z/OS



Publications
======
  <ul>{% for post in site.publications %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>


Awards
======
* 2018
  * International Invention, Innocation & Technology Exhibition (ITEX), Malaysia: Silver Medalist (ICT & Multimedia - University & Research Institute Category)
  * Malaysia Technology Expo (MTE): Invention & Innovation Category: Bronze Medalist
  * A.I Hackathon for Good: 2nd Runner Up
* 2017
  * Research Innovation Commercialisation & Entrepreneurship Showcase (RICES): 1'st Runner Up 

<!---
Talks
======
  <ul>{% for post in site.talks %}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service and leadership
======
* Currently signed in to 43 different slack teams
-->
