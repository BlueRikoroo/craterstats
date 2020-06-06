
Installation and start-up
=========================

1. unzip the files to a single folder
2. Make sure you have IDL Virtual machine installed 
3. On Windows: double-click craterstats2.sav
   On linux: type idl -vm=craterstats2.sav

   -will report version error if installed VM is too old. Install the latest version (details on cratersoftware mailing list)


Default settings
================

Various default settings can be changed by altering the labelled values in 
craterstats2.ini (program behaviour) or default.plt (the initial blank plot)



Modification history
====================

2020-01-22 Recompiled with IDL 8.7.2 (compilation from 8.5 not working under 8.7)

2019-05-07 comments added for a0 definitions in functions.txt for Neukum 1983 and Neukum 2001 lunar PFs. a0 from PF not used by craterstats in any case.

2017-11-21 randomness analysis initialisation bug fixed

2017-11-14
 - Hartmann & Daubar 2016 Mars PF added
 - updated to allow Poisson calculation from .stat files
 - added Poisson data export

2017-07-20
 - removed premature 'staggered bins' feature from randomness analysis
 - JMARS import modified to read area from attribute_1 (previously attribute_0)

2017-03-19
 - corrected Hartmann 1984 equilibrium function (thanks to Kjartan Kinch and Caleb Fassett)
 - added n10, n20, n64 to summary file output
 - added Ceres chronology system - Hiesinger et al 2016

2016-11-10 fixed crash if .plt contains unknown PF

2016-10-12
 - add 's' suffix to isochron label for small font; 'a' to place above curve
 - extended user colour table up to max 100 colours
 - reversed plot order - first plot plots last, i.e. on top
 - added Marchi & O'Brien Vesta functions

2016-06-29 
 - added control dialog box for randomness analysis
 - refresh randomness analysis data when clicking checkbox
 - added 'natural' axis - "10m, 100m, 1km" etc

2016-06-10 
 - fix for manually entered ranges with Poisson causing stop
 - Standard lunar equilibrium function attributed to Trask (1966)

2016-05-19 better default plot names (taken from source data files)

2016-05-11

- added "Poisson pdf" as alternative to cumulative/differential fit. See Michael et al. (2016, Icarus, in press)
- added mu notation. See Michael et al. (2016, Icarus, in press)
- added shift-click-drag to adjust placement of age text
- added 'Export-Formatted age files...' - exports ages from current plots into .doc file formatted with super-/subscripts to copy/paste
- fixed significant figure display (e.g. show 3.0 instead of 3)
- tidied up functions.txt layout

- allow user-defined chronology functions (in functions_user.txt), e.g.

    n1_code={
        n1=3.22e-014*(exp(6.93*t)-1d)+0.0004875*t
        }

  Code may extend over multiple lines, and include variable declarations. The result must be returned in 'n1', e.g.

    n1_code={
        p=[3.22E-14,6.93E00,0,4.875E-04]
        n1=p[0]*(exp(p[1]*t)-1d)+p[3]*t
        }

  Code for the rate function can optionally be given, e.g.

    phi_code={
        phi=6.93*3.22e-014*exp(6.93*t)+0.0004875
        }

   If omitted, phi is calculated numerically from n1  


2015-09-11 changed chronology and rate plots to show curve for N(ref_diameter)

2015-08-19 added Mercury chronology systems - Le Feuvre and Wieczorek (2011) porous/non-porous (contributed by C. Fassett)

2015-07-15 

- fixed mouse-over y-value for rate plot (thanks to Caleb)
- added 'reference diameter' to legend panel. Allows alternative N(D) for fit legend items

2015-05-13 added N_event to .stat file output (needed to calculate errors when F includes fractional craters)

2015-02-25 fixed area display bug for Mac users

2015-02-20

- rearranged user interface to fit smaller screens
- added D_mean, N_diff, Err to .stat file output

