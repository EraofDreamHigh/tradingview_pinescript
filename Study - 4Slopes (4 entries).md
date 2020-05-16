![4Slopes to be used with 4 entries](https://i.imgur.com/ooYop27.png)

####### To be traded with 4 different entry points. Each slope has a different period

```

study("4S",overlay=false)
c=input(close)

p1=input(75,title="First Slope Period", type=integer, minval=2,maxval=600)
p2=input(150,title="Second Slope Period", type=integer, minval=2, maxval=600)
p3=input(300, title="Third Slope Period", type=integer, minval=2,maxval=600)
p4=input(375, title="Fourth Slope Period", type=integer, minval=2,maxval=600)

slope(a,b)=>(linreg(a,b,0)-linreg(a,b,0)[b])/b

s1 = slope(c,p1)
s2 = slope(c,p2)
s3 = slope(c,p3)
s4 = slope(c,p4)

plot(s1,color=s1>s1[1]?white:s1<s1[1]?orange:na,style=line,linewidth=1)
plot(s2,color=s2>s2[1]?white:s2<s2[1]?orange:na,style=line,linewidth=2)
plot(s3,color=s3>s3[1]?white:s3<s3[1]?orange:na,style=line,linewidth=3)
plot(s4,color=s4>s4[1]?white:s4<s4[1]?orange:na,style=line,linewidth=4)

```
