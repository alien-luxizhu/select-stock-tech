# select-stock-tech
通达信选股公式

# 1. 双响炮
```
涨停:=C>REF(C,1)*1.1-0.01 AND C=H;

周期:= BARSLAST(REF(涨停,1))+1;

HH:=C<REF(C, 周期)*1.15;

LL:=C>REF(O, 周期)*0.9;

强势:=LLV(C,周期-1)>REF(O,周期)*0.9;

中间:=HH AND LL AND 强势;

REF(中间,1) AND 涨停 AND 周期<30;
```

# 2. 涨停强势股
```
涨停:=C>REF(C,1)*1.1-0.01 AND C=H;
周期:= BARSLAST(涨停);
未连续涨停:=REF(C,周期+1)<REF(C,周期+2)*1.05;
多头排列:=EVERY(EMA(C,5)>EMA(C,10)*1.01,周期);
周期 >= 5 AND 周期<=30 AND 未连续涨停 AND 多头排列 AND C<REF(C,周期)*1.1;
```
