# SynCalMa
Analysis of synaptic calcium signals in Cochlear Hair Cells

Requirements: 
- Igor Pro 6.37
- Image Analysis Package SARFIA from IgorExchange: http://www.igorexchange.com/project/SARFIA

Procedure: 
1.	Load the images as a TIFF Stack. They should be accompanied by a Wave containing the acquisition time of each frame. The name of that wave should be: “Timewave_”+ “ImageName”,  where “ImageName” refers to the exact full name of the image loaded.
2.	Open the Image to be analyzed and keep it in front. 
3.	Execute CalciumImagingAnalysis(). This will open a Menu that will give the chance to load all the analysis parameters 
<img src=https://github.com/mjmoglie/SynCalMa/blob/master/MENU.png width="700">
