---
share: "true"
---

# Modelování a syntéza

1. Pojem modelování signálu nebo systému aplikace? Vyjmenujte některé aplikace, ve kterých se používá.

**modelování signálu** - filtrace signálu s konstantním spektrem nebo spektrální výkonovou hustotou LTI filtrem s danou přenosovou funkcí pro získání signálu s danými parametry -> model reálného signálu

**aplikace** - syntéza řeči z textu, syntéza řeči po analýze a kompresi
     - předpověď řad (ekonomické projekce)
     - ověřování a optimalizace algoritmů (spektrální analýza)

---

2. Proces filtrace deterministického signálu LTI filtrem

 - časová oblast: konvoluce: $X[n] = v[n]\ast h[n] = \sum_{i= 0}^{\infty} x[i]\cdot h[n-i]$
 - spekrální oblast : násobení spektra s přenosovou funkcí
			 $X(z) = V(z) \cdot H(z)$ - Z transformace pouze pro deterministické signály

 - korelační oblast: konvoluce autokorelací $R_x[k] = R_{v} \ast R_{h}[k]$
				  pro $v = \delta[n] \rightarrow R_{v}= \delta [k] \rightarrow \boxed{R_{x}[k] = R_{h}[k]}$
 - podmínky vstupního signálu - konstantní spektrum -> $\delta[n]$
 - spektrum výstupního signálu : $Cx\left(e^{j\theta}\right)=\left|X\left(e^{j\theta}\right)\right|^2=\left|V\left(e^{j\theta}\right)\right|^2\left|H\left(e^{j\theta}\right)\right|^{2=}=\left|v\left[n\right]=\delta\left[n\right]\rightarrow \left|V\left(e^{j\theta}\right)\right|^2=1\right|=\left|H\left(e^{j\theta}\right)\right|^2$
		 -> spektrum je dané filtrem

 - vzájemná korelace   : $R_{xv[h]}= R_{v[h]} \ast h[h] = h[k]$
 - vzájemné spektrum :  $Cxv\left(e^{j\theta}\right)=X\left(e^{j\theta}\right)\cdot V^*\left(e^{j\theta}\right)= H\left(e^{j\theta}\right)\cdot V\left(e^{j\theta}\right)\cdot V^*\left(e^{j\theta}\right) = H\left(e^{j\theta}\right)$
 - -> také dané filtrem, ale obsahuje informaci o fázi
---

3. Popište proces filtrace náhodného signálu LTI filtrem v časové, korelační a spektrální oblasti. Uveďte podmínky pro vstupní signál. Vysvětlete, jak vypadá korelační funkce a výkonová spektrální hustota výstupního signálu. Vysvětlete, jak vypadá vzájemná korelace a vzájemná výkonová spektrální hustota.

- Náhodný signál -> nelze použít Z transformace ani Fourierova transformace
- Podmínky vstupu -> širokopásmový (bílý šum) -> konstantní spektrum, stacionární

-  Časová oblast : $X[k] = v[k] \ast h[k]$
- Spektrální oblast - spektrální výkonová hustota
- $Sx\left(e^{j\theta}\right)=\sigma_u^2\left|H\left(e^{j\theta}\right)\right|^2$
	- $\sigma_u$ směrodatná odchylka
     - $\sigma_u^2$ rozptyl signálu
- Vzájemné spektrum : $Sxu\left(e^{j\theta}\right)=\sigma_u^2H\left(e^{j\theta}\right)$

- Korelační oblast : $Rx\left[k\right]=\sigma_u^2Rk\left[k\right]$
		Vzájemná korelace : $Rxu\left[k\right]=\sigma_u^2k\left[k\right]$

---

4. Vysvětlete, co znamená pojem autoregresní (AR) proces (signál). Jak jej lze generovat? Nakreslete blokové schéma pro generování AR signálu a popište jej.

- Proces generovaný IIR filtrem bez dopředných vazeb -> $H(z) = \frac{1}{A(z)}$
 ![AR_diagram.svg](AR_diagram.svg)
- $v[n]$   - vstupní signál konstantním spektrem
- $H(z)$ - přenosová funkce modelujícího filtru
- $X[n]$ - modelovaný signál

---
5. AR spektrální hustota

$S_{ar}(e^{j\theta}) = \frac{\delta_e^2}{\left|A(e^{j\theta})^2\right|}$

- $\delta_e^2$ ... rozptyl chyby predikce
- $A(e^{j\theta})$ ...frekvenční charakteristika chybového filtru 

- tvar: ostrá maxima, kulatá údolí
 ![AR_spektralni_hustota.svg](AR_spektralni_hustota.svg)
- řád x maxima -> čím vyšší řád, tím více maxim -
				-  každý pól modeluje jednu špičku

---
6. AR vs Fouriere spektrum

 Výhoda AR - frekvenční rozlišení téměř nezávislé na délce signálu
 Nevýhoda - nezvládá přítomnost šumu

V AR spektru není vidět periodicita a šumový charakter - je vyhlazené

![Pasted image 20240118140144.png](Pasted%20image%2020240118140144.png)

---
7. Jak souvisí AR model s číslicovými filtry a číslicovou filtrací? Nakreslete příklad generování AR signálu s využitím příslušného číslicového filtru a načrtněte odpovídající tvar AR spektrální hustoty.

- AR proces lze modelovat číslicovým all-pole filtrem

