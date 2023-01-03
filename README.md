
## Homework Assignment #1
Notes:
- f = O(g) -> f(n) <= c*g(n)
- f = Ω(g) -> g = O(f)
- f = Θ(g) -> f = O(g) and f = Ω(g)
    
### #1
a) f = Θ(g)
- f(n) <= c*g(n), g(n) <= c*f(n), therefore f = Θ(g)

b) f = O(g)
- f(n) <= c*g(n), therefore f = O(g)

c) f = Θ(g)
- log(n)^2 = 2log(n)
- f(n) <= c*g(n), g(n) <= c*f(n), therefore f = Θ(g)

d) f = Θ(g)
- log(10n) = c+log(n)
- f(n) <= c*g(n), g(n) <= c*f(n), therefore f = Θ(g)

e) f = Θ(g)
- log(2n) <= c+log(n)
- log(3n) <= c+log(n)
- f(n) <= c*g(n), g(n) <= c*f(n), therefore f = Θ(g)

f) f = Θ(g)
- log(n^2) <= 2log(n)
- f(n) <= c*g(n), g(n) <= c*f(n), therefore f = Θ(g)

m) f = O(g)
- n*2^n < 3^n 
- f(n) <= c*g(n), therefore f = O(g)

### #2 
a) g = Θ(1) if c < 1
- if c < 1,  (1 - c^(n + 1))/(1 - c) converges to a constant
- then, 1 = c*g(n), g(n) = c*1, therefore, g(n) = Θ(1)

b) g = Θ(n) if c = 1
- if c = 1, all terms are 1, then, g(n) = n
- then, n <= c*g(n), g(n) <= c*n, therefore, g(n) = Θ(n)

c) g = Θ(c^n) if c > 1
- if c > 1, then (1 - c^(n + 1))/(1 - c)  converges to (c^n)
- then, c^n <= c*g(n), g(n) <= c*(c^n), therefore, g(n) = Θ(c^n)

### #3
a) 
```
if n  = 0, return 0
if n = 1, return 1
return f(n-1) + f(n-2)
```
b)
```
if n = 0, return 0
create an array f of length n+1
f[0] = 0, f[1] = 1
for i = 2 ... n:
	f[i] = f[i-1] + f[i-2]
return f[n]
```
## Homework Assignment #2

### #1.7
- assuming that the multiply function takes (m,n) as input, the multiply function creates  n rows because when n is divided by 2, it is shifted by 1.
- the length of each row is at most 2m, because it can be shifted only m times.
- therefore, the time complexity is O(m*n)

### #1.25
- using fast mod exp,
```
def  mod_exp(g, a, p):
	r = 1
	y = g % p
	while a > 0:
		if a & 1 == 1:
			r = (r * y) % p
		y = y**2 % p
		a >>= 1
	return r
```
- g^a mod p, g = 2, a = 125, p = 127
- first iteration
	 - r = 1
	- y = 2 % 127 = 2
	- a = 125 (odd)
		-  r = (1 * 2) % 127 = 2
	- y = (2^2) % 127 = 4
	- a = 125 >> 1 = 62
- second iteration
	- a = 62 (even)
	- r = 2 (from prev iteration)
	- y = 16 % 127 = 16
	- a = 62 >> 1 = 31
- third iteration
	- a = 31 (odd)
		- r = (2 * 16) % 127 = 32
	- y = (16^2) % 127 = 2
	- a = 31 >> 1 = 15
- fourth iteration
	- a = 15 (odd)
		- r = (32 * 2) % 127 = 64
	- y = (2^2) % 127 = 4
	- a = 15 >> 1 = 7
- fifth iteration
	- a = 7 (odd)
		- r = (64 * 4) % 127 = 2
	- y = (4^2) % 127 = 16
	- a = 7 >> 1 = 3
- sixth iteration
	- a = 3 (odd)
		- r = (2 * 16) % 127 = 32
	- y = (16^2) % 127 = 2
	- a = 3 >> 1 = 1
- seventh iteration 
	- a = 1 (odd)
		- r = (32 * 2) % 127 = 64
		- y = (2^2) % 127 = 4
		- a 1 >> 1 = 0

solution = r = 64

### # 3
- 2^21 mod 18

| iteration | x | y | N | z |
|--|--|--|--|--|
| 0 | 2 | 21 | 18 | 1 |
| 1 | 2 | 10 | 18 | 2 |
| 2 | 2 | 5 | 18 | 4 |
| 3 | 2 | 2 | 18 | 14 |
| 4 | 2 | 1 | 18 | 16 |
| 5 | 2 | 0 | 18 | 8 |

solution = z = 8
