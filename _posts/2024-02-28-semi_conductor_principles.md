---
layout: post
title: Some physical principles about semiconductors
date: 2024-02-28 08:00:00
description: a brief summary of semiconductors, in particular the PN junction
tags: semiconductor physics
categories: sample-posts
thumbnail: assets/img/9.jpg
---

## Semi-conducteurs à l'équilibre thermodynamique local

Pour un semi-conducteur à l'équilibre à $$0\,K$$, la bande remplie de plus haute énergie est appelée la **bande de valence** et la bande vide de plus basse énergie est la **bande de conduction**. Entre ces deux bandes, se trouve la **bande interdite** couramment appelée **gap** du semi-conducteur. L'énergie séparant la bande de valence et la bande de conduction est notée $$E_g$$. Les semi-conducteurs à base de silicium ont un gap de $$1,12$$ eV. 
À des températures non nulles, l'énergie d'agitation des atomes du réseau promeut des électrons de la bande de valence vers la bande de conduction. Il y a donc génération de paires électron-trou menant à un peuplement des états dont l'ocupation est décrite par une fonction de distribution notée $f$.

### Concentration de charges

La concentration d'électrons à l'équilibre, notée $$n$$, s'écrit selon l'équation \eqref{eq:n_equilibre}. 

\begin{equation}\label{eq:n_equilibre}
    n = \int_{E_c}^{+\infty} \mathrm{d}E \, f(E) D(E)
\end{equation}

