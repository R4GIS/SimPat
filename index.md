<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">

<head>
  <title>SIMPATC User's Manual - Overview</title>
  <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
  <link rel="shortcut icon" type="image/ico" href="./format/favicon.ico" />
  <link rel="stylesheet" type="text/css" href="./format/manual.css">
</head>

<body>

<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++ header ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<div id="header"><table><tr>
  <td id="left"><span id="title">SIMPATC User's Manual</span></td>
  <td id="right"><ul>
    <li><a href="index.html">Home</a></li>
    <li><a class="selected" href="overview.html">Overview</a></li>
    <li><a href="quick_start.html">Quick Start</a></li>
    <li><a href="input_files.html">Input Files</a></li>
    <li><a href="parameter_files.html">Parameter Files</a></li>
    <li><a href="tips_tricks.html">Tips &amp; Tricks</a></li>
    <li id="last"><a class="external" href="http://ekofisk.stanford.edu/SCRFweb/">SCRF</a></li>
  </ul></td>
</tr></table></div>
<!-- +++ /header +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->

<table id="main_layout"><tr>

<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++ topics ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<td class="topics">

<div class="topics"><span id="title">Topics</span>&nbsp;&nbsp;(&nbsp;All&nbsp;)<ul>
<li><a href="index.html">Home</a></li>
<li><a class="selected" href="overview.html">Overview</a></li>
<li><a href="quick_start.html">Quick Start</a></li>
<li><a href="input_files.html">Input Files</a></li>
<li><a href="parameter_files.html">Parameter Files</a></li>
<li><a href="group_general.html">Group: General</a></li>
<li><a href="group_realizations.html">Group: Realizations</a></li>
<li><a href="group_data.html">Group: Data</a></li>
<li><a href="group_run.html">Group: Run</a></li>
<li><a href="group_simulation.html">Group: Simulation</a></li>
<li><a href="tips_tricks.html">Tips &amp; Tricks</a></li>
</ul></div>

<div class="topics"><span id="title">Overview</span><ul>
<li><a href="#features">Features</a></li>
<li><a href="#limitations">Limitations</a></li>
<li><a href="#installation">Installation</a></li>
<li><a href="#usage">Usage</a></li>
</ul></div>

</td>
<!-- +++ /topics +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->

<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++ content +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<td id="content"><div id="content">
<h1>1. Overview</h1>

<p>SIMPATC is a command-line software developed to run SIMPAT simulations.
SIMPAT (SIMulation with PATterns) is a pattern-based stochastic geostatistical
simulation algorithm developed as a part of a <a class="external" href="http://www.burcarpat.com/thesis/">Ph.D. thesis</a>
from the <a class="external" href="http://ekofisk.stanford.edu/">Petroleum Engineering Dept.</a> of
<a class="external" href="http://www.stanford.edu">Stanford University</a> and the <a class="external" href="http://ekofisk.stanford.edu/SCRFweb/">SCRF</a>
(Stanford Center for Reservoir Forecasting) research group.</p>

<p>The software operates similar to SCRF's well-known <a class="external" href="http://ekofisk.stanford.edu/SCRFweb/GSLIB/">GSLIB</a>
(Geostatistical Software Library) tools. However, SIMPATC does not directly use
the conventional GSLIB parameter file format or the standard GSLIB input file
format. This manual explains how to use the binary distribution of SIMPATC
software (simpatc-bin) along with the parameter and the input file formats.
Note that, <b>the manual is not intended to serve as a manual for SIMPAT
itself; only for the command-line tool SIMPATC. It is assumed that the user is
familiar with the SIMPAT algorithm. For more information on the SIMPAT
algorithm, see the thesis <i><a class="external" href="http://www.burcarpat.com/thesis/">Sequential Simulation with Patterns</a></i>,
available online for download</b>.</p>


<h2 id="features">1.1. Features</h2>

<p>This version of SIMPATC has the following features (Chapter numbers refer to
the above <a class="external" href="http://www.burcarpat.com/thesis/">Ph.D. thesis</a>):</p>
<ul>
<li>Dual-template simulation (Section 4.2);</li>
<li>Multiple-band hard and soft training images (Partially in Section 5.4);</li>
<li>Hard data conditioning using dual templates (Section 6.1);</li>
<li>Concurrent region simulation (Section 7.1);</li>
<li>Structured path for hard data conditioning (Section 8.1.2).</li>
</ul>

<p>Additional features such as using proximity transforms to enhance simulation
results are to be handled external to SIMPATC. In other words, some of
the features explained in the thesis <i><a class="external" href="http://www.burcarpat.com/thesis/">Sequential Simulation with Patterns</a></i>
are not directly available and require using external software prior to running
SIMPATC.  Such software may be available for download from <a class="external" href="http://ekofisk.stanford.edu/SCRFweb/">SCRF</a>.
Majority of the times, you can put the external software and SIMPATC
in a batch or script file to use them together.  See the section on
<a href="parameter_files.html#includes">includes</a> for script support in SIMPATC.</p>

<h2 id="limitations">1.2. Limitations</h2>

<p>Note the following limitations of Release Candidate 3 only:</p>
<ul>

