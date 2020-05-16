![image in tradingview](https://i.imgur.com/2qBeWhP.png)


study("Extreme Rates of Buy vs Sell",overlay=false)

slope(a,b)=>(linreg(a,b,0)-linreg(a,b,0)[b])/b
norm(a,b,c)=>c*(a-lowest(a,b))/(highest(a,b)-lowest(a,b))
zs(a,b)=>(a-linreg(a,b,0))/stdev(a,b)
dx(a,b)=>(a-b)/((a+b)/2)

P=500
N1 = 200
Smooth=50


c=input(close)
o=input(open)

LCO=linreg(dx(c,open),P,0)

SLCO=linreg(linreg(LCO,Smooth/5,0),Smooth*2,0)*500


Sm = linreg(zs(LCO,N1),Smooth/5,0)/2
Vm = linreg(SLCO,Smooth,0)

HL=2.5
ML=0
LL=-2.5


plot(Sm, color=Sm>ML and Sm<HL?gray:Sm<ML and Sm>LL?gray:Sm>HL?white:Sm<LL?white:na, style=histogram)
plot(Vm, color=white, style=line)
plot(SLCO, color=orange, style=line,linewidth=2)



plot(ML, color=gray,style=line,linewidth=1)
plot(HL, color=gray,style=line,linewidth=1)
plot(LL, color=gray,style=line,linewidth=1)
