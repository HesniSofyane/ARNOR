## Morphometric Parameters  

The scripts in this repository compute several **morphometric parameters** associated with subglacial bedforms. These parameters are derived using a semi-automatic mapping method. Below is a detailed description of each parameter, its formula, and its definition:  

```latex
\documentclass[8pt]{article}
\usepackage{amsmath} % For equations
\usepackage{array}   % For custom column specification
\usepackage{adjustbox}
\usepackage[textwidth=160mm]{geometry} % Set maximum width to 160mm
\usepackage{caption} % For captions

\begin{document}

\noindent
\begin{adjustbox}{width=\textwidth}
\begin{tabular}{l c m{0.5\linewidth}} % Three columns: Parameter, Formula, and Definition
    \hline
    \textbf{Parameter} & \textbf{Formula} & \textbf{Definition} \\
    \hline & & \\[-1ex]
    
    Area & - & {\fontsize{8}{7.2}\selectfont Bedform Area.} \\[1.5cm]
    Width & - & {\fontsize{8}{7.2}\selectfont Width of bedform's Oriented Minimum Bounding Box (OMMB).} \\[1.5cm]
    Length & - & {\fontsize{8}{7.2}\selectfont Length of bedform's Oriented Minimum Bounding Box (OMMB).} \\[1.5cm]
    Number of bedforms per hexagon & - & {\fontsize{8}{7.2}\selectfont Number of bedforms totally or partially contained by each hexagon.} \\[1.5cm]
    
    Volume & \scalebox{1.33}{$V=\sum_{i=1}^n \text {h}_i \times \text {Pixel area}$} & {\fontsize{8}{7.2}\selectfont Refers to the quantity of bedform material located above a base plane interpolated from the bedform outline altitude, with $h_{n}$ the difference between the base plane and the topography for $n$ pixels inside the bedform outline.} \\[2.2cm]

    Mean thickness & \scalebox{1.33}{$h_{mean}=\frac{\text V}{\text A}$} & {\fontsize{8}{7.2}\selectfont Bedform average thickness calculated from a ratio between its volume V and area A.} \\[2.2cm]

    Circularity index & \scalebox{1.33}{$I_{cir}=\frac{4 \times A \times \pi}{P^2}$} & {\fontsize{8}{7.2}\selectfont Compares the perimeter (P) of a contour of a given area (A) with the perimeter of a circle of an identical area (Burgess et al., 2003).} \\[1cm]
    
    Sinuosity index & \scalebox{1.33}{$I_{sin}=\frac{\frac{\text { Curvilinear length }}{\text { Straight length }}-1}{\sqrt{5}-1}$} & {\fontsize{8}{7.2}\selectfont Measures the sinuosity of the crestline (i.e. ratio between the curvilinear length of the crest line and its straight length; Schumm, 1963), normalized to the sinuosity of an equilateral triangle (${\sqrt{5}}$) (Vérité et al., 2022).} \\[2cm]
    
    Oriented elongation index & \scalebox{1.33}{$I_{oe}=\log _{10}\left(\frac{LC_{MAX}}{TC_{MAX}}\right)$} & {\fontsize{8}{7.2}\selectfont Measures the ratio between the maximal longitudinal (i.e. along-ice flow; ${LC_{MAX}}$) and the maximal transverse (i.e. across-ice flow; ${TC_{MAX}}$) components of a bedform, expressed on a logarithmic scale.} \\[1.5cm]
    
    Degree of evolution & \scalebox{1.33}{$Deg_{evo}=\left(\frac{\pi}{2}+\tan ^{-1}\left(\frac{I_{oe}}{I_{sin}}\right)\right) \times\left(I_{oe}+1\right)$} & {\fontsize{8}{7.2}\selectfont Traces the evolution of subglacial bedforms, starting as linear ribbed structures and progressing through complex transitional forms with varying sinuosities($I_{sin}$) and orientations ($I_{oe}$), ultimately transforming into elongated streamlined bedforms.} \\[2.2cm]

    \hline
\end{tabular}
\end{adjustbox}

\captionsetup{justification=centering} % Center the caption text
\captionof{table}{Tab. S1: Morphometric parameters produced by the semi-automatic mapping method.}

\end{document}

