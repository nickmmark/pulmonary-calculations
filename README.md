# pulmonary-calculations

## Driving Pressure

```math
\Delta P = P_{plateau} = PEEP
```


## Mechanical Power


### Mechanical Power in Volume Control (VC) Ventilation

Per [Gattinoni _et al_](https://doi.org/10.1007/s00134-016-4505-2):
```math
{\text{Power}}_{\text{rs}} = {\text{RR}} \cdot \left\{ {\Delta V^{2} \cdot \left[ {\frac{1}{2} \cdot {\text{EL}}_{\text{rs}} + {\text{RR}} \cdot \frac{{\left( {1 + I:E} \right)}}{60 \cdot I:E} \cdot R_{\text{aw}} } \right] + \Delta V \cdot {\text{PEEP}}} \right\},
```


### Mechanical Power in Pressuve Control (PC) Ventilation

Per [Becher _et al_](https://doi.org/10.1007/s00134-019-05636-8):
```math
MP_{{{\text{PCV}}({\text{slope}})}} = 0.098 \cdot {\text{RR}} \cdot \left[ {(\Delta P_{\text{insp}} + {\text{PEEP}}) \cdot V_{{{\text{T}} }} {-} \Delta P_{\text{insp}}^{2} \cdot C \cdot \left( {0.5 {-} \frac{R \cdot C}{{T_{\text{slope}} }} + \left( {\frac{R \cdot C}{{T_{\text{slope}} }}} \right)^{2} \cdot \left( {1 {-} {\text{e}}^{{\frac{{ - T_{\text{slope}} }}{R \cdot C}}} } \right)} \right)} \right],
```

This can be simplified
𝐸𝑏𝑟𝑒𝑎𝑡ℎ = ∆𝑉2 ∙𝐸𝐿𝑟𝑠 ∙ 1 2 +∆𝑉∙(𝑃𝑝𝑒𝑎𝑘 −𝑃𝑝𝑙𝑎𝑡)+ ∆𝑉 ∙𝑃𝐸𝐸𝑃
Knowing that ELrs=∆Paw/∆V, the equation can be rewritten as follows: 𝐸𝑏𝑟𝑒𝑎𝑡ℎ = ∆𝑉 ∙ (1 2 ∙ ∆𝑃𝑎𝑤 +𝑃𝑝𝑒𝑎𝑘 −𝑃𝑝𝑙𝑎𝑡 +𝑃𝐸𝐸𝑃)
Where ∆Paw=Pplat–PEEP. 
Accordingly: 𝐸𝑏𝑟𝑒𝑎𝑡ℎ = ∆𝑉 ∙ [𝑃𝑝𝑒𝑎𝑘 −1 2 Or: 𝐸𝑏𝑟𝑒𝑎𝑡ℎ = ∆𝑉 ∙ (𝑃𝑝𝑒𝑎𝑘 − 1 2 So: ∙ (𝑃𝑝𝑙𝑎𝑡 − 𝑃𝐸𝐸𝑃)]     ∙ ∆𝑃𝑎𝑤)       
𝑃𝑜𝑤𝑒𝑟𝑟𝑠 = 0.098∙𝑅𝑅 ∙∆𝑉 ∙(𝑃𝑝𝑒𝑎𝑘 −1 2 ∙ ∆𝑃𝑎𝑤)  


## References
Gattinoni, L., Tonetti, T., Cressoni, M. _et al._ **[Ventilator-related causes of lung injury: the mechanical power](https://doi.org/10.1007/s00134-016-4505-2)** _Intensive Care Med_ 2016 

Becher, T., van der Staay, M., Schädler, D. _et al._ **[Calculation of mechanical power for pressure-controlled ventilation.](https://doi.org/10.1007/s00134-019-05636-8)** _Intensive Care Med_ 2019 