![AR_model_digi_filtrce.svg](AR_model_digi_filtrce.svg)

>[!warning] Autoregresní model
>	Je to reprezentace typu náhodných procesů, používá se k popsání určitých časově proměnných procesů. Určuje, že výstupní proměnná lineárně závisí na svých vlastních předchozích hodnotách, a na stochastickém členu.

---

8. Předpokládejte, že máte signál, který odpovídá AR modelu. Jak zjistíte parametry tohoto modelu? Načrtněte blokové schéma analýzy a popište jej.

- Parametry modelu : Yule - Walkerovy rovnice -> koeficienty $A(z)$

analýza ![Analyza_AR_signalu.svg](Analyza_AR_signalu.svg)

- $A(z)$ ... přenosová funkce FIR chybového filtru
- $e[n]$ ... chybový signál (pro srovnání $A(z)$ bílý šum)
---

9. Co znamená termín lineární predikce? Co je chyba predikce? Co znamená termín dekorelace signálu a dekorelační (bělicí) filtr? Jak získáme jeho koeficienty?

- **Lineární predikce** = odhad dalšího vzorku signálu lineární kombinací předchozích vzorků
- **Chyba predikce** = rozdíl reálné hodnoty signálu a predikované hodnoty
- **Dekorelace** = proces filtrace signálu chybovým (dekorelačním/bělícím) filtrem -> chybový signál je bílý šum (= nekorelovaný)
- koeficienty získáme minimalizací chyby predikce - například Yule Walkerovy rovnice

---
10. Co jsou a k čemu slouží normální (Yuleovy-Walkerovy) rovnice?

$$
\begin{bmatrix}
R[0] & R[1] & \dots  & R[M-1] \\
R[1] & R[0] &  & \vdots \\
\vdots &  & \ddots & \vdots \\
R[M-1] & \dots & \dots & R[0]
\end{bmatrix}
\begin{bmatrix} A_1 \\ \vdots \\ \vdots \\ A_n \end{bmatrix}
=
\begin{bmatrix} R_x[1] \\ \vdots \\ \vdots \\ R[M] \end{bmatrix}
$$

- soustava rovnic pro určení koeficientů chybového filtru řádu M autokorelační metodou.

---
11. Popište postup vedoucí k určení AR spektrální hustoty. V čem se liší od spektrální hustoty získané Welchovou metodou z hlediska typického tvaru, spektrálního rozlišení, potřebné délky signálu a odolnosti vůči aditivnímu šumu?

1)  analýza chybovým filtrem : $e[n] = a_{n} \ast x[n]$ ... chybový signál
2) chyba predikce je bílý šum -> $S_{e}(e^{j\theta}) = \delta_e^2$
3) PSD : $S_{x}(e^{j\theta}) = \frac{\delta_{e^2}}{|A(e^{j\theta})|}$


|                       | Welch                                                | AR                                                   |
|-----------------------|------------------------------------------------------|------------------------------------------------------|
| Délka signálu         | Dlouhý                                               | Krátký                                               |
| Aditivní šum          | Zvládne                                              | Špatný tvar                                           |
| Vyhlazenost           | -                                                    | Vyhlazenější, nelze v něm vidět periodicita ani šumový charakter |
| Spektrální rozložení  | Závislé na délce signálu                             | Téměř nezávislé na délce signálu                       |

---
# Měření zpoždění mezi signály

12. Nedisperzní prostředí

- **Nedisperzní prostředí** - frekvenčně nezávislé
                      - konstantní útlum na všech frekvencích
					  - lineární fázová charakteristika -> konstantní skupinové zpoždění


- **Disperzní prostředí**    - frekvenčně závislé skupinové zpoždění a útlum


- **Nedisperzní prostředí** - spojitý čas $y(t) = h_{0} \cdot x(t-\tau_{0)} \rightarrow H(j\omega) = h_{0} \cdot e^{-j\tau_{0}\omega}$
				      - diskrétní čas $y[n] = h_{0} \cdot x[n-D] -> H(z) = h_{0}\cdot z^{D} ; D = \frac{\tau_0}{\tau_s}$
					  - $h_{0}\Rightarrow útlum$
					  - $\tau_{0}; D \Rightarrow delay$
					  -
					  -Modelování filtrem: ![Disperze_modelovani_filtrem.svg](Disperze_modelovani_filtrem.svg)
					  - Nekorelovaný aditivní bílý šum nemá vliv na vzájemnou korelaci mezi vstupem a výstupem $R_{yx(\tau)}= h_{0}\cdot R_{xx}(\tau - \tau_{0)}\rightarrow$ posunutá autokorelace

- **Disperzní prostředí**   - spojitý čas : $y(t) = h(t) \ast x(t) \rightarrow R_{yx}(\tau) = h(\tau) \ast R_{xx}(\tau)$
				    - diskrétní čas: $y[n] = h[n] \ast x[n]$
				    - obecný průběh frekvenční charakteristiky
				    - konvoluce s $h(t)$ mění tvar autokorelační funkce -> je třeba použít CPSD
				    - $$
S_{yx}(f) = \underbrace{\left| H(f) \right|  \cdot S_{xx}(f) e^{j\phi(f)} }_{\text{Frekvenčně závislá modulová a fázová charakteristika}}
$$

