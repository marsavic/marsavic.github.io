---
marp: true
---
<style>
  img[alt~='center'] {
    display: block;
    margin-left: auto;
    margin-right: auto;
  }
</style>

<!-- _backgroundColor: #222 -->
<!-- _color:           #eee -->
![bg left:44% width:112.5%](cover_tree.png)

Računarska grafika
# Proceduralno generisanje

---

# Proceduralno generisanje

![bg right:45%](1Cube.jpg)

Generisanje sadržaja (slika, tekstura, animacija, modela, scena, mapa, ...) korišćenjem algoritama (nasuprot "ručnom" dizajniranju)

Alati:
- Matematičke funkcije
- Generatori slučajnih brojeva
- Fraktali
- Koherentni šum
- Verovatnosne distribucije
- ...

---

# Igranje sa matematičkim funkcijama

|![h:360](f_XOR.png)|![h:360](f_WavesStanding.png)|![h:360](f_WaveCircular.png)|
|-|-|-|
|$v = x \text{ xor } y$|$v = \cos x \cos y$|$v = \cos r \cos phi$|

---

# Samosličnost

![bg right:59%](romanesco.webp) 

 U prirodi često manji delovi nečega liče na celinu čiji su deo.
  - reljef, obale
  - drveće, paprat, karfiol
  - nautilus
  - munje
  - ...

---

# Fraktali

![bg fit right:36%](Fractal_fern_explained.png)

- Matematički definisani objekti čiji delovi liče na objekat u celini.

|💻 `IFSTree`|💻 `IFSPoly`|
|-|-|
|![h:300](fractal_treebrain.png)|![h:300](fractal_poly.png)|

---

# Koherentni šum

![bg right:37.5%](perlin0.png)

Funkcija koja tačke preslikava u vrednosti:
- razlika vrednosti je mala za bliske tačke
- vrednosti nisu u korelaciji ako su tačke daleko

## Perlin noise
Ken Perlin, 1983.
- Želeo je da grafiku učini da izgleda malo manje "mašinski", a više "organski".
- Za šta je dobio oskara!

---

# Koherentni šum

![bg right:37.5%](perlin.png)

## Primena funkcija

💻 `PerlinNoiseDemo`

---

# Koherentni šum

## Kombinovanje

![bg right:54% vertical](perlin_combined.png)

💻 `PixelFunctions`

---

![bg right:54% vertical](perlin_combined.png)

# Frekvencija
- Učestalost "vizuelnih delova"
- Sitni delovi, mala rastojanja = velika frekvencija

# Amplituda
- Varijacija u intenzitetu između "vizuelnih delova"


---

## Fractal noise

Primena ideje samosličnosti na koherentni šum.

$$fractalNoise(p) = \sum_{k=1}^n amplitude_k \cdot noise_k(frequency_k \cdot p)$$

💻 `Terrain`

![w:218](map1.png) ![w:218](map2.png) ![w:218](map3.png) ![w:218](map4.png) ![w:218](map5.png)

---

![bg](RecursiveCentaur.jpg)
