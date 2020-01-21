---
layout: post
title: Cours de climatisation
---

Le principe de la climatisation consiste à enlever de la chaleur d'un endroit vers un autre.  La combustion du soufre dans une allumette se fait à 200o F, cependant, cela n'affecte pas la température de la salle à cause de sa masse qui est faible.

On a remarqué qu'en fournissant de la chaleur 1a un corps, on augmente l'activité moléculaire au niveau de corps.  De même en y retirant de la chaleur, on augmente l'attraction des molécules au niveau du corps.  Un corps à 0o C ne degage plus de la chaleur

Les échelles de température:
1- le kelvin (k) utilisé surtout en europe
2- Le degré Rankine (oR) utilisé par les Anglo-Sazons
3- Le degré Celsius
4- Le degré Farenheit

La détermination du 0o C est faite à partir du point triple où l'eau se trouve à la fois à l'état solide, liquide, gazeux ou vapeur à la pression atmosphérique

**Expérience de Toricelli**

760 mm de Hg
29 mm 92 de Hg
14.696 psi (pounds pers square inch) ou lb/Po 2
1 atm ou 101.33 kPa

Sur le mont Everest à l'Himalaya (8880 m) la pression atmosphérique est de 8.882 psi.  La pression est plus basse
Pabsolue = Pmanométrique + Patm


# Finite differences for the 2D heat equation


Implementation of a simple numerical schemes for the heat equation.



**<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;u}{\partial&space;t}=\alpha&space;\left(\frac{\partial^2&space;u}{\partial&space;x^2&space;}+\frac{\partial^2&space;u}{\partial&space;y^2&space;}\right)."/>**



Applying the second-order centered differences to approximate the spatial derivatives,



<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;u}{\partial&space;t}=\alpha&space;\left(\frac{u(i-1,j)-2u(i,j)+u(i+1,j)}{\Delta&space;x^2&space;}+\frac{u(i,j-1)-2u(i,j)+u(i,j+1)}{\Delta&space;y^2&space;}\right)."/>



Neumann boundary condition is employed for no-heat flux, thus please note that the grid location is staggered. Once the right hand side is obtained, the equation can be solved by the ODE suite. Here we use ode15s. Copyright 2015-2016 The MathWorks, Inc.


<img src="/assets/pictures/self_500x500.jpg" alt="Self" style="width: 300px;"/>

![image_0.png](SimpleHeatEquation_images/image_0.png)


# Problem Setup
```matlab
N = 50; % Number of grid in x,y-direction
L = 4*pi; % Domain size

% Grid point
x = linspace(0,L,N);
y = linspace(0,L,N);
% Make it staggered.
x = (x(1:end-1)+x(2:end))/2;
y = (y(1:end-1)+y(2:end))/2;
[X,Y] = meshgrid(x,y);
```
# Initial Condition
```matlab
% Let's use MATLAB logo.
% A variable u0 is defined at the center of each grid cell
% thus the number of grid point is N-1.
u0(:,:) = peaks(N-1);

% Plot it
handle_surf = surf(X,Y,u0);
handle_axes = gca;
handle_axes.ZLim = [-10,10];
handle_axes.CLim = [-10,10];
title('Evolution of MATLAB Logo by Heat equation');
```

![figure_0.png](SimpleHeatEquation_images/figure_0.png)

```matlab
```
# Simulation
```matlab
dx = x(2)-x(1); % spatial grid size
alpha = 2; % coefficient
tspan = linspace(0,1,40);
[t,u] = ode15s(@(t,x)getRHS(x,alpha,dx,N),tspan,u0(:));
```
# Visualize
```matlab
Tn = length(t);
u = reshape(u,Tn,N-1,N-1);

filename = 'heat.gif';
for ii=1:Tn
    Z = u(ii,:,:);
    Z = squeeze(Z);
    handle_surf.ZData = Z;
    drawnow;
    frame = getframe(gcf);
    im = frame2im(frame);
    [A,map] = rgb2ind(im,256);
    if ii==1
        imwrite(A,map,filename,'gif','LoopCount',Inf,'DelayTime',0.05);
    else
        imwrite(A,map,filename,'gif','WriteMode','append','DelayTime',0.05);
    end
end
```

![figure_1.png](SimpleHeatEquation_images/figure_1.png)

Copyright 2015-2016 The MathWorks, Inc.
[![View Simple Heat Equation solver on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://jp.mathworks.com/matlabcentral/fileexchange/59916-simple-heat-equation-solver)
