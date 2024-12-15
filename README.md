# pulmonary-calculations

## Driving Pressure
**Driving pressure (∆P)** in the lung refers to the pressure difference between the plateau pressure (Pplat) - the pressure at full lung inflation and the positive end-expiratory pressure (PEEP), representing the force that drives air into the lungs during each breath. Driving pressure is a key indicator of lung strain, particularly in patients with conditions like acute respiratory distress syndrome (ARDS) where lung compliance is significantly reduced & maintaining a lower driving pressure is associated with improved outcomes.

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

As explained [in the supplement](https://static-content.springer.com/esm/art%3A10.1007%2Fs00134-016-4505-2/MediaObjects/134_2016_4505_MOESM1_ESM.pdf), this can be simplified:
```math
MP = 0.098 \cdot RR \cdot \Delta V \cdot (P_{peak} - \frac{1}{2} \cdot \Delta P_{aw} )
```



## References
Gattinoni, L., Tonetti, T., Cressoni, M. _et al._ **[Ventilator-related causes of lung injury: the mechanical power](https://doi.org/10.1007/s00134-016-4505-2)** _Intensive Care Med_ 2016 

Becher, T., van der Staay, M., Schädler, D. _et al._ **[Calculation of mechanical power for pressure-controlled ventilation.](https://doi.org/10.1007/s00134-019-05636-8)** _Intensive Care Med_ 2019 
