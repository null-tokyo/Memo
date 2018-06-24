# シェーダーに関するメモ

## 参考文献
* [The Book of Shaders](https://thebookofshaders.com/)



## 回転行列
```glsl
mat2 rotate2d(float _angle){
    return mat2(cos(_angle),-sin(_angle),
                sin(_angle),cos(_angle));
}
```

## 拡大縮小行列
```glsl
mat2 scale(vec2 _scale){
    return mat2(_scale.x,0.0,
                0.0,_scale.y);
}
```

## YUV から　RGB
```glsl
mat3 yuv2rgb = mat3(1.0, 0.0, 1.13983,
                    1.0, -0.39465, -0.58060,
                    1.0, 2.03211, 0.0);
```

## RGB から YUV
```glsl
mat3 rgb2yuv = mat3(0.2126, 0.7152, 0.0722,
                    -0.09991, -0.33609, 0.43600,
                    0.615, -0.5586, -0.05639);
```

## タイルパターン
```glsl
vec2 st = gl_FragCoord.xy/u_resolution.xy;
st *= 3.0; 
st = fract(st);
```

## ランダム
```glsl
float random (vec2 st) {
    return fract(sin(
        dot(st.xy, vec2(12.9898,78.233))
    ) * 43758.5453123);
}
```