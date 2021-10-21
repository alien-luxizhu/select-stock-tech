# select-stock-tech
通达信选股公式

# 1. 双响炮
```
涨停:=C>REF(C,1)*1.1-0.01 AND C=H;

周期:= BARSLAST(REF(涨停,1))+1;

HH:=C<REF(C, 周期)*1.06;

LL:=C>REF(O, 周期)*0.9;

强势:=LLV(C,周期-1)>REF(O,周期);

中间:=HH AND LL AND 强势;

REF(中间,1) AND 涨停 AND 周期<30;
```

