clc 
clear all 
close all 
% Initialize Webcam 
cam = webcam; 
% Load Pretrained Model (Choose either Transfer Learning or Feature Extraction Approach) 
load('netTransfer.mat'); % For Transfer Learning Approach 
% or 
load('mainmma.mat'); % For Feature Extraction Approach 
% Main Loop 
while true 
% Capture Image from Webcam 
img = snapshot(cam); 
% Preprocess Image (Resize, Convert to Grayscale if needed, etc.) 
% Example: 
img = imresize(img, [227 227]); % Resize to fit AlexNet input size 
% Classify Image Emotion 
% For Transfer Learning Approach 
predictedLabel = classify(netTransfer, img); 
% or For Feature Extraction Approach 
features = activations(net, img, 'fc7', 'OutputAs', 'rows'); 
predictedLabel = predict(classifier, features); 
% Display Result 
imshow(img); 
title(['Predicted Emotion: ', char(predictedLabel)], 'FontSize', 14); 
drawnow; 
end 
% Clean up 
clear cam; 
