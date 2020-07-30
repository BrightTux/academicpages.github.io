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
<p style="line-height: 1.5;" align="center"><span style="font-size: medium;"><b>Curriculum Vitae</b> </span> <br>
clarence_han[at]hotmail[dot]com | <a href="https://github.com/BrightTux">https://github.com/BrightTux</a></span><br>
Python, Bash, JavaScript, C++, COBOL, JCL | Git, OpenCV, Docker, Tensorflow, Ansible</p>

<script>
console.log("Use printcv() to set certain elements to hidden");

function printcv()
{
  console.log("function printcv called");
  
  document.getElementById("printThis").style.visibility = "hidden"; 
  document.getElementsByClassName("page__title")[0].style.visibility = "hidden";
  document.getElementsByClassName("btn btn--inverse")[0].style.visibility = "hidden";
  document.getElementById("publicationslist").style.visibility = "hidden";
  document.getElementsByClassName("author__avatar")[0].style.visibility ="hidden";
  document.getElementsByClassName("author__name")[0].style.visibility ="hidden";
  document.getElementsByClassName("author__bio")[0].style.visibility ="hidden";
  
  document.getElementById("printThis").style.display= "none";
  document.getElementsByClassName("page__title")[0].style.display= "none";
  document.getElementsByClassName("btn btn--inverse")[0].style.display= "none";
  document.getElementById("publicationslist").style.display= "none";
  document.getElementsByClassName("author__avatar")[0].style.display= "none";
  document.getElementsByClassName("author__name")[0].style.display= "none";
  document.getElementsByClassName("author__bio")[0].style.display= "none";
  document.getElementsByClassName("page__footer")[0].style.display= "none";

  
  console.log("Remember to change the scale to 72% before printing - use Chrome/Linux");

};
  
</script>