>[!info] Proč nás zpoždění zajímá?
>například k analýze odrazů - radar, porucha vláken

---

13. Jak měřit zpoždění

- **Vzájemná korelační funkce** - pouze pro ==nedisperzní prostředí== 
						  - vykazuje maximum pro dané zpoždění
						  - vícecestné šíření -> více maxim
							  - rozšířitelné pro širokopásmové signály
							  - úzká autokorelace
						 - aditivní šum nemá na výstupu vliv na měření


- **Vzájemná spektrální výkonová hustota** - disperzní i nedisperzní
								   - zpoždění je dané derivací fázové charakteristiky
								   - Podmínky : vyhlazená spektrální hustota
								   - problém s vícecestným šířením signálu - neproveditelná hřebenová struktura

---
14. Jak vypadá vzájemná korelace mezi signálem na vstupu a na výstupu LTI soustavy? Jaký je její vztah k autokorelaci vstupního signálu?

- obecně $R_{yx}(\tau) = h(\tau) \ast R_{xx} (\tau)$
- nedisperzní prostředí : $R_{yx}(\tau) = h_{0}\cdot R{xx} (\tau - \tau_0)$ - Zpožděná a utlumená
---
15. Určení zpoždění ze vzájemní korelace

- Zpoždění je určené polohou maxima vzájemné korelační funkce

![zpozdení_ze_vzajemne_korelace.svg](zpozden%C3%AD_ze_vzajemne_korelace.svg)       $$ \tau_{0}= \frac{D}{f_s}$$

---
16. Vliv šumu na výstupu na vzájemnou korelaci

- Nekorelovaný šum -> korelace se signálem nulová ->nemá vliv
---
17. Autospektrální hustoty

$S_{yx}=H(f)\cdot S_{xx}(f)$
$S_{yy}(f) = |H(f)|^{2} \cdot S_{xx}(f)$
---
18. CPSD vs korelace

**korelace** - pouze nedisperzní prostředí, zvládne vícecestné šíření, šum nemá vliv na měření

**CPSD** - i disperzní prostředí, problém s vícecestným šířením, je třeba počítat z nevyhlazených spekter

>[!question] Proč fáze?
>$x(t - t_{o)} \longleftrightarrow X(f) \cdot e^{(-j2\pi t_{0}f)}$ 
>-> zpoždění přidá lineární trend k fázi
>-> fáze (derivace) obsahuje informaci o posunu signálů

# Koherenční funkce

19. Definice koherenční funkce
$$
\gamma_{yx}(f) = \frac{S_{yx}(f)}{\sqrt{S_{xx}(f)\cdot S_{yy}(f)}}
$$
- Komplexní funkce
- Lze využít pro měření zpoždění signálu v disperzním prostředí
- Normovaná vzájemná společná hodnota odpovídá koeficientu 
- $MSC = |\gamma_{yx}(f)|^2$ … směrodatná odchylka pro měření spektrální výkonové hustoty -> důvěryhodnost -> detekce šumu, nelinearit -> kontrola přesnosti měření

- Odpovídá korelačnímu koeficientu $r_{gx}=\frac{\delta_{gx}}{\delta_{x}\cdot \delta_{y}}$, ale je komplexní a má hodnotu pro každou funkci

---
20. Jak se MSC liší od koherenční funkce?

- MSC neobsahuje informaci o fázi ($MSC = |\gamma|^2 \rightarrow$ je reálná)


>[!important] MSC
>MSC (Magnitude Squared Coherence) je statistika, která může být použita k prozkoumání mezi dvěma sety dat nebo signály. Používá k odhadu přenosu výkonu mezi vstupem a výstupem lineárního systému. Pokud jsou signály ergodické a funkce systému je lineární, lze ji použít k odhadu kauzality mezi vstupem a výstupem.

---
21. K čemu je MSC?

- Míra přesnosti měření frekvenční charakteristiky
- Detekce šumu a nelinearit
- Šum, nelinearita a chyby měření snižují MSC

22. Správný odhad MSC

1) spočítám $S_{xx}, S_{yy}$ : $Segmentace \rightarrow okno \rightarrow DFT \rightarrow ||^{2} \rightarrow průměrování$ 
2) spočítám vzájemnou hustotu $S_{yx}: Y \cdot X \rightarrow průměrování \rightarrow ||^2$
3) $\gamma = \frac{S_yx}{\sqrt{S_{xx}\cdot S_{yy}}}$ při nesprávném postupu vyjde jednotková
---
23. Vliv aditivního šumu na vstupu i výstupu u filtrace na MSC

Šum na výstupu:
![Vliv_aditivního_šumu.svg](Vliv_aditivn%C3%ADho_%C5%A1umu.svg)

-> šum na výstupu snižuje MSC
- Filtrace - nezmění MSC pokud nemá nuly na jednotkové kružnici -> hřebenová struktura

- Šum na vstupu má stejný vliv jako šum na výstupu -> snižuje MSC
![šum_filtrace_MSC.svg](%C5%A1um_filtrace_MSC.svg)
- měřitelné je x ne s

>[!warning] Aditivní šum
>Aditivní -> přičtený šum, většinou se myslí prostě AWGN (Additive White Gaussian Noise).
>Nekorelovaný bílý šum, definovaný rozptylem a spektrálním výkonem.

---
24. Lze koherenci použít pro odhad zpoždění?

