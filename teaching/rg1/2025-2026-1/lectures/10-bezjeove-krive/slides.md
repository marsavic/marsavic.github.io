---
marp: true
---
<style>
	img[alt~='center'] {
		display: block;
		margin-left: auto;
		margin-right: auto;
	}
	section {
		padding-top: 30px;
		padding-bottom: 30px;
		display: flex;
	}
	section ul li,
	section ol li {
		margin-top: 0.1em;   /* or 0 */
		margin-bottom: 0.1em;
	}
</style>
<!-- _backgroundColor: #222 -->
<!-- _color:           #eee -->
![bg left:44%](Spline_(PSF).png)

Računarska grafika
# Bezjeove krive

---

![bg vertical right:34% w:440](vectore.png)

# Bezjeove krive (Bézier curves)

🚗 Nazvane po Pjeru Bezjeu (Pierre Bézier) koji ih je koristio 1960-tih za dizajn Renoovih automobila.

🚙 Međutim, razvio ih je Pol de Kastelžo (Paul de Casteljau) nekoliko godina ranije, radeći za Citroen.

### Primene
- Grafički dizajn
- 3D modeliranje  
- Fontovi
- Putanje u animaciji
- Animacione krive

---

# Parametarska kriva

![bg fit right:56.25%](parametric.svg)

Funkcija $p(t)$
- Kontinualna
- $p : \mathbb{R} \rightarrow \mathbb{R}^2$

Ograničavamo se na
$t \in [0,1]$

Radi kraćeg zapisa:
$s = 1-t$.

---

## Linearna Bezjeova kriva

<!-- Staviti animaciju za prezentaciju, samo jedan frame za pdf slajdove -->
![h:300](Bezier_1_big.gif)

$B_{P_0P_1}(t) = sP_0 + tP_1$

Duž između tačaka $P_0$ i $P_1$.

---

## Kvadratna Bezjeova kriva

<!-- Staviti animaciju za prezentaciju, samo jedan frame za pdf slajdove -->
![h:300](Bezier_2_big.gif)

$B_{P_0P_1P_2}(t) = sB_{P_0P_1}(t) + tB_{P_1P_2}(t)$
$\phantom{B_{P_0P_1P_2}(t)} = s(sP_0 + tP_1) + t(sP_1 + tP_2)$
$\phantom{B_{P_0P_1P_2}(t)} = s^2P_0 + 2stP_1 + t^2P_2$

Deo parabole između tačaka $P_0$ i $P_2$.

💻 `Bezier2_Quadratic`

---


## Kubna Bezjeova kriva

<!-- Staviti animaciju za prezentaciju, samo jedan frame za pdf slajdove -->
![h:300](Bezier_3_big.gif)![w:403](Bezier_basis.svg)

$B_{P_0P_1P_2P_3}(t) = sB_{P_0P_1P_2}(t) + tB_{P_1P_2P_3}(t)$
$\phantom{B_{P_0P_1P_2P_3}(t)} = s(s^2P_0 + 2stP_1 + t^2P_2) + t(s^2P_1 + 2stP_2 + t^2P_3)$
$\phantom{B_{P_0P_1P_2P_3}(t)} = s^3P_0 + 3s^2tP_1 + 3st^2P_2 + t^3P_3$


💻 `Bezier3_Cubic`

---

<!-- Staviti animaciju za prezentaciju, samo jedan frame za pdf slajdove -->
![bg vertical right:38% h:378](BezierCurve.gif)

## Bezjeova kriva $n$-tog reda

$B_{P_0}(t) = P_0$
$B_{P_0 \ldots P_n}(t) = sB_{P_0 \ldots P_{n-1}}(t) + tB_{P_1 \ldots P_n}(t)$
$B_{P_0 \ldots P_n} = \sum_{i=0}^n{ {n \choose i}s^{n-i}t^iP_i}$

### Osobine:

- Počinje u $P_0$ i završava se u $P_n$.
- $P_0P_1$ je tangenta na početak, a $P_{n-1}P_n$ na kraj krive.
- Prava linija akko su $P_0, \ldots, P_n$ kolinearne.
- Svaka Bezjeova kriva reda $n$ je takođe Bezjeova kriva reda $m$, za svako $m > n$.
- Neke jednostavne krive se ne mogu prikazati kao Bezjeove krive, npr. kružnica!

---

![bg right:45% w:500](Beziergon.svg)

# Složene Bezjeove krive
_(polybezier)_

Kriva koja se sastoji od više Bezjeovih krivi, tako da je kraj jedne početak sledeće.

"Glatka" je (prvi izvod je kontinualan) ako je svaka krajnja tačka kolinearna sa njoj dve susedne kontrolne tačke.

<!--
I prvi i drugi izvod su kontinualani ako važi prethodno, uz to da su rastojanja do dve susedne kontrolne tačake jednake.
Ovo sam "proverio" računski, deluje ok.
-->


---

# Putanje (klasa View)

`beginPath()`
Započinje kreiranje nove putanje.

`moveTo(p)`
Postavlja trenutnu poziciju na p, bez dodavanja novih delova putanje.

`lineTo(p)`
Dodaje duž od trenutne pozicije ka p. Nova trenutna pozicija je p.

`quadraticCurveTo(c, p)`
Dodaje kvadratnu Bezjeovu krivu od trenutne pozicije do pozicije p, koristeći kontrolnu tačku c. Nova trenutna pozicija je p.

`bezierCurveTo(c1, c2, p)`
Dodaje kubnu Bezjeovu krivu od trenutne pozicije do pozicije p, koristeći kontrolne tačke c1 i c2. Nova trenutna pozicija je p.

---

# Putanje (klasa View)

`closePath()`
Zatvara putanju, dodavajući duž koja spaja trenutnu poziciju sa početnom pozicijom.

`stroke()`
Iscrtava liniju po aktivnoj putanji.

`fill()`
Ispunjava površinu oivičenu aktivnom putanjom.
