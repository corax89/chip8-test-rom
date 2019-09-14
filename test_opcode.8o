:alias x0 v8
:alias x1 v9
:alias x2 vA
:alias y	vB
: imageok
	0xEA 0xAC 0xAA 0xEA
: imagefalse
	0xCE 0xAA 0xAA 0xAE
: im0
	0xE0 0xA0 0xA0 0xE0
: im1
	0xC0 0x40 0x40 0xE0 
: im2
	0xE0 0x20 0xC0 0xE0
: im3
	0xE0 0x60 0x20 0xE0
: im4
	0xA0 0xE0 0x20 0x20
: im5
	0x60 0x40 0x20 0x40
: im6
	0xE0 0x80 0xE0 0xE0
: im7
	0xE0 0x20 0x20 0x20
: im8
	0xE0 0xE0 0xA0 0xE0
: im9
	0xE0 0xE0 0x20 0xE0
: imA
	0x40 0xA0 0xE0 0xA0
: imE
	0xE0 0xC0 0x80 0xE0
: imF
	0xE0 0x80 0xC0 0x80
: imX
	0xA0 0x40 0xA0 0xA0
  
:macro drawop A B {
i := A
sprite x0 y 4
i := B
sprite x1 y 4
}

: testAX
#test Ax
i := imageok
sprite x2 y 4
return

: test1x
i := imageok
sprite x2 y 4
jump endtest

: main
x0 := 1
x1 := 5
x2 := 10
y := 1
v5 := 42
v6 := 43
#test 3x
drawop im3 imX
i := imageok
if v6 != 43 then i := imagefalse
sprite x2 y 4
#test 4x
y := 6
drawop im4 imX
i := imagefalse
if v5 == 42 then i := imageok
sprite x2 y 4
#test 5x
y := 11
drawop im5 imX
i := imagefalse
if v5 != v6 then i := imageok
sprite x2 y 4
#test 7x
y := 16
drawop im7 imX
i := imagefalse
v6 += 255
if v6 == 42 then i := imageok
sprite x2 y 4
#test 9x
y := 21
drawop im9 imX
i := imagefalse
if v5 == v6 then i := imageok
sprite x2 y 4
#test AX
y := 26
drawop imA imX
testAX
#test 0E
x0 := 23
x1 := 27
x2 := 32
y := 1
drawop im0 imE
i := imageok
sprite x2 y 4
#test 8xy0
y := 6
drawop im8 im0
i := imagefalse
v7 := v5
if v7 == 42 then i := imageok
sprite x2 y 4
#test 8xy1
y := 11
drawop im8 im1
i := imagefalse
v7 := 42
v7 |= y
if v7 == 43 then i := imageok
sprite x2 y 4
#test 8xy2
y := 16
drawop im8 im2
i := imagefalse
v6 := 120
v7 := 31
v7 &= v6
if v7 == 24 then i := imageok
sprite x2 y 4
#test 8xy3
y := 21
drawop im8 im3
i := imagefalse
v6 := 120
v7 := 31
v7 ^= v6
if v7 == 103 then i := imageok
sprite x2 y 4
#test 8xy4
y := 26
drawop im8 im4
i := imagefalse
v6 := 140
v7 := 140
v7 += v6
if v7 == 24 then i := imageok
sprite x2 y 4
#test 8xy5
x0 := 44
x1 := 48
x2 := 52
y  := 1
drawop im8 im5
i := imagefalse
v6 := 140
v7 := 120
v7 -= v6
if v7 == 236 then i := imageok
sprite x2 y 4
#test 8xy6
y := 6
drawop im8 im6
i := imagefalse
v6 := 224
v6 <<= v6
if v6 == 192 then i := imageok
sprite x2 y 4
#test 8xyE
y := 11
drawop im8 imE
i := imagefalse
v6 := 15
v6 >>= v6
if v6 == 7 then i := imageok
sprite x2 y 4
#test Fx55,Fx65
y := 16
drawop imF im5
i := 1000
v0 := 0
v1 := 48
save v1
i := 1001
load v0
i := imagefalse
if v0 == 48 then i := imageok
sprite x2 y 4
#test Fx33
y := 21
drawop imF im3
i := 1000
v6 := 137
bcd v6
load v2
i := imageok
if v0 != 1 then i := imagefalse
if v1 != 3 then i := imagefalse
if v2 != 7 then i := imagefalse
sprite x2 y 4
#test 1x
y := 26
drawop im1 imX
jump test1x
: endtest
loop
again
