# Barbwire

## Min. NR
```
analysis_len = input.int(150)
a = array.new<float>()

for i = 1 to analysis_len
    array.push(a, HR[i])

nr (_x, _arr) => array.indexof(_arr, array.min(_arr)) < _x

plotshape(nr(4, a), style=shape.labeldown, text="Min. NR", location=location.top, textcolor=color.white)
```
