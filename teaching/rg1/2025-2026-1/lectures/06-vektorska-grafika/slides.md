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
![bg left:44%](cover_vector_graphics.svg)

Računarska grafika
# Vektorska grafika

---

# Raster vs Vector

💻 `RasterVsVector`

![bg vertical right:43% w:480](raster-and-vector.png)
![bg w:480](Vector-vs-raster-1.jpg)

#### Rasterska grafika
- Sliku čini matrica piksela
- Memorija ~ veličina matrice
- Obrada kvari kvalitet
- Primene: fotografija

#### Vektorska grafika
- Sliku čine objekti opisani geometrijski
- Memorija ~ broj objekata
- Obrada očuvava kvalitet
- Primene: dizajn

---

# Klasa `Vector`

![bg right:36% w:360](Vector_addition.svg)

Immutable klasa koja predstavlja 2D vektor

|||
|-|-|
|`new Vector(x, y)`| Kreira vektor (x, y) |
|`Vector.ZERO`| Vektor (0, 0) |
|`inverse()`| Inverzni vektor |
|`add(o)`| Sabira sa vektorom o |
|`sub(o)`| Oduzima vektor o |
|`mul(k)`| Skalira faktorom k |
|`norm()`| Norma (dužina) |

---

# Klasa `Vector`

|||
|-|-|
|`Vector.polar(r, phi)`| Kreira vektor sa polarnim koordinatama (r, phi) |
|`angle()`| Ugao između x-ose i vektora
|`rotate(phi)`| Rotira za ugao phi |
|`dot(o)`| Skalarni proizvod |
|`cross(o)`| Vektorski proizvod |
|`perp()`| Normalni vektor (u pozitivnom smeru) |
|...||

---

# Klasa `View`

- Skup metoda za crtanje
- Koordinatni sistem:
  - (0, 0) je u centru, x raste na desno, y raste na gore, 1 = 1 piksel
  	- Možete promeniti kako želite korišćenjem transformacija
  - Uglovi se mere u okretima (turns)
  	- 1 okret = 360° = 2π
  	- Meri se od pozitivnog dela x-ose u pozitivnom smeru (suprotno od kazaljke na satu)

---

# Klasa `View` - Crtanje oblika

![bg right:25%](aabb.svg)

- Dva tipa metoda za crtanje oblika:
  - `stroke...` - crtaju obod oblika.
  - `fill...` - ispunjavaju oblik.
- Oblik se crta unutar _axis-aligned_ pravougaonika zadatog u parametrima:
  - `...(Vector p, Vector d)`
  	- Jedno teme u `p`, suprotno teme u `p`+`d`
  - `...Centered(Vector c, Vector r)`
  	- Centar u `c`, radijus-vektor `r`.
- Stanje: {stroke boja, fill boja, debljina linije, transformacija, ...}


---

# 💻 `SmileyFace`

![center height:560](SmileyFace0.svg)

---

# 💻 `SmileyFace`

![center height:560](SmileyFace1.svg)
