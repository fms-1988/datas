## CO2e Emission Coefficients for the Brazilian Economy

The **Sirene** package is crafted to provide CO2e emissions data for various Brazilian economic activities. This package facilitates the estimation of direct emission coefficients for each sector, representing the volume of emissions in Gg relative to the production volume (expressed in aggregate value in millions of reais).

Beyond direct coefficients, it also computes the indirect emission coefficients. The estimation methodology is adopted from Luis Masa's paper, titled ["AN ESTIMATION OF THE CARBON FOOTPRINT IN SPANISH CREDIT INSTITUTIONS’ BUSINESS LENDING PORTFOLIO"](https://repositorio.bde.es/bitstream/123456789/29610/4/do2220e.pdf).

The **Sirene** package contains a series of variables that detail emissions from various sectors and other related data. The available variables are:

- `**atividade_tru68_ibge**`: Refers to activity (i) of TRU68.
- `**production_values_mi_brl**`: Represents the total production of activity (i) for the year (t) in millions of BRL.
- `**ano**`: Reference year with complete data available between 2012 and 2020.
- `**energia_Gg_CO2e_GWP_SAR**`: Emissions of CO2e from the energy sector in Gg, calculated using the CO2e_GWP_SAR methodology.
- `**residuo_Gg_CO2e_GWP_SAR**`: Emissions of CO2e from the waste sector in Gg.
- `**agropecuaria_Gg_CO2e_GWP_SAR**`: Emissions of CO2e from the agricultural sector in Gg.
- `**ippu_Gg_CO2e_GWP_SAR**`: Emissions of CO2e from the IPPU sector in Gg.
- `**lulucf_Gg_CO2e_GWP_SAR**`: Emissions of CO2e from the LULUCF sector in Gg.
- `**total_Gg_CO2e_GWP_SAR**`: Total CO2e emissions in Gg.
- `**active_loan_portfolio_mi_brl**`: Value of loans by sector in millions of BRL.
- `**q_direct**`: Coefficient of direct emissions.
- `**q_total**`: Coefficient of total emissions.
- `**q_indirect**`: Coefficient of indirect emissions.


### Instalation

```python
!pip install sirene
from sirene import srn2 as srn
coef67_t = srn.coef('2019', lulucf = False).result
```

### Reading the Raw Emission Data (MCTI/SIRENE)

Emission data is available for 3 different gases ('CO2', 'CH4', 'N2O'). If preferred, it is also possible to consult equivalent emissions ('CO2e_GWP_SAR', 'CO2e_GWP_AR5', 'CO2e_GTP_AR5'). The available sectors are: 'agropecuaria', 'energia', 'ippu', 'lulucf', 'residuos' and 'total-brasil-1'.

```python
res_m = srn2.read('residuos','CO2')
```

### Main Function: coef()

The `coef()` function is the core of this package and returns all of the above-listed variables. The arguments it accepts are:

- `ano`: String representing the desired year, with values between 2012 and 2020.
- `household`: Boolean (True or False) determining whether households should be considered when calculating emissions and coefficients.
- `emission`: Defines which type of emission will be considered when constructing the emission coefficients. Available options are: 'total', 'total_no_lulucf', 'lulucf', 'ippu', 'residuo', and 'agropecuaria'.

**Usage Example**:

```python
result_t = srn.coef('2019', emission='lulucf', household=False).result
```

---


