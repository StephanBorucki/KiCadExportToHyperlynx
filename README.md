# KiCadExportToHyperlynx
KiCad Problem exporting PCB to Hyperlynx format

This describes a problem that occurs in KiCad when exporting a PCB to Hyperlynx format:

When exporting from KiCad 9.0.5, arcs are displayed incorrectly.

First, we will describe the changes that can be made to the Hyperlynx file using a text editor so that the arcs are displayed correctly.

I have created a simple example. 
KiCad7Test2.zip is the KiCad project created with KiCad 7.0.10 and KiCad7Test2.hyp is the exported Hyperlynx file. 

When I import these into CST, it looks like KiCad7ExportToCST_1.png and KiCad7ExportToCST_2.png.

KiCad9Test2.zip is the same project, which was opened with KiCad 9.0.5 and then saved.

KiCad9Test2.hyp is the Hyperlynx file exported from KiCad 9. When I import this into CST, it looks like KiCad9ExportToCST_1.png and KiCad9ExportToCST_2.png.

By comparing the export files, I found out where the error in the KiCad 9 export lies:
In Hyperlynx, an arc is specified as follows:
(ARC X1=….. Y1=….. X2=…. Y2=….. XC=….. YC=…. R=…. W=…. L=…)
X1 and Y1 specify the starting point of the arc, and X2 and Y2 specify the end point. If I swap the starting and end points, the arcs are displayed correctly in CST. 

This is shown again in KiCad9ExportToCST_changed_1.png and KiCad9ExportToCST_changed_2.png.

I have corrected this in KiCad9Test2_changed.hyp.
