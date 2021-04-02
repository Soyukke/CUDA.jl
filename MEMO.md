## 実行がうまく行く場合と失敗する場合

```julia
julia> x = rand(3)
3-element Vector{Float64}:
 0.6989937796473533
 0.2125750077973394
 0.6686848527807518

julia> y = cu(x)
3-element CuArray{Float32, 1}:
 0.6989938
 0.212575
 0.66868484

julia> y' * y
0.9809199f0

julia> y * y'
ERROR: 
signal (11): Segmentation fault
```

nvmlを使っているかinfoを出力するようにした
```julia
julia> x = rand(3)
3-element Vector{Float64}:
 0.4488165085119058
 0.5801561627394951
 0.1965187237180963

julia> y = cu(x)
3-element CuArray{Float32, 1}:
 0.4488165
 0.58015615
 0.19651872

julia> y' * y
0.576637f0

julia> y * y'
[ Info: NVML.jl: libnvidia-ml.so.1
ERROR: 
signal (11): Segmentation fault
```

nvmlを叩いている部分があり、そこで落ちている