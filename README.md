# HAB-WrightState
Using Simulink for a high altitude balloon to maintain altitude within a certain range 
%% Preparing Arduino
% Connecting the arduino chip to Matlab
a=arduino('COM4');

%% Nichrome Wire on Timer

% configureDigitalPin takes pin 9 and will Unset pin 9 so it can be used
configureDigitalPin(a,D13,'output') 

% Create timer object 
t = timer('TimerFcn', 'disp(''Timer!'')','StartDelay',10);
start(t)
if t==(86400)
    % callback to turn on nichrome wire
    % The digitalwrite command tells pin#13 and pin#12 to turn on with the "1" value    
    writeDigitalPin(a,D13,1);
    % need to set a limit on the time the nichrome wire is on (maybe)
end

delete(t) % Always delete timer objects after using them.
