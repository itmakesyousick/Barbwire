# Barbwire

## HR
```
f_HR (_open, _close) => 
    math.max(_open, _close) - math.min(_open, _close)

use_heikinashi = input.bool(true, 'Use Heikin-Ahi')

HR = f_HR(use_heikinashi ? hopen : open, use ? hclose : close)
```

## Min. ID
```
analysis_len = input.int(150)
a = array.new<float>()

for i = 1 to analysis_len
    array.push(a, HR[i])

f_id (_v, _arr) => array.indexof(_arr, array.min(_arr)) < _v

plotshape(f_id(1, a), style=shape.labeldown, text="Min. ID", location=location.top, size=size.tiny, textcolor=color.white, offset=-1)
```

## NR
```
v_std = array.stdev(a)

f_le (_v, _std, _malt) => _v <= _std * _malt

is_le030 = f_le(HR, v_std, 0.3 )
is_le005 = f_le(HR, v_std, 0.05)

plotshape(is_le030 ? 0 : na, style=shape.circle, color=color.purple, location=location.absolute, size=size.tiny, textcolor=color.white)
plotshape(is_le005 , style=shape.labelup, text="Sm. NR", color=color.purple, location=location.bottom, size=size.tiny, textcolor=color.white)
```