2014-12-10 updated crater count file merge utility to account for fractional craters

2014-09-26 bug fix: calculation of last bin width for .stat file (assume equivalent ratio to previous bin)

2014-05-12 fixed no-binning bug 

2014-05-07 

- added hide all/show all buttons
- bug fix - randomness plot showing excess results

2014-04-28

- added new small body functions (Vesta, Phobos, Gaspra, Ida, Lutetia - Schemedemann et al (2014a,b))

- added support for JMARS crater counts

To use JMARS output, you need to export a crater list as a CSV file, and the bounding area as a shape file (which produces a set of 3 files). All of these files should share the same name, differing only by their extensions, e.g.

	cratercount.csv
	cratercount.polygon.shp
	cratercount.polygon.dbf
	cratercount.polygon.shx

and be placed in the same directory. In craterstats, when you select the csv file as a data source, the others will be picked up automatically. If you make a randomness analysis, craterstats will create an additional file with the extension _geom.txt which contains the *assumed* radial axes for Mars (not exported by JMARS). If you are using JMARS for a crater count not on Mars, you must edit these appropriately.

- modified structure of randomness_analysis output. All results are now placed in a new folder named as the source file with the extension _randomness. Previous output will need to be moved (or re-run)

- improved sizing of plot symbols


2014-03-31

- changed default age display to 2 significant figures (can revert with 3sf checkbox)
- changed selection of CF/PF pairs to allow only valid combinations ('chronology systems')
- added 'invert' to make white on black plot for presentations
- two extra plot colours for Mike Zanetti (you can edit their rgb values in craterstats2.ini)

2014-03-04 changed default .diam file format (see sample folder). Old formats still supported.

2014-01-08

- old plots no longer open with epochs showing
- axis range bug fix

2013-12-19

- added display of Mars epochs (see chronology/rate plots for interpretation of grey shades)
- fixed bug in eps text output (now editable in Illustrator)
- improved default print layout and font sizes

2013-05-16

- allow fractional craters in counts
- count impact 'events' for error calculations involving fractions (esp. buffered counts) (displayed as, e.g. "0.3 (of 2)")
- changed ".binned" input format (to allow event_frequency as well as frequency)

2013-02-27

- differential binning correction: affects ages calculated with 'differential fit' by up to ~5% (see Michael, 2013, LPSC abstract)
- added 'export crater map' for .scc files

2012-11-09 fixed mouse selection of ranges beyond data range: clip to range

2012-10-31 functions_user.txt moved to sample folder

2012-10-24 'Mars, Hartmann 2004 iteration' functions updated (introduced tabular PF definition)

2012-09-12 

- fixed cursor location info for view with randomness plot
- improved detection of changed data-source filenames           

2012-08-27 - added png_dimensions setting to .ini file

2012-08-24 

- fixed bug causing program closure when editing axis ranges
- added check for duplicate entries in .scc files

2012-06-06 added randomness analysis features (see Michael et al, 2011, Icarus)

2011-08-23 improved error handling for badly formed .diam files 

2011-08-05

- added chronology plot

2011-07-28

- added 'Sum .stat file' and 'Merge .diam file' functions to utility menu

2011-07-25

- improved error handling for badly formed .diam files

2011-06-09

- indent hidden plot titles

2011-05-09

- reorganisation of layout to better suit small screens

2011-03-22

- bug fixed for non-pseudo binned data on non-cumulative plots
- non-cumulative plots show fit line starting at d_mean rather than d_min

2011-02-02 New features in craterstats2

- display isochrons in cumulative, differential, R-plot and Hartmann presentations
- make fits to differential data as well as cumulative
- support for Hartmann-style piecewise production functions (Moon (1999) and Mars (2004) added)
- files created when saving is configurable (valid options - [png,txt,eps]) 
	e.g. export_on_save=[png,txt]
- support for alternative equilibrium functions
- may 'click and drag' in plot window to set diameter range

