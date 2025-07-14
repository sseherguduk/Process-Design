The MATLAB code is designed to determine the optimal conversion value (X) for a given reaction rate (r) at various temperatures, based on a two-step reaction mechanism. 
A range of target reaction rates r is defined, spanning from extremely low to moderately high values.
For each value of r, and for temperatures between 300 K and 1000 K, the code:
Calculates reaction rate constants 𝑘1 and 𝑘2 using the Arrhenius equation.Iteratively searches for the combination of conversions X1 and X2 that minimizes the difference |f1-r|.
Stores the optimal conversion X=X1+X2 in a results matrix. 
The resulting conversion values are plotted as a function of temperature for each r.
Additionally, a series of red horizontal lines are plotted on the graph to visually define operational or target conversion zones.

Inputs:
A predefined list of target reaction rates 𝑟
A fixed temperature range T=300:20:1000 (in Kelvin)

Outputs:
A matrix 𝐴 containing corresponding temperature and optimal conversion values.
A graph showing Temperature (T) & Conversion (X) for each target 𝑟

# Process-Design
function r=C1(X) 
X=0; 
for r=[0 0.000001 0.000002 0.000003 0.000004 0.000005 0.000006 0.000007 0.000008 0.000009 0.00001 0.00002 0.00003 0.00004 0.00005 0.00006 0.00007 0.00008 0.00009 0.0001 0.0002 0.0003 0.0004 0.0005 0.0006 0.0007 0.0008 0.0009 0.001 0.002 0.003 0.004 0.005 0.006 0.007 0.008 0.009 0.01 0.02 0.03 0.04 0.05 0.06 0.07 0.08 0.09 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1 1.1 1.2 1.3 1.4 1.5 1.6 1.7 1.8 1.9 2 2.2 2.4 2.6 2.8 3 3.2 3.4 3.6 3.8 4 4.2 4.4 4.6 4.8 5 6 7 8]
    A=[];
    for T=300:20:1000
        k1=exp(-27000/(1.987*T)+19.837);
        k2=exp(-27900/(1.987*T)+19.23);
    s=999999;
    dogru_X=1;
        for X1=0:0.001:0.75;
            X2=X1*0.33;
            r1=k1*[(45.04-(45.04*(X1+X2)))/(945.84+(45.04*0.5*X2))*(189.16-45.04*(3*X1+7.5*X2))/(945.84+(45.04*0.5*X2))];
            r2=k2*[(45.04-(45.04*(X1+X2)))/(945.84+(45.04*0.5*X2))*(189.16-45.04*(3*X1+7.5*X2))/(945.84+(45.04*0.5*X2))];
            f1=r1+r2;
            if abs(f1-r)<s
                dogru_X=X1+X2;
                s=abs(f1-r);
            end
        end
       A=[A;T,dogru_X];
   end
   line(A(:,1),A(:,2));
   r
   A
end
hold on
hold on
kk=[623 723];
cc=[0 0.106];
plot(kk,cc,'r')
hold on
kk=[723 523];
cc=[0.106 0.106];
plot(kk,cc,'r')
hold on
kk=[523 723];
cc=[0.106 0.212];
plot(kk,cc,'r')
hold on
kk=[723 523];
cc=[0.212 0.212];
plot(kk,cc,'r')
hold on
kk=[523 723];
cc=[0.212 0.318];
plot(kk,cc,'r')
hold on
kk=[723 523];
cc=[0.318 0.318];
plot(kk,cc,'r')
hold on
kk=[523 723];
cc=[0.318 0.424];
plot(kk,cc,'r')
hold on
kk=[723 523];
cc=[0.424 0.424];
plot(kk,cc,'r')
hold on
kk=[523 723];
cc=[0.424 0.53];
plot(kk,cc,'r')
hold on
kk=[723 523];
cc=[0.53 0.53];
plot(kk,cc,'r')
hold on
kk=[523 723];
cc=[0.53 0.636];
plot(kk,cc,'r')
hold on
kk=[723 523];
cc=[0.636 0.636];
plot(kk,cc,'r')
hold on
kk=[523 723];
cc=[0.636 0.742];
plot(kk,cc,'r')
