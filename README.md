# How to create a Time Series from Ocean Color data Using MATLAB

Welcome to my script
I would like to introduce you to how to create a time series of ocean color data.

>First read in a matrix file containing your latitude and longitude coordinates:

'''%% Load Data and Define Time Range
% Load lon and lat data from the .mat file
x = load('OC_coverageExample.mat');'''

>Then collect the data from:
>>https://oceandata.sci.gsfc.nasa.gov/api/file_search/
>Then organize the parameters you are interested in into separate folders within your main folder
>Next load each file in those folders as different directories:

'''% Load all files in the directories
filechl    = dir('chl/AQUA*chlor_a.9km.nc');
filepar    = dir('par/AQUA*.par.9km.nc');
filebbp443 = dir('bbp443/AQUA*.9km.nc');
filesst    = dir('sst/AQUA*.9km.nc');
filemld    = dir('MLD/mld*.hdf');'''

>Next you will need to define your time range, start time, end time, time steps:

'''% Define time range and calculate expected number of files
startDate  = datetime(2002,07,04);
endDate    = datetime(2021,12,31);
timeStep   = caldays(8);
timeVector = startDate:timeStep:endDate;
num_times  = length(timeVector);

% Convert the datetime vector to numeric values for polyfit
time_num = datetime(timeVector);'''