- Ano - je to normovaná CPSD -> zpoždění je derivace fáze
---
# Kepstrální analýza

25. Superpozice, konvoluce a dekonvoluce

- superpozice -> pro lineární systémy -> odezva součtů = součet odezev
- zobecněný princip superpozice -> platí v nelineárních systémech
- mohou se měnit operace, například : $T\{x\} = e^{x};e^{x_{1}+x_{2}} = e^{x_1} \cdot e^{x_2}$
- **Konvoluce**![Lin_system.svg](Lin_system.svg)
$y[n] = x[n] \ast h[n] = \sum_{-\infty}^{\infty} x[i] \cdot h[n-i]$ 

- **Dekonvoluce** -> oddělení buzení od impulsové odezvy
- Při znalosti $x[n] \hspace{0.25cm} a \hspace{0.25cm} y[n]$ : $y[n] = x[n] \ast h[n]$
					-   $Y(z) = X(z) \cdot H(z) \Rightarrow H(z) = \frac{Y(z)}{X(z)}$
					- ==Výsledek je impulsová odezva systému==

>[!important] Kepstrální analýza
>Spektrum logaritmického spektra
 **Vlastnosti reálného kepstra:**
>- tím logaritmem nám přechází násobení na sčítání
>- periodická část je zatlumená 
>- cs = ifft(log(abs(fft(s)))) !!!
>- Podmínky: jeden musí být neperiodickej a nejakej se nejak opakovat
>
**Vlastnosti kepstra**:
>- Co je na vstupu v konovluci je v kepstru v součtu (díky logaritmu)
>- dá se rozdělit periodická a aperiodická část



---
26. Dekonvoluce pouze z výstupního signálu

- Ano lze -> kepstrální analýzou
	       -> podmínky: jeden signál je aperiodický a druhý se opakuje

---
27. K čemu je kepstrální analýza?

 - Používá se k dekonvoluci se znalostí pouze výstupního signálu, je nelineární a používá se ln a exp
---
28. Tři bloky pro kepstrální analýzu a rekonstrukci

1) Nelineární blok transformace D : $konvoluce \rightarrow součet$
2) Lineární blok $\rightarrow \text{liftrace} \rightarrow \text{oddělení signálů}$
3) $\text{Nelineární blok} \rightarrow \text{zpětná vazba transformace}D^{-1} \rightarrow \text{přechod zpět do časové oblasti} \rightarrow \text{inverzní Z transformace}$ 
---
29. Bloky analýzy při použití DFT

![Bloky_analyzy_pri_pouziti_dat.svg](Bloky_analyzy_pri_pouziti_dat.svg)

---
30. Bloky rekonstukce při použití DFT

![Rekonstukce_DFT.svg](Rekonstukce_DFT.svg)

---
31. Liftrace

- Váhování kepstra oknem -> oddělení aperiodické a opakující se části -> oddělení $h[n]$
---
32. Nízké a vysoké kvefrence

- Nízké kvefrence nesou informaci o aperiodickém signálu, vysoké o opakujícím se 
--> oddělení liftrací

![Liftrace.svg](Liftrace.svg)

---
33. Proč kepstrum dokáže odhalit slabý odraz

- Díky využití algoritmu -> zatlumení koeficientů s $\frac{1}{n}$ -> aperiodická část je dostatečně zatlumená a odraz je vidět
![Pasted image 20240119163155.png](Pasted%20image%2020240119163155.png)

---
34. Vztah spektra; logaritmického spektra, autokorelace a kepstra
![vztah_spektra_logspek_atd.svg](vztah_spektra_logspek_atd.svg)

- Autokorelace je zpětnou transformací výkonového spektra
- reálné kepstrum je zpětnou transformací logaritmického výkonového spektra

---
35. Alternativní výpočet kepstra

![alt_kepstrum_vypocet.svg](alt_kepstrum_vypocet.svg)

---
36. DFT vs. Kepstrum AR

- DFT kepstrum: konečné (IDFT) 

- AR -> nekonečné (Z transformace)
	- -> vyhlazené -> nenese informaci o periodicitě ani šumovém charakteru
---

37. Aplikace kepstrální analýzy

- Parametrizace signálu -> rozpoznávání řeči
- Měření zkreslení -> kepstrální vzdálenost
- analýza odrazů
---

38. Metrika

- Vlastnosti  -> $d(x;y) \geq 0 ... \text{vždy nulová nebo kladná}$
		    -> $d(x;y) = d(x;y)... \text{symetrie}$
		    -> $d(x;y) = 0 \leftrightarrow x=y ... \text{nulová jen když se}  \hspace{0.25cm}x=y$
		    -> $d(x;y) \leq d(x;y) + d(y;x) ... \text{trojúhelníková nerovnost}$
		    
![Metrika.svg](Metrika.svg)

- Typy metrik a integrálních metrik
	-  -> eukleidovská součtová; čebyševova
	- -> integrální metrika -> spektrální vzdálenost
![Pasted image 20240120112712.png](Pasted%20image%2020240120112712.png)

---
39. Spektrální vzdálenost

- Plocha uzavřená mezi $ln(S_1)$ a $ln(S_2)$ viz 38 -> udává rozdílnost spektrálních hustot
- dá se spočítat pomocí kepstrálních koeficientů -> kepstrální koeficienty jsou rozvoj $ln(S)$ do řady (Laurentovy/Taylorovy) =>integrální metrika přejde v Eukleidovskou.