Work experience
======
* May 2019 - Current: Maintenance & Testing Technician (Machine Learning)
  * Almex System Technology Asia (Almex-STA), MY 
  * Working remotely with a distributed team in HQ (Japan)
  * Tools used: Python, TensorFlow, Bash, OpenCV, Docker, Ansible, MongoDB, PyQt
  * Projects: 
      * Flir AX8 Thermal Camera API: Cowritten an API for thermal imaging purposes.
      * Image Labeling Tool: Enhance existing [labeling tool](https://github.com/tzutalin/labelImg) to include MongoDB, automatic text detection & labeling (via Openvino). Automatic installation on multiple workstations via Ansible.
      * FCOS-Styled Datasets Generator: Converted existing datasets into Fully Convolutional One-Stage [(FCOS)](https://arxiv.org/abs/1904.01355) styled tfrecord dataset. 
      * Japanese Characters (Hiragana, Katagana, Kanji) Text OCR: Developed an system to generate pairs of binary mask and synthetic text as training data. This includes checking of available unique glyphs for each font and ensuring the generated text does not exceed the canvas upon various augmentation. 
      * SynthText-JPN (Japanese Text-on-Image Synthesis): Enhance existing [text generators](https://github.com/gachiemchiep/SynthText) to generated more text-in-image samples, the process includes generating new depth maps and new segmentation maps to generate own background images. 
      * Text Saliency Mapper: Developed saliency map generator to visualize and understand how well each text-characters are predicted. 

* Oct 2016 - April 2019: Research Scholar
  * Multimedia University, MY
  * Project: SHERLOCK: Video Analytics for Multi-Camera Long-term Surveillance in Smart Cities. 
  * Responsibilities: Developed an object semantics extraction and retrieval engine, includes data preprocessing, manual annotation. Attended Conferences, participated in bi-weekly reading group on latest research works in Computer Vision (Aesthetics, Medical, Micro Expressions, Image Recognition), exhibited and showcased the SHERLOCK Retrieval Engine. Published 2 conference papers; Currently writting a journal as well another conference paper (WIP). Obtained copyright for the retrieval engine.
  * Tools used: C++, OpenCV, Python, HTML, CSS and JavaScript
  * Supervisor: [Professor John See](http://pesona.mmu.edu.my/~johnsee/)
  
* Nov 2018 - Feb 2019: Freelance Project
  * Project: Retail Store Analytics using Video Feed 
  * Developed a solution to extract customer's information such as location, clothing preference, entry/exit, visited aisle, payment counter, and etc using video feed. A simple deep learning model was trained to differentiate between male and female customers in AWS. The extracted JSON data is then sent to AWS for storage and postprocessing by the client.
  * Tools used: Raspberry Pi, OpenCV, Python, BASH, AWS and Docker. 

* Summer 2018 (Jun 2018 - Sept 2018): Research Intern
  * National Chung Cheng University, TW
  * Project: Vehicle Trajectory Classification using Machine Learning tools. Learned how to develop a simple network using Convolutional Neural Networks.
  * Tools used: Python, OpenCV, Keras and Tensorflow.
  * Supervisor: [Professor Wen-Nung, Lie](http://www.dsp.ee.ccu.edu.tw/wnlie/)
  
* Sept 2012 - Sept 2016: Application Management Service Delivery
  * Hewlett Packard Enterprise, MY
  * Provided 24/7 Service Delivery Support for a local bank’s (CIMB) core payment systems which includes IBG, Direct Debit, Autopay, Remittance as well as PTPTN system. While providing technical support, I would be liaising with the clients and IT operations team. Along with that, during the tenure I was also working on the CIMB 1P (1 Platform) project to develop extraction programs based on client’s requirements.
  * Tools used: (Mainframe Z/os) COBOL, JCL, CA-7, Unix, BASH, Visual Basic and SQL.
  * Supervisor: [Chor Pheng Khee](https://my.linkedin.com/in/chor-pheng-khee-652685133)

* Aug 2010 - Jan 2012: Research Assistant
  * Multimedia University, MY
  * Project: Content Management System (CMS) for Multimedia University Staffs to report their R&D progress as well as contributions. The system went live from 2012 and was decommissioned on 2017.
  * Tools used: PHP, SQL, HTML, CSS and WAMP server.
  * Supervisor: [Dr Chin Ji Jian](https://mmuexpert.mmu.edu.my/jjchin)
  

Education
======
* M.S. in Information Technology, Multimedia University, 2020 (expected)
  * Thesis Topic: Extraction and Retrieval of Object Semantics for Long-Term Car Park Surveillance Videos

* B.Eng. in Electronics Majoring in Multimedia, Multimedia University, 2012
  * Thesis Topic: Speaker Voice Recognition

* Diploma in Technology, Mechatronics, Tunku Abdul Rahman College, 2008


Skills
======
* Framework/Tools: OpenCV, Docker, VMs, AWS (Basic EC2, S3), Git
* Languages: C++, JavaScript, Python, SQL, PHP, VB, HTML, CSS, MATLAB, PowerShell, Unix Shell Scripting
* Mainframe: COBOL, JCL, CA-7, z/OS
* ITIL Foundation knowledge, Incident & Crisis Management

Languages
======
* Spoken: English (Native), Chinese, Malay
* Written: English, Malay
  
Publications and Awards
======
<a id="publicationslist" href="https://scholar.google.com/citations?user=z8n5LTEAAAAJ&hl=en">Google Scholar</a>
  <ul>{% for post in site.publications %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

* 2018
  * International Invention, Innovation & Technology Exhibition (ITEX), Malaysia: Silver Medalist (ICT & Multimedia - University & Research Institute Category)
  * Malaysia Technology Expo (MTE): Invention & Innovation Category: Bronze Medalist
  * A.I Hackathon for Good: 2nd Runner Up
* 2017
  * Research Innovation Commercialisation & Entrepreneurship Showcase (RICES): 1'st Runner Up 
