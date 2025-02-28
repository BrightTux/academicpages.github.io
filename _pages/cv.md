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
clarence_han[at]hotmail[dot]com | <a href="https://github.com/BrightTux">https://github.com/BrightTux</a> <br>

<img align="center" alt="Python" width="22px" src="https://raw.githubusercontent.com/BrightTux/brighttux/master/icons/python-logo-generic.svg"/>
<img align="center" alt="Bash" width="22px" src="https://raw.githubusercontent.com/odb/official-bash-logo/master/assets/Logos/Icons/PNG/24x24.png"/>
<img align="center" alt="OpenCV" width="22px" src="https://raw.githubusercontent.com/BrightTux/brighttux/master/icons/487px-OpenCV_Logo_with_text_svg_version.svg.png"/>
<img align="center" alt="Tensorflow" width="22px" src="https://raw.githubusercontent.com/BrightTux/brighttux/master/icons/Tensorflow_logo.svg"/>
<img align="center" alt="Vim" width="22px" src="https://raw.githubusercontent.com/BrightTux/brighttux/master/icons/Vimlogo.svg" />
<img align="center" alt="Git" width="22px" src="https://raw.githubusercontent.com/BrightTux/brighttux/master/icons/512px-Git-logo.svg.png"/>
<img align="center" alt="Ansible" width="22px" src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Ansible_logo.svg/256px-Ansible_logo.svg.png"/> 
<img align="center" alt="Docker" width="22px" src="https://www.docker.com/wp-content/uploads/2022/03/vertical-logo-monochromatic.png"/>

</p>

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

}


  
</script>

Work experience
======
* May 2019 - Current: Maintenance & Testing Technician (Machine Learning)
  * Almex System Technology Asia (Almex-STA), MY 
  * Working remotely with a distributed team in HQ (Japan)
  * Tools used: Python, Docker, OpenCV, OpenVINO, Bash, Flask, MongoDB, Ansible, TensorFlow, PyQt
  * Projects: 
      * Invoice OCR: Research, proposal and POC Development.
        * Classification of documents using image features, Identification and extraction of desired texts
      * Person Re-Identification: Research, proposal and POC Development.
        * Labelling tools for internal testing, Performance Measurement, POC Demo at Hotel Fairs
        * Utilized pre-trained models from OpenVINO
      * Flir AX8 Thermal Camera API: Cowritten an API for thermal imaging purposes.
        * Face detection, Thermal correction using BlackBody device
      * Image Labeling Tool: Enhance existing [labeling tool](https://github.com/tzutalin/labelImg) to include MongoDB, automatic text detection & labeling (via OpenVINO). Automatic installation on multiple workstations via Ansible.
      * FCOS-Styled Datasets Generator: Converted existing datasets into Fully Convolutional One-Stage [(FCOS)](https://arxiv.org/abs/1904.01355) styled tfrecord dataset. 
      * Japanese Characters (Hiragana, Katagana, Kanji) Text OCR: Developed an system to generate pairs of binary mask and synthetic text as training data. This includes checking of available unique glyphs for each font and ensuring the generated text does not exceed the canvas upon various augmentation. 
      * SynthText-JPN (Japanese Text-on-Image Synthesis): Enhance existing [text generators](https://github.com/gachiemchiep/SynthText) to generated more text-in-image samples, the process includes generating new depth maps and new segmentation maps to generate own background images. 
      * Text Saliency Mapper: Developed saliency map generator to visualize and understand how well each text-characters are predicted. 

* Oct 2016 - April 2019: Research Scholar, Multimedia University, MY
  * Project: [SHERLOCK: Video Analytics for Multi-Camera Long-term Surveillance in Smart Cities.](https://www.youtube.com/watch?v=x_UJIOEBusw) 
  * Responsibilities: Developed an object semantics extraction and retrieval engine, includes data preprocessing, manual annotation. Attended Conferences, participated in bi-weekly reading group on latest research works in Computer Vision (Aesthetics, Medical, Micro Expressions, Image Recognition), exhibited and showcased the SHERLOCK Retrieval Engine. Published 2 conference papers; Obtained copyright for the retrieval engine.
  * Tools used: C++, OpenCV, Python, HTML, CSS and JavaScript
  * Supervisor: [Professor John See](https://researchportal.hw.ac.uk/en/persons/john-see)
  
* Nov 2018 - Feb 2019: Freelance Project
  * Project: Retail Store Analytics using Video Feed 
  * Developed a solution to extract customer's information such as location, clothing preference, entry/exit, visited aisle, payment counter, and etc using video feed. A simple deep learning model was trained to differentiate between male and female customers in AWS. The extracted JSON data is then sent to AWS for storage and postprocessing by the client.
  * Tools used: Raspberry Pi, OpenCV, Python, BASH, AWS and Docker. 

* Summer 2018 (Jun 2018 - Sept 2018): Research Intern, National Chung Cheng University, TW
  * Project: Vehicle Trajectory Classification using Machine Learning tools. Learned how to develop a simple network using Convolutional Neural Networks.
  * Tools used: Python, OpenCV, Keras and Tensorflow.
  * Supervisor: [Professor Wen-Nung, Lie](http://www.dsp.ee.ccu.edu.tw/wnlie/)
  
* Sept 2012 - Sept 2016: Application Management Service Delivery, Hewlett Packard Enterprise, MY
  * Provided 24/7 Service Delivery Support for a local bank’s (CIMB) core payment systems which includes IBG, Direct Debit, Autopay, Remittance as well as PTPTN system. While providing technical support, I would be liaising with the clients and IT operations team. Along with that, during the tenure I was also working on the CIMB 1P (1 Platform) project to develop extraction programs based on client’s requirements.
  * Tools used: (Mainframe Z/os) COBOL, JCL, CA-7, Unix, BASH, Visual Basic and SQL.
  * Supervisor: [Chor Pheng Khee](https://my.linkedin.com/in/chor-pheng-khee-652685133)

* Aug 2010 - Jan 2012: Research Assistant, Multimedia University, MY
  * Project: Content Management System (CMS) for Multimedia University Staffs to report their R&D progress as well as contributions. The system went live from 2012 and was decommissioned on 2017.
  * Tools used: PHP, SQL, HTML, CSS and WAMP server.
  * Supervisor: [Dr Chin Ji Jian](https://www.plymouth.ac.uk/staff/ji-jian-chin)
  

Education
======
* M.S. in Information Technology, Multimedia University, 2021
  * Thesis Topic: Extraction and Retrieval of Object Semantics for Long-Term Car Park Surveillance Videos

* B.Eng. in Electronics Majoring in Multimedia, Multimedia University, 2012
  * Thesis Topic: Speaker Voice Recognition

* Diploma in Technology, Mechatronics, Tunku Abdul Rahman College, 2008


Skills
======
* Framework/Tools: OpenCV, Docker, OpenVINO, Flask, VMs, AWS (Basic EC2, S3), Git
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