---
40. Výpočet kepstrální vzdálenosti pro konečný počet koeficientů

$d_{2}= \sqrt{\underbrace{(C_{x}[0] - C_{y}[0])^{2}}_\text{Rozdíl energií} + \underbrace{2\sum_{i = 1}^{L}(C_{x}[i] - C_y[i])^2}_\text{rozdíl tvarů}}$

---
41. Vlastnosti a význam kepstrálních vzdáleností

- Eukleidovská vzdálenost v prostoru kepstrálních koeficientů
- plocha vyjadřující rozdíl PSD signálů

$(C_{x}[0])^{2}\text{odpovídá energii} = (plocha \hspace{0.25cm}S_x)^2$

- další koeficienty porovnávají tvar PSD -> čím více koeficientů, tím více detailů

>[!important] Klobouk (hat) 
> $\hat{x}$   -> klobouk zde představuje odhad. Například po filtraci signálu Wienerovým filtrem dostaneme odhad signálu.
# Ortogonální transformace

42. Ortogonální transformace

- transformace jejíž bázové funkce mají nulový společný výkon 
- -> ==jsou ortogonální==

- Poznáme z maticového zápisu : $T \cdot T^{H} = I \rightarrow T^{H} = T^{-1}$
- $I ... \text{jednotková matice}$
- $T ... \text{matice transformace}$
- $H ... \text{Hermitovská transpozice - transpozice + komplexní sdružení}$

---
43. Je DFT ortogonální?

- ano je, maticový zápis: $X = W \cdot x$
- $x ... \text{vstupní signál}$
- $X ...\text{spektrum}$
- $W ... \text{matice transpozice}$

$$x = \begin{bmatrix} X[0] \\ X[1] \\ \vdots \\ X[n] \end{bmatrix}
x = \begin{bmatrix} X[0] \\ X[1] \\ \vdots \\ X[n] \end{bmatrix}
W= \begin{bmatrix}
W^{nk} & \dots & \dots  & W^{nk} \\
\vdots &  &  & \vdots \\
\vdots &  &  & \vdots \\
W^{nk} & \dots & \dots & W^{nk}
\end{bmatrix}
$$
$$w = e^{-j\frac{2\pi}{N}} \rightarrow w^{nk} \rightarrow e^{-j\frac{2\pi}{N}kn}$$

---
44. Pro jaký typ signálu lze ze spojité  FT získat CT

 - Pro kauzální signál -> zrcadlení nebo sudý signál

---
45. Úpravy posloupnosti pro DCT-1 a DCT-2

![Posloupnosti_pro_dct1adct2.svg](Posloupnosti_pro_dct1adct2.svg)

>[!important] DCT-1 vs DCT-2
>TODO

---
46. Vztah DCT a DFT

- **DCT-1 a DFT** -> spektrum je stejné jako DFT spektrum signálu rozšířeného do $2N-2$ posloupnosti jako $k = 0; ...; N-1$ 


- **DCT-2 a DFT - DCT2** -> spektrum je stejné jako DFT spektrum signálu rozšířeného do $2N$ posloupnosti pro $k = 0;...; N-1$

---
47. Další ortogonální transformace

- **KLT** - Korkumenova - Leonova transformace
- **DWT** - Diskrétní vlnková transformace
---
# Metoda rozkladu na hlavní komponenty/složky - PCA; EVD; KLT

48. Princip rozkladu na hlavní komponenty

- Hledání bázových vektorů, ze kterých se signál skládá
	- vlastní vektory -> směry největšího rozptylu 
	- vlastní čísla      -> rozptyly ve směru vlastních vektorů 
	- ==> průmět dat ve směru hlavního vektoru

>[!important] PCA
>Principal component analysis (Metoda rozkladu na hlavní komponenty)
>Statistická metoda
>TODO


---
49. Matice PCA

- Pracuje s korelační maticí $C_{x}= X \cdot X^{T}   X ... \text{sloupce jsou realizace (jednotlivá měření)}$
- hledáme její vlastní čísla a vlastní vektory (rozptyl dat ve směru vlastích vektorů <= vlastní čísla; bázové funkce <= vlastní vektory)


- na diagonále je rozptyl dat, mimo diagonálu je vzájemná energie dvojic signálů

![rozptyl_dat.svg](rozptyl_dat.svg)
- Nekorelovaná data -> prvky pouze na diagonále
---
50. Na co se rozkládá korelační matice

 - $C_{x}= V \cdot D \cdot V^T$
	 - $D ...\text{diagonální matice}$
	 - $V ... \text{matice vlastních vektorů}\rightarrow \text{směr nejvetšího rozptylu dat}$
---
51. Co představují vlastní čísla a vlastní vektory

- vlastní vektory -> směr největšího rozptylu dat
- vlastní čísla -> rozptyl dat ve směru vlastních vektorů

---
52. Kdy PCA selže

- Když jsou vlastní čísla stejně velká     -> nelze nalézt směr největšího rozptylu
								-> rozmístění po kružnici
								-> lze to napravit, existují na to nelineární transformace

![PCA.svg](PCA.svg) -> rozmístění po kružnici

---
53. Jak PCA použít pro ztrátovou kompresi 1-D signálu

