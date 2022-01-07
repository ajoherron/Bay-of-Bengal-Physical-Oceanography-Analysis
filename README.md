This notebook recreates work I did in Matlab over the summer of 2019 while working at the Lamont-Doherty Earth Institute. It's main purpose is too clean, organize, and create cross-sections of Argo float data from 2003-2018.

Primary cross-sections of interest with this dataset are: seasons, depth-slabs (50m increments up to 300m), and spatial areas (10 degree and 15 degree latitude bands, each +/-2 degrees).

The main purpose of this work is finding freshwater flow rates for various cross-sections. To do this, slopes are determined from a linear regression of freshwater as a function of distance. These slopes are then converted to freshwater flow rates using the formulas in section 4.

The conclusion of this work is that the central Bay of Bengal band is responsible for a majority of the freshwater export in the Bay of Bengal (using a conservative estimate of the horizontal mixing coefficient, where Kh = 1,000 m/s^2).
