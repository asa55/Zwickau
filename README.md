Zwickau
=======

Basic code for some of my matlab plots

%%%%% CODE SAMPLE 1 START%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%Simulation of Schott N-BK7 Glass Wedge beam dispersion
% Part #: G334483000

% Constants of Dispersion Formula
B1=1.03961212;B2=.231792344;B3=1.01046945;C1=.00600069867;C2=.0200179144;C3=103.560653;

% Valid Scope Domain
lambda=.4:.001:.8;

% n(lambda)
n=(B1*lambda.^2./(lambda.^2-C1)+B2*lambda.^2./(lambda.^2-C2)+B3*lambda.^2./(lambda.^2-C3)+1).^(.5);
figure(1)
plot(lambda,n)
title('Wavelength Dependence of n in N-BK7 Glass')
xlabel('wavelength (um)')
ylabel('n')

% Wedge Angle
alpha=3.52*pi/180;

% Mirror Angle measured with respect to the ray trajectory immediately exiting the beamsplitter
mirror_angle_rad = 4.127*pi/180

% (Ray Deflection Angle Formula from pp.11 of Saleh,Teich text 'Photonics')
% (2nd edition.                                                           )
% Incoming ray
incoming_radians=-alpha+asin(n*sin(alpha));
incoming_degrees=incoming_radians*180/pi;
figure(2)
plot(lambda,incoming_degrees)
title('Deflection of Incoming Rays')
xlabel('wavelength (um)')
ylabel('Angle (degrees)')

% Angle of reflection about the vector normal to the plane of the mirror
theta_r_radians = incoming_radians - mirror_angle_radians;
%%%%% CODE SAMPLE 1 END %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