- Stacionární data -> segmentace -> datová matice -> korelační matice > V, D -> $y = X \cdot V^{'}$ a vezmu pouze část matice vlastních vektorů, která odpovídá největším vlastním číslům

---
54. DCT a DFT pro ztrátovou kompresi

- Jdou použít
- rozdíl: 
	- DCT a DFT mají signálově nezávislou bázi
	- KLT má signálově závislou bázi -> největší stupeň komprese
	- DCT má vyšší stupeň komprese než DFT
---
56. Podle čeho se stanovuje počet složek pro ztrátovou kompresi

	- Vybereme nejvýznamnější složky jednotlivých spekter, ostatní se nulují
	- DCT má většinou přiřazené hodnoty podle velikosti
	- počet se vybírá, tak aby zrekonstruovaný signál měl co nejpodobnější výkon
	- KLT potřebuje nejméně, vždy seřazené
	- DCT o něco víc, většinou seřazeny
	- DFT potřebuje nejvíc a nejsou seřazeny
---

57. Co představují hodnoty DFT spektra

- **Modulové spektrum** -> podobnost signálu s bázovou funkcí o dané frekvenci.
- **Výkonové spektrum** -> rozptyl signálu v daném frekvenčním pásmu.
- **Komprese** -> největší hodnoty ve spektru, jak velké a kde, zbytek nuluju.
- **Rekonstrukce** -> postavím spektrum z nenulových čar a IDFT

---
58. Co představují hodnoty DCT spektra

- totéž ale s cosíny, koprese stejné jako DFT

59. Co u PCA  představují vlastní čísla

- Rozptyly signálu ve směrech vlastních vektorů, komprese zase stejná akorát matice rozkladu je signálově závislá

>[!warning] Signálová závislost
>TODO

---
# Modely zkreslení signálu a možnosti jeho rekonstrukce: Inverzní filtrace


60. Model zkreslení aditivním šumem
![Zkresleni_aditivnim_sumem.svg](Zkresleni_aditivnim_sumem.svg) 
$X[n] = s[n] + u[n]$
$R_{x}[k] = R_{s}[k] + R_{u}[k]$
$S_{x}(e^{j\theta})= S_{s}(e^{j\theta}) + S_{u}(e^{j\theta})$

---
61. Model zkreslení konvolučním šumem

![Zkreslení_konvolucnim_sumem.svg](Zkreslen%C3%AD_konvolucnim_sumem.svg)
$X[n] = s[n] \ast h[n]$
$R_{x}[k] = R_{s}[k] \ast R_{h}[k]$
$S_{x}(e^{j\theta}) = S_s(e^{j\theta}) \cdot |H(e^{j\theta})|^2$

---
62. Model zkreslení aditivním a konvolučním šumem

![Zkreslení_aditivním_a_konvolucnim_sumem.svg](Zkreslen%C3%AD_aditivn%C3%ADm_a_konvolucnim_sumem.svg)
$X[n] = s[n] \ast h[n] + u[n]$
$R_{x}[k] = R_{s}[k] \ast R_{h}[k] + R_{u}[k]$
$S_{x}(e^{j\theta}) = S_s(e^{j\theta}) \cdot |H(e^{j\theta})|^{2} + S_{u}(e^{j\theta})$

---
63. Potlačení aditivního šumu

- **Úzkopásmový** -> pásmová zádrž (signál je širokopásmový oproti šumu)
- **Širokopásmový** -> odhad PSD šumu z šumových segmentů -> spektrální odčítání
				- (Nebo odhadnu korelaci šumu a odečtu od korelace signálů)
- signál je úzkopásmový oproti šumu -> pásmová propust

---

64. Potlačení konvolučního šumu

- **Prostá dekonvoluce** (filtrace inverzním filtrem)
- Wienerova filtrace
- prostá inverze - nulování "slabých" spektrálních čar
- adaptivní algoritmy

---
65. Prostá inverzní filtrace

![Prosta_inv_filtrace.svg](Prosta_inv_filtrace.svg)
- Filtruji signál filtrem s inverzní filtrační charakteristikou
- H musí mít minimální fázi -> nuly pouze uvnitř jednotkové kružnice -> $\frac{1}{H(z)}$ je pak stabilní
- Pokud je na výstupu $H(z)$ přítomen aditivní šum, pak je nepoužitelná -> šumová katastrofa!

---
66. Šumová katastrofa

![sumova_katastrofa.svg](sumova_katastrofa.svg)

$X[n] = s[n] \ast h[n] + u_{n} \rightarrow S_{xs}= S_{ss}\cdot H + S_{uu} \rightarrow \hat{S}_{ss}= \frac{S_{xs}}{H} = S_{ss}+ \frac{S_uu}{H}$

- Nastává pokud je při inverzní filtraci přítomen aditivní šum, pokud je $H(z)$ malé, pak ho $\frac{1}{H(z)}$ zesílí.
>TODO? nechápu jak ho jako zesílí

- Potlačení -> pseudoinverse: Nulování $\frac{1}{H}$ tam, kde je větší než práh.
	- limitace: $H = M \cdot e^{j\cdot arg(\frac{1}{H})}$, tam kde je větší než práh $(M)$

---
67. Modifikace inverzní filtrace

- **Inverzní filtrace**  -> $H_{i} = \frac{1}{H} -> \hat{S}_{ss} = \frac{S_{xs}}{H} = \frac{S_{ss}\cdot H + S_{uu}}{H} \neq S_{ss}$
				-> $\frac{S_{uu}}{H}$ -> šumová  katastrofa pro velké $S_{uu}$ nebo malé $H$

 - **Pseudoinverse**   ->  $H_{i}= \frac{1}{H} \hspace{0.25cm} \text{když} \hspace{0.25cm} |\frac{1}{H} |< M$
				 -> $H_{i}= 0 \hspace{0.25cm} \text{když} \hspace{0.25cm} |\frac{1}{H} | \geq M  \hspace{1cm} M ... \text{práh}$
				 -> Nulování složek spektra ke je $H$ malé

- **Limitace**    -> $H_{i}= \frac{1}{H} \hspace{0.25cm} \text{když} |\frac{1}{H}| < M$
			-> $H_{i} =M \cdot e^{j\cdot arg(\frac{1}{H})} \hspace{0.25cm} \text{když} |\frac{1}{H}| \geq M$
			-> neodstraní složky spektra a zachová fázi -> zpracování obrazů

---
68. Wienerova filtrace

![wienerova_filtrace.svg](wienerova_filtrace.svg)
$X[n] \dots \text{vstup WF, dán modelem zkreslení}$
$d[n] \dots \text{čistý signál}$
$\hat{d}[n] \dots \text{odhad čistého signálu} = h[n] \ast x[n]$
$l[n] \dots \text{chybový signál} = d[n] - \hat{d}[n]$

- Snažíme se najít filtr optimální pro danou úlohu (odstranění šumu,...)

---
69. Úlohy Wienerovy filtrace

1) **Filtrace** -> kauzální -> v reálném čase (výstup z minulých vstupů a aktuálního)
2) **Predikce** -> kauzální -> jednokroková predikce -> z minulých vzorků odhadujeme další
3) **Interpolace** -> nekauzální -> potřebujeme všechny vzorky uložené (z minulých i budoucích vzorků výstup)
4) **Dekonvoluce**     ->čistý signál ze vzorků a impulsové odezvy 
			    -> kauzální i nekauzální

