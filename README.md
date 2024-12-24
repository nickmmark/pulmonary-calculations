# pulmonary-calculations

![](https://github.com/nickmmark/pulmonary-calculations/blob/main/mechanical_power_demo1.gif)

## Driving Pressure
**Driving pressure (∆P)** in the lung refers to the pressure difference between the plateau pressure (Pplat) - the pressure at full lung inflation and the positive end-expiratory pressure (PEEP), representing the force that drives air into the lungs during each breath. Driving pressure is a key indicator of lung strain, particularly in patients with conditions like acute respiratory distress syndrome (ARDS) where lung compliance is significantly reduced & maintaining a lower driving pressure is associated with improved outcomes.

```math
\Delta P = P_{plateau} = PEEP
```

A [common misconception](https://journals.aboutscience.eu/index.php/aboutopen/article/view/297/275) is that Pplat is the same as the inspiratory pressure during pressure control ventilation. This is untrue however. The Inspiratory pressure (IP) is the same as a the peak inspiratory pressure (PIP) in PC. The IP/PIP is always going to be (at least slighly) greater than Pplat because it represents the sum of airway resistance and lung compliance.

### Threshold
There is some controversy about the optimal cutoff value for driving pressure. A Driving Pressure greater than 15 cmH2O is clearly associated with worse outcomes including mortality, however a threshold of 13 cmH2O may be a better goal.

## Mechanical Power
Ventilator induced lung injury (VILI) is more likely to occur if more energy is transfered to the lung from the mechanical ventilator.
Mechanical power (MP) attempts to unify all the ways that energy can be transfered to the lung, using the [equation of motion](https://pubmed.ncbi.nlm.nih.gov/15436363/).
The formula depends on the mode of ventilation, however conceptually we can think of mechanical power as the area under the pressure volume curve (work) multiplied by the respiratory rate.

![](https://github.com/nickmmark/pulmonary-calculations/blob/main/Mechanical%20Power.png)

### Mechanical Power in Volume Control Ventilation (VCV) 

Per [Gattinoni _et al_](https://doi.org/10.1007/s00134-016-4505-2):
```math
{\text{Power}}_{\text{rs}} = {\text{RR}} \cdot \left\{ {\Delta V^{2} \cdot \left[ {\frac{1}{2} \cdot {\text{EL}}_{\text{rs}} + {\text{RR}} \cdot \frac{{\left( {1 + I:E} \right)}}{60 \cdot I:E} \cdot R_{\text{aw}} } \right] + \Delta V \cdot {\text{PEEP}}} \right\},
```

As explained [in the supplement](https://static-content.springer.com/esm/art%3A10.1007%2Fs00134-016-4505-2/MediaObjects/134_2016_4505_MOESM1_ESM.pdf), this can be simplified:
```math
Power_{VCV} = 0.098 \cdot RR \cdot \Delta V \cdot (P_{peak} - \frac{1}{2} \cdot \Delta P )
```
(note that 0.098 is a conversion factor to go from cmH2O*mL/min to Joules/min)
Thus for patients on volume control ventilation we only need five parameters to calculate MP: `Respiratory Rate (RR)`, `Tidal volume (TV)`, `Peak Inspiratory Pressure (PIP)`, `Plateau Pressure (Pplat)`, and `PEEP`.


### Mechanical Power in Pressure Control Ventilation (PCV) 

Per [Becher _et al_](https://doi.org/10.1007/s00134-019-05636-8):
```math
MP_{{{\text{PCV}}}} = 0.098 \cdot {\text{RR}} \cdot \left[ {(\Delta P_{\text{insp}} + {\text{PEEP}}) \cdot V_{{{\text{T}} }} {-} \Delta P_{\text{insp}}^{2} \cdot C \cdot \left( {0.5 {-} \frac{R \cdot C}{{T_{\text{slope}} }} + \left( {\frac{R \cdot C}{{T_{\text{slope}} }}} \right)^{2} \cdot \left( {1 {-} {\text{e}}^{{\frac{{ - T_{\text{slope}} }}{R \cdot C}}} } \right)} \right)} \right],
```

By assuming that the waveform is square, we can simplify this equation as well and remove the need for slope from the calculation:
```math
MP_{PCV} = 0.098 \cdot RR \cdot V_T \cdot (\Delta P_{insp} + PEEP )
```
Thus for patients on pressure control ventilation we only need four parameters to calculate MP: `RR`, `TV`, `Inspiratory Pressure (IP)`, and `PEEP`.

### Threshold
As with Driving Pressure, the goal and cutoff for Mechanical Power is controversial. There are compelling arguements for several different values as a safe threshold: 12 vs 17 vs 22 J/min. 
Normal negative pressure breathing generates a mechanical power of about 2.4 J/min.
Animal studies suggest the ventilator induced lung injury is unlikely if mechanical power is < 12 J/min.
A [review of MIMIC-III and eICU databases](https://link.springer.com/article/10.1007/s00134-018-5375-6) found that MP > 17 J/min predictive of worse clinical outcomes including ICU mortality, 30-day mortality, ventilator-free days, ICU & hospital length of stay. Even at low tidal volumes, high MP was associated with in-hospital mortality. 


## Mechanical Power and Driving Pressure Calculator
We can implement a simple web-based calculator that allows the user to select the ventilator mode (Volume Control or Pressure Control) and enter the requisite ventilator parameters. For simplicity, I combined MP and ∆P into one calculator. (This makes Plateau Pressure required even in PCV mode)

Probably the most controversial aspect of this calculator is the comments added to the results. Could argue endlessly about what exact thresholds to use and what the `alertMessage` should say.


![](https://github.com/nickmmark/pulmonary-calculations/blob/main/mechanical_power_demo2.gif)

```HTML
if (drivingPressure >= 15) {
   alertMessages += 'Driving Pressure (∆P) greater than 15 cmH2O is associated with worse clinical outcomes, including mortality. A ∆P less than 13 cmH2O may be associated with improved outcomes.<br>';
   }

if (mechanicalPower >= 17) {
   alertMessages += 'Mechanical Power (MP) greater than 17 Joules/minute is associated with worse clinical outcomes including mortality.';
}
```

## Disclaimer
This code is provided "as is", without warranty of any kind. Double check any calculations. See the attached license for more information about the MIT License.

## References
- Otis AB, Fenn WO, Rahn H. **[Mechanics of breathing in man](10.1152/jappl.1950.2.11.592)** _J Appl Physiol_ 1950
- Gattinoni, L., Tonetti, T., Cressoni, M. _et al._ **[Ventilator-related causes of lung injury: the mechanical power](https://doi.org/10.1007/s00134-016-4505-2)** _Intensive Care Med_ 2016 
- Becher, T., van der Staay, M., Schädler, D. _et al._ **[Calculation of mechanical power for pressure-controlled ventilation.](https://doi.org/10.1007/s00134-019-05636-8)** _Intensive Care Med_ 2019 
