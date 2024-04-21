% Get vibration input from the user
vibration_x = input('Enter vibration frequency (X-axis) of the car engine (in Hz): ');
vibration_y = input('Enter vibration frequency (Y-axis) of the car engine (in Hz): ');
vibration_z = input('Enter vibration frequency (Z-axis) of the car engine (in Hz): ');

% Define axes labels
axes = {'X-axis', 'Y-axis', 'Z-axis'};
frequencies = [vibration_x, vibration_y, vibration_z];

% Plot vibration levels for each axis separately
figure;
bar(frequencies);
xticks(1:numel(axes));
xticklabels(axes);
xlabel('Axis');
ylabel('Vibration Frequency (Hz)');
title('Car Engine Vibration Frequencies');
ylim([0, 3000]);  % Set the y-axis limit to 3000 Hz

% Calculate overall vibration frequency
overall_frequency = mean(frequencies);

% Prompt user to input thresholds
threshold_normal = input('Enter the threshold for Normal condition (in Hz): ');
threshold_good = input('Enter the threshold for Good condition (in Hz): ');

% Determine condition based on user-defined thresholds
if overall_frequency < threshold_normal
    condition = 'Normal';
elseif overall_frequency < threshold_good
    condition = 'Good';
else
    condition = 'Critical';
end

% Print overall vibration frequency and condition
fprintf('Overall Vibration Frequency: %.2f Hz\n', overall_frequency);
fprintf('Condition: %s\n', condition);