- liší se požadovaným signálem a vstupním signálem
	-> **predikce** : $X[n] = s[n];\hspace{0.25cm}d[n] = s[n+1]$
	-> **dekonvoluce** : $X[n] = s[n] \ast h[n];\hspace{0.25cm} d[n]=s[n]$
	-> **filtrace a interpolace** : $X[n]= s+u;\hspace{0.25cm} d[n]=s$
	
---

70. Typy Wienerových filtrů

- obecný Wienerův filter : $H_{w}\cdot (e^{j\theta}) = \frac{S_{dx}(e^{j\theta})}{S_{xx}(e^{j\theta})}$
- Wienerův filtr pro additivní šum: $H_{w}(e^{j\theta}) = \frac{S_ss(e^{j\theta})}{S_{xx}(e^{j\theta})}(X[n] = s+n; \hspace{0.25cm} d=s) = \frac{S_{xx}(e^{j\theta})-S_{uu}}{S_{xx}} = \frac{S_{ss}}{S_{ss}+S_{uu}} = \frac{SNR (e^{j\theta})}{SNR (e^{j\theta}+1)}$ 
	- $S_{dx}\dots \text{vzájemná PSD do X}$
	- $S_{xx} \dots \text{PSDx(vstupní signál)}$
	- $S_{ss} \dots \text{PSDs (čistý signál)}$

- WF pro konvoluční šum: $\underbrace{H_{WF}}_{\text{Inverzní filtr}} = \underbrace{\frac{1}{H} \cdot \frac{|H|^2}{|H|^{2}+ \frac{S_{uu}}{S_{ss}}}}_{\text{Upravuje zisk ze znalosti H a SNR -> potlačení šumové katastrofy}}$

---
# Slepá separace a dekonvoluce

71. Učení adaptivních filtrů

- S učitelem -> existují trénovací signály s požadovanou odezvou -> nejprve na nich natrénujeme algoritmus, pak ho pustím do (na) opravdový signál a funguje

- Bez učitele -> slepá adaptace -> neexistuje požadovaná odezva (trénovací signál), existuje soubor pravidel, který umožňuje nastavit vztah mezi vstupem a výstupem -> přes ZV se to postupně za běhu určí
---
72. Předpoklady
 
- Slepá separace   -> signály jsou negaussovské (nenulové statistiky vyšších řádů)
				-> nezávislé
				-> skalární mixáž (výstupy lineární kombinace vstupů)
- Slepá dekonvoluce -> systém s minimální fází, pokud nemá, je nutné stabilizovat inverzní filtr
---
73. Rozdíly

- Slepá separace  -> známe směr signálů a chceme získat původní signály
				=> nalezení demixážní matice

- Slepá dekonvoluce    -> známe výstupní signál soustavy a chceme zjistit vstupní
					=> nalezení inverzního systému $H^{-1}$
	
- EAST ICA je metoda slepé separace
---
74. Dekonvoluční metody

- Kepstrální analýza -> známe výstupní signál
				   -> podmínky: jeden signál aperiodický a jeden se opakuje
- Inverzní filtrace  -> známe výstupy a $H(z)$
				-> $H(z)$ musí být s minimální fází
				-> šumová katastrofa
- Wienerova filtrace      -> inverzní filtrace s modifikací přenosu podle SNR
				    -> potlačení šumové katastrofy
