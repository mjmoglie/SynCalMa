Requirements: 
- Igor Pro 6.37
- Image Analysis Package SARFIA from IgorExchange: http://www.igorexchange.com/project/SARFIA

Procedure: 
1.	Load the images as a TIFF Stack. They should be accompanied by a Wave containing the acquisition time of each frame. The name of that wave should be: “Timewave_”+ “ImageName”,  where “ImageName” refers to the exact full name of the image loaded.
2.	Open the Image to be analyzed and keep it in front. 
3.	Execute CalciumImagingAnalysis(). This will open a Menu that will give the chance to load all the analysis parameters 

<img src=https://github.com/mjmoglie/SynCalMa/blob/master/IMAGENES/MENU.png width="700">
 
•	Photobleaching Correction: photobleaching will be corrected by fitting a straight line to the fluorescence signal obtained after averaging the signal of ROIs comprised from Photobleaching PRE- Photobleaching POST. If these present the same number, all ROIs will be averaged. It should be noted that these number should be higher than the total number of ROIs (#ROIs=360/Angle)
•	Analysis Output: select whether the result will be expressed as DeltaF/F0 or Delta F.
•	Automatic Center Determination: Determines the center of the cell by automatic thresholding followed by a particle analysis. The center will be the center of mass of the biggest particle detected. When this option is not selected, the center of the analysis has to be manually determined in “X center” and “Y center”. 
•	Smooth ROI traces: When selected, it will perform an additional smooth operation over the final fluorescence traces.
•	File Properties: 
i.	FILE: file number (only for anotation purpurses)
ii.	VERSION: it will add this number at the end of the folder when the analysis was run more than one time (only for anotation purpurses)
iii.	TOTAL IMAGES: total number of frames to be analyzed
iv.	TOTAL Sweeps: total number of sweeps to be analyzed. It will only work if the number of images per sweep is constant throughout the file ( # images per sweep= total images/total sweeps)
v.	Stimulus Time (ms): This will allow to define when was the stimulus applied (based in the Timewave loaded with the image). It will determine the total number of frames that will be considered to calculate the baseline and where to start looking for the maximum fluorescence signal.
•	Location Properties: 
i.	X-Center & Y-Center: Position of the center of the circunference that will be analyzed .  It will only be considered if “Automatic center determination” is not selected. 
ii.	External Radius: external radious of the circumference delimited. It is expressed in number of pixels. 
iii.	Angle: determines each ROI size (# ROIs= 360/Angle)

<img src=https://github.com/mjmoglie/SynCalMa/blob/master/IMAGENES/Dise%C3%B1o%20ROI.png width="350">

