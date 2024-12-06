% This file will read the whole data and convert it to 3 channel image. 
% Also resize the image to 227x227. and then stores the image in a new 
% folder. 
% Run this file only once if you haven't preprocessed the data once. 
clc 
clear all 
close all 
% Create Image data store. 
imds = imageDatastore('train', ... 
'IncludeSubfolders',true, ... 
'LabelSource','foldernames'); 
% Total number of images. 
numImages = numel(imds.Files); 
% Creating a folder for processed images. 
rootDir = 'ProcessedData'; 
mkdir(rootDir) 
% Total number of subfolders i.e classes. 
totFolders = numel(categories(imds.Labels)); 
foldersNames = categories(imds.Labels); 
for n = 1:totFolders 
mkdir(fullfile(rootDir, foldersNames{n})); 
end 
count = 1; 
for i = 1:numImages 
I = readimage(imds, i); 
% Check number of channels 
if size(I, 3) ~= 3 
% If not 3, convert to 3 channels (assuming grayscale) 
I = cat(3, I, I, I); 
end 
I = imresize(I, [227, 227]); 
subF = char(imds.Labels(i)); 
imageName = [sprintf('%d', count), '.tiff']; 
fullFileName = fullfile(rootDir, subF, imageName); 
imwrite(I, fullFileName); 
fprintf('Processed %0.2f percent records\n', (i / numImages) * 100); 
count = count + 1; 
end 