---
# Vlnková tranformace - CWT; DWT

75. FT a STFT

- FT → fourierova transformace   -> výpočet spektra z celého signálu
							-> spektrum => jaké frekvenční složky jsou přítomné

- STFT -> krátkodobá FT -> okno -> výběr segmentu -> výpočet spektra segmentu ->      posun okna

- spektrogram ⇒ závislost frekvenčního spektra na čase

---
76. STFT vs. CWT

- STFT → mám signál a okno, kterým vybírám segment, pak porovnám segment s harmonickými průběhy → spektrogram

- CWT → porovnání signálu s vlnkou, kterou můžu posunout v čase a měnit její měřítko → scalogram (vlnka se zkracuje)

---
77. Časově frekvenční rozlišení STFT a CWT

- STFT → délka okna $\times$ frekvenční rozlišení = konstanta 
- CWT → časově frekvenční rozlišení prakticky neomezené → můžeme vlnku libovolně zkracovat → pro krátké vlnky zachytí rychlé změny, dlouhé vlnky pomalé (periodicita)
	-> úzká vlnka ⇒ široké spektrum a naopak
	
---
78. Pojmy

- **Vlnka** → fázová funkce vlnkové transformace
- **Hladina** → pro dané roztažení vlnky (měřítko), řez scalogramem
- **Aproximace** → nízko frekvenční část signálu → zaznamenávají široké vlnky
- **Detaily** → Rychlé změny v signálu → zaznamenávají úzké vlnky

- Pro DWT   → aproximace: nejnižší frekvenční pásmo
			-> detaily: vyšší frekvenční pásmo

![Pasted image 20240121093843.png](Pasted%20image%2020240121093843.png)

---
79. Rozdíl CWT a DWT

- U CWT se posun a měřítko mění spojitě, u DWT v diskrétních hodnotách (mocniny 2)
- DWT lze realizovat bankou filtrů

Použití → komprese a redukce šumu

---
80. Pojmy 2

- Měřítková funkce → vstup a výstup dolní propusti
![pojmy1.svg](pojmy1.svg) → měřítková funkce, na vstupu běží čas 2$\times$ rychleji - decimace

- Měřítková rovnice → vztah mezi měřítkovou funkcí na vstupu a výstupu
$$DP: \upvarepsilon (t) = \sqrt{2} h_{0} \ast \varphi(2t)$$
- vlnka → Přechodový děj s nulovou střední hodnotou a konečnou energií
- vlnková rovnice  → vztah měřítkové funkce a vlnky
![pojmy2.svg](pojmy2.svg)

Význam měřítkové a vlnové rovnice → určení $h_{0}$ pro banku filtrů
							-> určení měřítkové funkce a vlnky
							-> určení $h_{1}\hspace{0.25cm} z\hspace{0.25cm} h_{0}$

---

81. DWT banka filtrů

![DWT_banka_filtrů.svg](DWT_banka_filtr%C5%AF.svg)
- Impulsová odezva $h_0$ je v měřítkové rovnici; $h_1$ ve vlnkové

---
82. Redukce šumů v DWT

- Odhadneme práh z vlastností šumu a pak jsou koeficienty v jednotlivých pásmech prahovány

- **Tvrdé prahování** : koeficienty < thr → 0
				   koeficinety > thr → koeficienty

- **Měkké prahování** :    koeficienty < thr → 0
				    koeficienty > thr → $sign(koef) \cdot (|koef| - thr)$

![Práhování.svg](Pr%C3%A1hov%C3%A1n%C3%AD.svg)

---
83. Mateřská vlnka

- Přechodový děj (základní vlnka), kterou komprimujeme a posouváme

![Pasted image 20240121113115.png](Pasted%20image%2020240121113115.png)

---
84. Redukce šumu STFT a DWT

- DWT → prahování
- STFT → stejné jako DWT: odhadneme hladinu šumu, posouváme práh a tím oříznu hladinu šumu
	-> můžeme spektrálně odečítat

85. Banka filtrů
![Banka_filtrů.svg](Banka_filtr%C5%AF.svg)
- **Analyzující banka** → provádí rozklad do pásem
- **Syntetizující banka** → skládá pásma dohromady
- **Perfektní rekonstrukce** → Při splnění se signál na výstupu rovná signálu na vstupu (jen zpoždění)
<span class="symbols-prettifier-unclear">?nejasné</span> 
- Důsledky perfektní rekonstrukce: přenosové funkce jsou vázané, musím z DP odvodit další filtry
- Decimace a interpolace proto, abychom nenavyšovali počet vzorků

---
86.  Návrh dvoupásmové banky filtrů

1) Navrhneme prototyp DP který dělí pásmo na půl $H(z)\hspace{0.25cm} (h[n])$
2) $H_{0(z)}= H(z); \hspace{0.25cm} H_{1}(z) = \underbrace{H_{0} (-z)}_{\text{z DP udělám HP}}$
- Jsou vázány podmínkami perfektní rekonstrukce
	-> žádné překryvy mezi pásmy a žádné zkreslení

---
87. Kvadraturní zrcadlové filtry

- $|H_{0}|^{2}+|H_{1}|^{2} = 1$

![Kvad_zrcadlové_filtry.svg](Kvad_zrcadlov%C3%A9_filtry.svg)


