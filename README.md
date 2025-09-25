# Simulation-of-the-impact-of-V2G-integration-on-the-power-grid

## AIM
To Simulate the impact of V2G integration on the power grid

## APPARATUS REQUIRED
•	MATLAB

## MATLAB CODING

% Simple V2G Simulation with 3 Output Graphs

clc; 

clear;

close all;


% Time base: 24 hours

t = 0:1:23; % hours

% Grid demand profile (MW)

demand = [60 55 50 55 65 80 100 120 110 95 85 80 75 70 80 95 110 130 140 130 110 90 75 65];

% Renewable generation (MW) – solar midday

renewable = [0 0 0 5 20 40 60 80 100 110 120 115 100 80 60 40 20 5 0 0 0 0 0 0];

% Baseline net load (without V2G)

netLoad_base = demand - renewable;

% EV fleet parameters

Charge_power = 20; % MW charging at night

Discharge_power = 20; % MW discharging at evening peak

% V2G strategy

V2G_action = zeros(size(t));

V2G_action(t>=0 & t<=6) = Charge_power; % charge at night

V2G_action(t>=17 & t<=21) = -Discharge_power; % discharge at peak

% Net load with V2G

netLoad_V2G = netLoad_base + V2G_action;

% Plot 1: Demand and Renewable

figure('Color','w','Position',[100 100 1000 600]);

subplot(3,1,1);

plot(t,demand,'-o','LineWidth',2);

hold on;

plot(t,renewable,'-s','LineWidth',2);

xlabel('Time (hours)');

ylabel('MW');

title('Demand and Renewable Profile');

legend('Demand','Renewable','Location','Best');

grid on;

% Plot 2: Net Load before vs after V2G

subplot(3,1,2);

plot(t,netLoad_base,'-o','LineWidth',2);

hold on;

plot(t,netLoad_V2G,'-s','LineWidth',2);

xlabel('Time (hours)');

ylabel('Net Load (MW)');

title('Net Load: Before vs After V2G');

legend('Without V2G','With V2G','Location','Best');

grid on;

% Plot 3: V2G Charging/Discharging Schedule

subplot(3,1,3);

bar(t,V2G_action,'FaceColor',[0.2 0.6 0.8]);

xlabel('Time (hours)');

ylabel('V2G Power (MW)');

title('V2G Charging (+) and Discharging (-) Schedule');

grid on;

% Use suptitle if sgtitle is not supported

suptitle('Impact of V2G Integration on Power Grid');


## OUTPUT

<img width="1246" height="845" alt="image" src="https://github.com/user-attachments/assets/094ac984-af5f-4566-9eb3-b7ead610f43c" />


## RESULT

Thus the impact of V2G integration on the power grid is simulated and verified using Matlab software