<li>Categorical variables (such as facies) must start from 0 and increment one by one, i.e. if you are running
a four facies simulation, the facies must be enumerated as 0, 1, 2 and 3;</li>

<li>Region codes must start from 0 and increment one by one, i.e. if you are running a four
region simulation, the region codes must be enumerated as 0, 1, 2 and 3.</li>

</ul>

<p>These limitations are planned to be removed with the next release of SIMPATC,
scheduled for May 2005.</p>


<h2 id="installation">1.3. Installation</h2>

<p>SIMPATC requires no installation and is distributed as a single executable
file. Copy the executable to a location within your path (or, to a location
where the parameter and data files are located) and you should be able to start
using the software immediately. If you choose to copy the executable to its own
location and update your path, it is also strongly encouraged to copy these
help files to the same location for future reference.  If you obtained SIMPATC
in a compressed archive file (ZIP, ARJ, etc.), you can simply copy the entire
content of the archive to a directory in your path, which ensures correct
installation.</p>


<h2 id="usage">1.4. Usage</h2>

<p>To run SIMPATC from the command prompt simply enter:</p>

<div class="kbd">$ simpatc</div>

<p>When used in this form, the software looks for a <a href="parameter.html">parameter file</a>
named "simpatc.par" in the current working directory. If such a file is found,
it is loaded, parsed and if found to be a valid SIMPATC parameter file, run by
the software. Alternatively, you can use the command:</p>

<div class="kbd">$ simpatc &lt;parameter-filename&gt;</div>

<p>For example, entering <kbd>simpatc myparfile.par</kbd> forces SIMPATC to
read the parameter file "myparfile.par" instead of the default "simpatc.par".
The file extension ".par" is not required (and can be anything else) but ".par"
is the extension traditionally used by <a class="external" href="http://ekofisk.stanford.edu/SCRFweb/GSLIB/">GSLIB</a> and thus you are encouraged to
follow this convention. In fact, parameter files are commonly referred to as
"PAR files" for this reason.</p>

<p>The software accepts two additional command-line options, namely "--help"
and "--version". When either of these options are given, SIMPATC outputs
the relevant information and immediately quits ignoring other arguments.</p>

</div></td>
<!-- +++ /content ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->

<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++ index +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<td class="index"><div class="index"><span id="title">Parameters</span><ul>

<li><a title="[ run ]" href="group_run.html#n_hard_bands">#_of_hard_bands</a></li>
<li><a title="[ run ]" href="group_run.html#n_multiple_grids">#_of_multiple_grids</a></li>
<li><a title="[ realizations ]" href="group_realizations.html#n_realizations">#_of_realizations</a></li>
<li><a title="[ data ]" href="group_data.html#n_regions">#_of_regions</a></li>
<li><a title="[ run ]" href="group_run.html#n_simulations">#_of_simulations</a></li>
<li><a title="[ run ]" href="group_run.html#n_soft_bands">#_of_soft_bands</a></li>
<li><a title="[ general ]" href="group_general.html#analysis_level">analysis_level</a></li>
<li><a title="[ realizations ]" href="group_realizations.html#dimensions">dimensions</a></li>
<li><a title="[ realizations ]" href="group_realizations.html#filename">filename</a></li>
<li><a title="[ data ]" href="group_data.html#hard_data">hard_data</a>+</li>
<li><a title="[ run ]" href="group_run.html#hard_template_dimensions">hard_template_dimensions</a></li>
<li><a title="[ simulation ]" href="group_simulation.html#hard_template_expansion">hard_template_expansion</a></li>
<li><a title="[ run ]" href="group_run.html#hard_training_image">hard_training_image</a>+</li>
<li><a title="[ data ]" href="group_data.html#init_data">init_data</a>+</li>
<li><a title="[ realizations ]" href="group_realizations.html#random_seed">random_seed</a></li>
<li><a title="[ data ]" href="group_data.html#regions">regions</a>+</li>
<li><a title="[ run ]" href="group_run.html#sampling_frequency">sampling_frequency</a></li>
<li><a title="[ general ]" href="group_general.html#simpatc_version">simpatc_version</a></li>
<li><a title="[ data ]" href="group_data.html#soft_data">soft_data</a>+</li>
<li><a title="[ run ]" href="group_run.html#soft_template_dimensions">soft_template_dimensions</a></li>
<li><a title="[ simulation ]" href="group_simulation.html#soft_template_expansion">soft_template_expansion</a></li>
<li><a title="[ run ]" href="group_run.html#soft_training_image">soft_training_image</a>+</li>
<li><a title="[ run ]" href="group_run.html#stop_after_multiple_grid">stop_after_multiple_grid</a></li>

</ul><br>+ indicates this parameter<br>has sub-parameters</div></td>
<!-- +++ /index ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->

</tr></table>

<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++ footer ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<div id="footer">Copyright © 2000 - 2005 by <a class="external" href="http://www.burcarpat.com/">Guven Burc ARPAT</a>
and The Board of Trustees of the <a class="external" href="http://ekofisk.stanford.edu/SCRFweb/">Leland Stanford Junior University</a>.&nbsp;
All rights reserved.</div>
<!-- +++ /footer +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->
<!-- +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ -->

</body>

</html>
