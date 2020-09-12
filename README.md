SynCalMa

Requirements: 
- Igor Pro 6.37
- Image Analysis Package SARFIA from IgorExchange: http://www.igorexchange.com/project/SARFIA

Procedure: 
1.	Load the images as a TIFF Stack. They should be accompanied by a Wave containing the acquisition time of each frame. The name of that wave should be: “Timewave_”+ “ImageName”,  where “ImageName” refers to the exact full name of the image loaded.
2.	Open the Image to be analyzed and keep it in front. 
3.	Execute CalciumImagingAnalysis(). This will open a Menu that will give the chance to load all the analysis parameters 

<img src=https://github.com/mjmoglie/SynCalMa/blob/master/IMAGENES/MENU.png width="700">
 
-	Photobleaching Correction: photobleaching will be corrected by fitting a straight line to the fluorescence signal obtained after averaging the signal of ROIs comprised from Photobleaching PRE- Photobleaching POST. If these present the same number, all ROIs will be averaged. It should be noted that these number should be higher than the total number of ROIs (#ROIs=360/Angle).
-	Analysis Output: select whether the result will be expressed as DeltaF/F0 or Delta F.
-	Automatic Center Determination: Determines the center of the cell by automatic thresholding followed by a particle analysis. The center will be the center of mass of the biggest particle detected. When this option is not selected, the center of the analysis has to be manually determined in “X center” and “Y center”. 
-	Smooth ROI traces: When selected, it will perform an additional smooth operation over the final fluorescence traces.
-	File Properties: 
		-	FILE: file number (only for anotation purpurses)
		-	VERSION: it will add this number at the end of the folder when the analysis was run more than one time (only for anotation purpurses)
	 -	TOTAL IMAGES: total number of frames to be analyzed
	 -	TOTAL Sweeps: total number of sweeps to be analyzed. It will only work if the number of images per sweep is constant throughout the file ( # images per sweep= total       images/total sweeps)
	 -	Stimulus Time (ms): This will allow to define when was the stimulus applied (based in the Timewave loaded with the image). It will determine the total number of frames that will be considered to calculate the baseline and where to start looking for the maximum fluorescence signal.
 
-	Location Properties: 
	 -	X-Center & Y-Center: Position of the center of the circunference that will be analyzed .  It will only be considered if “Automatic center determination” is not selected. 
	 -	External Radius: external radious of the circumference delimited. It is expressed in number of pixels. 
	 -	Angle: determines each ROI size (# ROIs= 360/Angle) 
 
<img src=https://github.com/mjmoglie/SynCalMa/blob/master/IMAGENES/Dise%C3%B1o%20ROI.png width="350">

-	Analysis parameters: 
 	-	Peak Criteria: indicates how many times higher than the standard deviation of the baseline signal the found peak must be (2-3)
 	-	Integral Criteria: threshold area under the curve of the fluorescence signal
 	-	Threshold Min & Threshold Max: relative fluorescence signal of the delimited signal that will be considered for analysis. A threshold of the normalized fluorescence signal  will be performed, obtaining a donut shaped mask

<img src=https://github.com/mjmoglie/ SynCalMa/blob/master/IMAGENES/Dise%C3%B1o%20ROI%20y%20MASCARA.png width="350">

-	Once the parameters were loaded, hit “Start Background-ROI Draw” and draw the ROI that will be used to obtain the background fluorescence signal. If no ROI is drawn, it will search for a previously created one.
-	Pres “Finish Background-ROI” to start the automated analysis. 
-	The output of the macro Will be stored in a folder with the following structure:  “IMAGE NAME+’_’+F_(# FILE)_V_(# VERSION)”. It will contain the following waves: 
  -	AutoROIAnalVar: string containing the analysis parameters.
		-	ROIMasksThreshold: Donut shaped mask obtained by setting Threshold Min & Threshold Max.
		-	ROIMasks: each layer of this wave contains the Mask generated for each ROI
  - ROIMasks_Back: ROI used to calculate the background fluorescence 
 	-	Back: Background fluorescence signal
  - BaselineF: two dimensional wave in which the baseline fluorescence signal of each ROI is indicated for each sweep.
  -	Amplitude: two dimensional wave in which the amplitude of the fluorescence signal obtained for each ROI in each sweep is depicted. Only those peaks that met the requirements set will show the value obtained. 
 -  PeakTime: Time in which the maximal peak was detected for each ROI in every sweep.
 - 	Integral_area: Area under the fluorescence signal curve obtained for each ROI in every sweep.
 - 	TauImaging: Exponential decay of the fluorescence signal for each ROI in every sweep.
 - 	ProbabilityROIS: Probability of getting a significant fluorescence signal in each of the ROIs obtained. 
 - 	ConcatenatedSweeps: This wave contains the processed fluorescence signal for each of the ROIs drawn. Each sweep will be normalized to its own baseline, photobleaching corrected and background subtracted.

<img src=https://github.com/mjmoglie/SynCalMa/blob/master/IMAGENES/CONCATENADO%20DE%20ROIS.png width="450">