où $$f(E)$$ est la probabilité qu'un électron occupe un état d'énergie $$E$$ et 
$$D(E) \mathrm{d}E$$ est le nombre d'états électroniques disponibles (nombre de places disponibles) dont l'énergie est comprise dans $$[E,E+\mathrm{d}E]$$, par unité de volume du cristal ($$D(E)$$ est la densité d'états).
$$\mathrm{d}E \, f(E) D(E)$$ est le nombre d'électrons ayant une énergie dans $$[E,E+\mathrm{d}E]$$, par unité de volume.
On peut définir de la même façon la concentration à l'équilibre pour les trous notée $$p$$ \eqref{eq:p_equilibre}.

\begin{equation}\label{eq:p_equilibre}
	p = \int_{-\infty}^{E_v} \mathrm{d}E \, (1-f(E)) D(E)
\end{equation}

Le nombre de porteurs effectifs dans chaque bande s'en déduit en prenant en compte la probabilité d'occupation de ces niveaux d'énergie.

La probabilité d'occupation d'un niveau d'énergie $$E$$ par un électron est décrite par la **statistique de Fermi-Dirac** à la température $$T$$ \eqref{eq:stat_fermi}.

\begin{equation}\label{eq:stat_fermi}
    f(E) = \frac{1}{1 + \exp(\frac{E-E_F}{k_B T})}
\end{equation}

où $$E_F$$ est le potentiel chimique (niveau de Fermi). Pour la plupart des semi-conducteurs, le niveau de Fermi se situe dans la bande interdite.

Dans l'hypothèse où le niveau de Fermi est éloigné de plusieurs $$k_B T$$ de la bande de conduction (typiquement pour $$E_c - E_F \geq 3 k_B T$$), la statistique de Fermi-Dirac se ramène à une **statistique de Boltzmann** \eqref{eq:stat_boltzmann}.

\begin{equation}\label{eq:stat_boltzmann}
    f(E) \simeq \exp(-\frac{E-E_F}{k_B T})
\end{equation}

La probabilité qu'un état d'énergie ne soit pas occupé par un électron (et donc occupé par un trou dans la bande de valence, i.e. si $$E<E_v$$) est donnée par le complémentaire de $$f(E)$$ \eqref{eq:stat_boltzmann_trou}.

\begin{equation}\label{eq:stat_boltzmann_trou}
    f_p(E) = 1 - f(E) = \frac{1}{1 + \exp(-\frac{E - E_F}{k_B T})}
\end{equation}

De façon similaire, si $$E_F - E_v \geq 3 k_B T$$ alors on se ramène à une statistique de Boltzmann et on obtient l'équation \eqref{eq:stat_boltzmann_trou_bis}.

\begin{equation}\label{eq:stat_boltzmann_trou_bis}
    f_p(E) = \exp(\frac{E-E_F}{k_B T})
\end{equation}


<div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/semicond/densites_etats.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">
Représentations des densités d’états et occupation des électrons et des trous
</div>  

En injectant les expression ci-dessus des distributions $$f$$ et $$f_p=1-f$$ dans les équations \eqref{eq:n_equilibre} et \eqref{eq:p_equilibre}, il vient :

\begin{equation}\label{eq:n_equilibre2}
    n = \int_{E_c}^{+\infty} D(E) \exp(-\frac{E-E_F}{k_B T}) \, \mathrm{d}E
\end{equation}

\begin{equation}\label{eq:p_equilibre2}
    p = \int_{-\infty}^{E_v} D(E) \exp(-\frac{E-E_F}{k_B T}) \, \mathrm{d}E
\end{equation}

Il est courant de définir les densités d'états effectives $$N_c$$ et $$N_v$$ (représentées sur la figure) telles que : 

\begin{equation}
	n = N_c\,f(E_c) =  N_c \exp(-\frac{E_c - E_F}{k_B T}) \label{eq:n_density}
\end{equation}

\begin{equation}
	p = N_v\,(1-f(E_v)) = N_v \exp(-\frac{E_F - E_v}{k_B T}) \label{eq:p_density}
\end{equation}

Par identification avec \eqref{eq:n_equilibre2} et \eqref{eq:p_equilibre2}, on obtient : 
\begin{equation}\label{eq:Nc_int}
   N_c = \int_{E_c}^{+\infty} D(E) \exp(-\frac{E-E_c}{k_B T}) \, \mathrm{d}E
\end{equation}

\begin{equation}\label{eq:Nv_int}
   N_v = \int_{-\infty}^{E_v} D(E) \exp(\frac{E-E_v}{k_B T}) \, \mathrm{d}E
\end{equation}

$$N_c$$ et $$N_v$$ (\eqref{eq:Nc_int} et \eqref{eq:Nv_int}) sont des constantes caractéristiques du semi-conducteur, accessibles dans la litérature,  et varient avec la température en $$T^{3/2}$$.

Le produit des concentrations à l'équilibre donne :
\begin{equation} \label{eq:np_product}
    n \cdot p = N_c N_v \exp(-\frac{E_g}{k_B T})
\end{equation}
Cette relation, appelée la \textit{loi d'action de masse}, ne fait intervenir que des caractéristiques du semi-conducteur qui sont généralement accessibles.

### Équilibre entre les populations d'électrons et de trous et au sein des populations, sous éclairement

Les populations d'électrons et de trous sont à l'équilibre entre elles lorsque le flux net de particules entre les populations est nul. Dans ce cas, les deux populations ont le même niveau de Fermi (le même potentiel chimique). Sous éclairement, les populations d'électrons et de trous peuvent ne plus être à l'équilibre entre elles (la vitesse de génération est plus grande que la vitesse de recombinaison) tout en ayant, séparément, une population d'électrons à l'équilibre thermodynamique local et une population de trous à l'équilibre thermodynamique local. Dans ce cas, chaque population est toujours décrite par une fonction de distribution de type Fermi-Dirac, mais l'énergie de Fermi est différente pour chaque population.

### Semi-conducteurs intrinsèques

Un semi-conducteur intrinsèque correspond à un semi-conducteur qui ne possède aucune impureté. 
Dans ce cas, et lorsque les densités de porteurs de charge sont uniformes, à chaque électron dans la bande de conduction correspond un trou dans la bande de valence et donc :

\begin{equation}
   n = p = n_i
\end{equation}

La densité $n_i$ est appelée la densité de porteurs intrinsèques et est une caractéristique du semi-conducteur à une température donnée.

D'après l'équation \eqref{eq:np_product}, l'expression de $$n_i^2$$ est donnée par l'équation \eqref{eq:niCarre}

\begin{equation}\label{eq:niCarre}
    n \cdot p = n_i^2 = N_c N_v \exp(-\frac{E_g}{k_B T}) \rightarrow n_i = \sqrt{N_c N_v} \exp(-\frac{E_g}{2 k_B T})
\end{equation}

Le produit $$N_c \cdot N_v$$ dépend de la température en $$T^3$$.

## Semi-conducteurs dopés

Pour augmenter la conductivité des semi-conducteurs, des atomes sont insérés dans le cristal. Cet ajout d'impuretés dans le cristal s'appelle le \textbf{dopage}. Ce dopage peut être réalisé de deux façons : le **dopage N** par l'ajout d'atomes apportant un excès d'électrons dans la bande de conduction, le **dopage P** par l'ajout d'atomes apportant un excès de trous dans la bande de valence. L'ajout des ces impuretés est négligeable par rapport aux atomes du cristal et par conséquent les densités d'états ne sont pas modifiées. Le produit $$n \cdot p$$ est indépendant du dopage et ne dépend que de la température. En revanche, le dopage va modifier la position du niveau de Fermi dans le semi-conducteur. 


Lorsque le semi-conducteur est à température ambiante, tous les atomes donneurs et accepteurs sont ionisés. Les atomes accepteurs sont donc ionisés négativement - on note leur densité $$N_a^-$$ - et les atomes donneurs sont ionisés positivement - on note leur densité $$N_d^+$$.

### Semi-conducteurs dopés P

Dans l'hypothèse où $$N_a^- \gg n_i$$, la densité de trous s'écrit selon l'équation \eqref{eq:approx_p_zone_P}.

\begin{equation}\label{eq:approx_p_zone_P}
    p \simeq N_a^-
\end{equation}

Le produit $$n \cdot p = n_i^2$$ étant fixé (voir \eqref{eq:niCarre}), la densité d'électrons dans le semi-conducteur dopé P s'en déduit (voir \eqref{eq:approx_n_zone_P}).

\begin{equation}\label{eq:approx_n_zone_P}
    n \simeq \frac{n_i^2}{N_a^-}
\end{equation}

En utilisant l'\eqref{eq:p_density} on obtient l'équation \eqref{eq:Na_dopageP}.

\begin{equation} \label{eq:Na_dopageP}
    p = N_a^- = N_v \exp(-\frac{E_{F_p} - E_v}{k_B T})
\end{equation}

où $$E_{F_p}$$ est le niveau de Fermi correspondant à un semi-conducteur dopé P défini par l'équation \eqref{eq:Efp_dopageP}.

\begin{equation} \label{eq:Efp_dopageP}
    E_{F_p} = E_v + k_B T \ln(\frac{N_a^-}{N_v})
\end{equation}

Dans l'expression \eqref{eq:Efp_dopageP}, on constate qu'une augmentation du dopage P (donc de la valeur de $$N_a^-$$) déplace le niveau de Fermi $$E_{F_p}$$ vers la bande de valence du semi-conducteur. Pour le silicium, $$N_v(300 \, \rm K) \approx 10^{19} \, \rm cm^{-3}$$ et $$N_a^- < N_v$$. Cela signifie que la bande de valence se remplit de trous et que la bande de conduction se vide d'électrons pour le semi-conducteur dopé P. En revanche, le produit $$n \cdot p$$ est conservé.

### Semi-conducteurs dopés N

Le même raisonnement s'applique pour un semi-conducteur dopé N. Dans l'hypothèse où $$N_d^+ \gg n_i$$, la densité d'électrons s'écrit selon l'équation \eqref{eq:approx_n_zone_N}.

\begin{equation}\label{eq:approx_n_zone_N}
    n \simeq N_d^+
\end{equation}

Le produit $$n \cdot p = n_i^2$$ étant fixé, la densité de trous dans le semi-conducteur dopé N s'en déduit (voir \eqref{eq:approx_p_zone_N})

\begin{equation}\label{eq:approx_p_zone_N}
    p \simeq \frac{n_i^2}{N_d^+}
\end{equation}


En utilisant \eqref{eq:n_density}, on obtient la densité en électrons (\eqref{eq:Nd_dopageN}).

\begin{equation} \label{eq:Nd_dopageN}
    n = N_d^+ = N_c \exp(-\frac{E_c - E_{F_n}}{k_B T})
\end{equation}

où $$E_{F_n}$$ est le niveau de Fermi correspondant à un semi-conducteur dopé N. Comme $$N_d^+ < N_c$$, le niveau de Fermi $$F_n$$ est bien en-dessous du niveau bas de la bande de conduction.

En partant de l'\eqref{eq:Nd_dopageN}, le niveau de Fermi pour le semi-conducteur s'exprime par l'équation \eqref{eq:Efn_dopageN}

\begin{equation} \label{eq:Efn_dopageN}
    E_{F_n} = E_c + k_B T \ln(\frac{N_d^+}{N_c})
\end{equation}

De façon similaire au semi-conducteur dopé P, l'augmentation du dopage N (augmentation de $$N_d^+$$) déplace le niveau de Fermi $$E_{F_n}$$ vers la bande de conduction du semi-conducteur. La bande de conduction se remplit d'électrons et la bande de valence se vide de trous tout en gardant constant le produit $$n \cdot p$$.

### Jonction PN

Une jonction PN est formée d'un semi-conducteur dopé N et d'un semi-conducteur dopé P. Lorsque les deux semi-conducteurs sont mis en contact, les trous vont diffuser de la région P vers la région N et inversement, les électrons vont diffuser de N vers P. Au niveau de la jonction, les électrons et les trous vont se recombiner et une zone particulière se crée à ce niveau où seuls les atomes donneurs et accepteurs sont présents, c'est la **Zone de Charge d'Espace (ZCE)**. Comme les atomes donneurs sont ionisés positivement et les atomes accepteurs négativement, un champ électrique apparaît dans la ZCE et est dirigé de la zone N vers la zone P.

<div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/semicond/jonction_PN_coordinates.jpg" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Jonction PN et définitions des ordonnées pour chaque frontière
</div>

À l'équilibre thermodynamique et après contact entre les deux semi-conducteurs dopés, le niveau de Fermi est uniforme dans le semi-conducteur. Le dopage P déplace le niveau de Fermi vers la bande de valence et le dopage N le déplace vers la bande de conduction. On voit ainsi apparaître une barrière de potentiel au niveau de la ZCE. Cette barrière empêche les trous de diffuser de P vers N et les électrons de diffuser de N vers P.

La valeur de la barrière de potentiel est donnée par l'équation \eqref{eq:barriere_potentiel}.

\begin{equation}\label{eq:barriere_potentiel}
	e V_{b} = E_{c_p} - E_{c_n} = E_{v_p} - E_{v_n}
\end{equation}

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/semicond/barriere_potentiel.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/semicond/abaissement_barriere_potentiel.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

À partir des équations \eqref{eq:Efp_dopageP} et \eqref{eq:Efn_dopageN}, la valeur de $$V_{bi}$$ , la barrière de potentiel intégré (\textit{built-in potential}), peut s'écrire : $$V_b = V_{bi} - V_{\text{app}}$$.

\begin{equation}
	e V_{bi} = E_g - (E_c - E_{F_n}) - (E_{F_p}-E_v) = E_g - k_B T \ln(\frac{N_c}{N_d^+}) - k_B T \ln(\frac{N_v}{N_a^-}) = E_g + k_B T \ln(\frac{N_d^+ N_a^-}{N_c N_v})
\end{equation}

En rappelant que $$n_i^2 = N_c N_v \exp(-\frac{E_g}{k_B T})$$, la barrière de potentiel se réécrit selon \eqref{eq:barriere_potentiel_bis}

\begin{equation} \label{eq:barriere_potentiel_bis}
	e V_{bi} = E_g + k_B T \ln(N_d^+ N_a^-) - k_B T \ln(n_i^2 \exp(\frac{E_g}{k_B T})) = k_B T \ln(\frac{N_d^+ N_a^-}{n_i^2})
\end{equation}

%!! Dans le déroulé, attention, à partir d'ici on est plus à l'équilibre. !!

L'application d'une polarisation directe $$V_{\text{app}}$$ à la jonction PN a pour effet l'abaissement de la barrière de potentiel d'une valeur $$e V_{\text{app}}$$ :  (voir la \label{fig:schema_barriere_potentiel}).

### Largeur de la ZCE et position de la frontière

La charge dans le cristal est donnée par :

\begin{equation}
    \rho(z) = e(\mathring{p}(z) + \Delta p(z) - \mathring{n}(z) - \Delta n(z) + N_d^+ - N_a^-)
\end{equation}

Le théorème de Gauss permet de calculer le champ électrique $$\symbf{E}$$ dans la ZCE :

\begin{equation} \label{equation_gauss}
    \partial_z E = -\partial_z^2 \varphi = \frac{\rho(z)}{\epsilon}
\end{equation}
où $$\epsilon$$ est la permittivité qui sera prise égale dans les couches dopée N et P.

\paragraph{Zone P entre $$\symbf{z_{CT}}$ et $\symbf{z_{CE}}$$}

La charge électrique est égale à $$-e N_a^-$$ et par suite :

\begin{equation}
    E(z) = \frac{-e N_a^-}{\epsilon}(z-z_{CT})
\end{equation}
où on a pris $$E(z_{CT})=0$$ sous l'hypothèse que l'effet du champ est nul en dehors de la ZCE.

Le potentiel s'obtient en intégrant le champ $$E(z)$$ entre $$z_{CE}$$ et $$z_{CT}$$ :

\begin{equation} \label{potentiel_ZCE_P}
    \varphi(z) = \frac{e N_a^-}{2 \epsilon} (z - z_{CT})^2 + \varphi(z_{CT})
\end{equation}

On pose l'origine des potentiels en $$z=z_{CT}$$ et donc $$V(z_{CT}) = 0$$.

\paragraph{Zone N entre $$\symbf{z_{CE}}$$ et $$\symbf{z_{CB}}$$}

La charge électrique est égale à $$e N_d^+$$ et donc :

\begin{equation}
    E(z) = \frac{e N_d^+}{\epsilon}(z - z_{CB})
\end{equation}
où on a pris $$E(z_{CB})=0$$ sous l'hypothèse que l'effet du champ est nul en dehors de la ZCE.

En intégrant l'expression $$E(z)$$ entre $$z_{CB}$$ et $$z_{CE}$$ :

\begin{equation} \label{potentiel_ZCE_N}
	\varphi(z) = \frac{-e N_d^+}{2\epsilon}(z - z_{CB})^2 + \varphi(z_{CB})
\end{equation}

La barrière de potentiel intégrée est égale à $$V_{bi}=\varphi(z_{CB})-\varphi(z_{CT})$$.

<div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/semicond/champs_E_V_ZCE.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>
<div class="caption">
    Représentation du champ électrique et du potentiel électrique dans la ZCE
</div>

On introduit maintenant les longueurs de la ZCE du côté P et N avec $$\lambda_n=z_{CE}-z_{CB}$$ la longueur du côté N et $$\lambda_p=z_{CT}-z_{CE}$$ celle du côté P. La largeur totale de la ZCE est donc donnée par $$\lambda_n + \lambda_p$$. Le champ électrique, le potentiel et la longueur de la ZCE sont représentés sur \label{fig:jonction_PN_coordinates}

On ne s'intéresse qu'à des situations dans lesquelles on a neutralité globale du semi-conducteur. De ce fait, les charges du côté N doivent compenser celles de la zone P dans la ZCE :

\begin{equation} \label{neutralite_ZCE}
    \lambda_n N_d^+ = \lambda_p N_a^-
\end{equation}

La continuité du potentiel implique que les expressions \eqref{potentiel_ZCE_P} et \eqref{potentiel_ZCE_N} donnent la même valeur en $$z_{CE}$$ :
\begin{equation}
	\frac{e N_a^-}{2 \epsilon} \lambda_p^2 = \frac{-e N_d^+}{2\epsilon}\lambda_n^2 + V_{bi}
\end{equation}

Avec \eqref{neutralite_ZCE}, on obtient les longueurs de la ZCE du côté N et P :

\begin{equation}
    \lambda_n^2 = \frac{2 \epsilon}{e N_d^+}\frac{1}{1 + N_d^+ / N_a^-} V_b
\end{equation}

\begin{equation}
    \lambda_p^2 = \frac{2 \epsilon}{e N_a^-}\frac{1}{1 + N_a^- / N_d^+} V_b
\end{equation}

où

- $$V_b = V_{bi}$$ en l'abscence de polarisation,
- $$V_b = V_{bi}- V_{\text{app}}$$ si la jonction est en polarisation directe selon un potentiel $$V_{\text{app}}$$.

## Jonction PN hors équilibre

A l'obscurité et sans surtension, les densités pour les électrons et les trous sont notées respectivement $$\mathring{n}$$ et $$\mathring{p}$$ .
Ce sont les densités à l'équilibre.
Sous éclairement et/ou surtension, ces densités sont modifiées ; on note $$\Delta n$$ et $$\Delta p$$ les densités de porteurs minoritaires en excès par rapport à l'équilibre :

\begin{align}
	n = \mathring{n} + \Delta n \text{ et }
	p = \mathring{p} + \Delta p
\end{align}

Ce delta correspond à la somme des électrons (resp. trous) qui ont été photogénérés dans la zone P (resp. N) et des électrons (resp. trous) qui ont été injectés de la zone N vers la zone P (resp. de la zone P vers la zone P) suite à l'application d'une tension externe ($$V_{\text{app}}$$) positive.


Dans un semi-conducteur, les électrons et les trous peuvent être mis en mouvement par un gradient de concentration ou un champ électrique. Le gradient de concentration s'accompagne d'une **diffusion** des particules alors que le champ électrique induit une \textbf{dérive} des particules. Par conséquent, le modèle qui décrit le déplacement des électrons et des trous dans une jonction de type PN est celui de **dérive-diffusion**.


Dans la situation d'une jonction PN, il y a trois zones distinctes :

- la zone P : elle correspond d'après le schéma à l'intervalle $$z \in [z_{CT}; z_T]$$ et dans cette zone seule la diffusion des électrons (minoritaires) est considérée car le champ électrique est nul.
- la zone N : elle correspond d'après le schéma à l'intervalle $$z \in [z_B; z_{CB}]$$ et dans cette zone seule la diffusion des trous (minoritaires) est considérée car le champ électrique est nul.
- la ZCE : dans cette zone le champ électrique $$\symbf{E}$$ résultant des atomes accepteurs et donneurs ionisés domine.


Les vecteurs densité surfacique de flux de particules $$\symbf{j_n}$$ et $$\symbf{j_p}$$ sont maintenant introduites et correspondent à des particules par $$\rm m^2 \cdot s^{-1}$$.

\begin{equation}
\symbf{j_n} = - D_n \symbf{\nabla}{\Delta n(z)} - \Delta n(z) \mu_n \symbf{E}
\end{equation}

\begin{equation}
\symbf{j_p} = - D_p \symbf{\nabla}{\Delta p(z)} + \Delta p(z) \mu_p \symbf{E}
\end{equation}

À l'équilibre thermodynamique, le courant total $$\symbf{j} = \symbf{j_n} + \symbf{j_p}$$ est nul car le champ électrique compense exactement la diffusion.

Dans le modèle qui suit, le terme de dérive est négligé hors de la ZCE. Dans la ZCE, la phénoménologie ci-dessus pour les densités de flux n'est pas utilisée.


### Génération, Recombinaison et superposition des densités d'équilibre

En **régime de faible injection**, seuls les porteurs minoritaires sont suivis dans la jonction PN. Ce mode de fonctionnement correspond à un semi-conducteur où la densité des porteurs minoritaires (les électrons dans P et les trous dans N) est faible devant la densité des porteurs majoritaires. Dans chacune des zones, on écrit :

\begin{equation}
n(z) = \underbrace{\Delta n(z)}_{\substack{\text{photogénérés} \\ \text{+} \\ \text{injectés}}} + \mathring{n}(z) = \Delta n^{ph.}(z) + \Delta n^{inj.}(z) + \mathring{p}(z)
\end{equation}

\begin{equation}
p(z) = \underbrace{\Delta p(z)}_{\substack{\text{photogénérés} \\ \text{+} \\ \text{injectés}}} + 
\mathring{p}(z) = \Delta p^{ph.}(z) + \Delta p^{inj.}(z) + \mathring{p}(z)
\end{equation}

avec $$\mathring{n}$$ et $$\mathring{p}$$ les densités en électrons et trous à l'équilibre.

Les équations de diffusion sur les photogénérés s'écrivent (*en régime stationnaire*) : 

\begin{equation}
	-D_n \partial_z^2 \Delta n^{ph.}(z) = G_n(z) - R_n^{ph.}(z) \text{ et }
	-D_p \partial_z^2 \Delta p^{ph.}(z) = G_p(z) - R_p^{ph.}(z)
\end{equation}

Et sur les injectés :

\begin{equation}
	-D_n \partial_z^2 \Delta n^{inj.}(z) = 0 - R_n^{inj.}(z) \text{ et }
	-D_p \partial_z^2\Delta p^{inj.}(z) = 0 - R_p^{inj.}(z)
\end{equation}

Dans le cadre de l'approximation linéaire des termes de recombinaison $$R_n^{i} = \Delta n^i \tau$$ et $$R_p^{i} = \Delta p^i \tau$$ ($$i = inj. \text{ ou } ph.$$), on peut sommer les équations sur les photogénérés et les injectés.

\begin{equation}
    -D_n \partial_z^2 \Delta n(z) = G_n(z) - R_n(z) \label{eq:diffusion_n}
\end{equation}

\begin{equation}
    -D_p \partial_z^2 \Delta p(z) = G_p(z) - R_p(z) \label{eq:diffusion_p}
\end{equation}
où $$R_j = R_j^{inj.} + R_j^{ph.}$$ avec $$j = n \text{ ou } p$$.

De cette manière, une seule équation de diffusion est écrite pour les électrons et les trous au lieu d'une équation pour la diffusion des minoritaires au lieu des 4 équations de diffusion écrites précédemment. On pourrait aussi effectuer une superposition d'équations de diffusion pour un ensemble d'intervalles spectraux $$\delta \nu$$.