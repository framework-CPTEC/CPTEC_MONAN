Como Usar
=========

# Acesso aos dados MONAN

Na nova versão dos pacotes de distribuição dos **Modelos Numéricos MONAN**, oferecemos duas formas de acessar, filtrar e receber os dados:

- **[Interface de Linha de Comando (CLI)](ca://s?q=MONAN_acesso_CLI)**  
  A maneira mais recente e prática, permitindo interação direta com o sistema.

- **[Biblioteca Python](ca://s?q=MONAN_acesso_Python)**  
  O método tradicional, que continua disponível para quem prefere integrar o MONAN em seus scripts e aplicações.
  
.. warning::
  Alterar a data para os valores exibidos na inicialização
  
.. note::

  **Definição de Steps**
  
  steps = **<int>**
  
  Define o número de steps que serão pedidos
  
  Ex. steps = ``6``
  
  O pedido será os steps ``0,1,2,3,4,5,6``
  
  steps = **<list>**
  
  Define os steps que serão pedidos
  
  Ex. steps =  ``[0,2,4,6]``
  
  O pedido será os steps específicos pedidos ``0,2,4,6``

.. code-block:: console

  # Import para os modelos disponiveis
  # CPTEC_BAM, CPTEC_WRF, CPTEC_ETA, CPTEC_GFS
  import cptecmodel.CPTEC_BAM as BAM

  # Durante a inicialização do construtor informações sobre os dados são exibidas
  # Entre elas informações de variaveis, niveis e frequência disponiveis para consulta

  bam = BAM.model()

  # Data da IC
  date = '2023011700'

  # Variaveis 
  vars = ['t']

  # Niveis
  levels = [1000]

  # Steps = Numero de simulações futuras a partir da inicialização do modelo
  steps = 1

  # Utizando o método load
  f = bam.load(date=date, var=vars,level=levels, steps=steps)
  
  # Imprimir os valores recuperados
  print(f)

Variáveis e Níveis
------------------

Uma vez que o modelo específico é inicializado, suas informações são visualizadas.

>>> import cptecmodel.CPTEC_ETA as ETA
>>> eta = ETA.model()

#### Regional (ams_08km) #####

Forecast data available for reading between 20250803 and 20250813.

Surface variables: ['u10m', 'v10m', 't2m', 'slp', 'psfc', 'pw', 'precip', 'tsoil', 'soilm', 'tmax', 'tmin', 'dpt', 'acpcp', 'ncpcp', 'asnow', 'lhtfl', 'shtfl', 'gflux', 'ssrun', 'dswrf', 'dlwrf', 'uswrf', 'ulwrf', 'nswrt', 'nlwrt', 'lcdc', 'mcdc', 'hcdc', 'soilw'].

Level variables:   ['t', 'u', 'v', 'rh', 'g', 'omega', 'spfh', 'epot', 'cwat', 'cice'].

levels (hPa): ['1020', '1000', '950', '925', '900', '850', '800', '750', '700', '650', '600', '550', '500', '450', '400', '350', '300', '250', '200', '150', '100', '50'].

Frequency: hourly frequency [0,1,2,...,22,23].

Podem ser utilizados outros comandos:

>>> eta.get_var_description()
   Variable                                               Name        Unit
0         t                                Surface Temperature           C
1         u                                U-Component of Wind         m/s
2         v                                V-Component of Wind         m/s
3        rh                                  Relative Humidity           %
4         g                                Geopotential Height         gpm
5     omega                                              Omega            
6      u10m              10 m above ground U-Component of Wind         m/s
7      v10m              10 m above ground V-Component of Wind         m/s
8       t2m                       2 m above ground Temperature           C
9       slp             mean sea level Pressure Reduced to MSL          Pa
10     psfc                                   surface Pressure          Pa
11       pw                         surface Precipitable Water      kg/m^2
12   precip                        Surface Total Precipitation      kg/m^2
13    tsoil                           surface Soil Temperature           C
14    soilm                      surface Soil Moisture Content      kg/m^2
15     tmax                        surface Maximum Temperature           C
16     tmin                        surface Minimum Temperature           C
17      dpt                 above ground Dew Point Temperature           C
18    acpcp                   surface Convective Precipitation      kg/m^2
19    ncpcp  surface Large-Scale Precipitation (non-convect...      kg/m^2
20    asnow                             surface Total Snowfall           m
21    lhtfl                       surface Latent Heat Net Flux       W/m^2
22    shtfl                     surface Sensible Heat Net Flux       W/m^2
23    gflux                           surface Ground Heat Flux       W/m^2
24    ssrun                       surface Storm Surface Runoff      kg/m^2
25    dswrf         surface Downward Short-Wave Radiation Flux       W/m^2
26    dlwrf               surface Downward Long-Wave Rad. Flux       W/m^2
27    uswrf           surface Upward Short-Wave Radiation Flux       W/m^2
28    ulwrf                 surface Upward Long-Wave Rad. Flux       W/m^2
29    nswrt  surface Net Short-Wave Radiation Flux (Top of ...       W/m^2
30    nlwrt  surface Net Long-Wave Radiation Flux (Top of A...       W/m^2
31     lcdc                            surface Low Cloud Cover           %
32     mcdc                         surface Medium Cloud Cover           %
33     hcdc                           surface High Cloud Cover           %
34     spfh                                  Specific Humidity       kg/kg
35     epot  Pseudo-Adiabatic Potential Temperature (or Equ...           C
36     cwat                                        Cloud Water      kg/m^2
37     cice                                          Cloud Ice      kg/m^2
38    soilw           surface Volumetric Soil Moisture Content  Proportion

>>> eta.get_var_description('t2m')
  Variable                          Name Unit
0      t2m  2 m above ground Temperature    C

>>> eta.levels
['1020', '1000', '950', '925', '900', '850', '800', '750', '700', '650', '600', '550', '500', '450', '400', '350', '300', '250', '200', '150', '100', '50']

>>> eta.variables
['t', 'u', 'v', 'rh', 'g', 'omega', 'u10m', 'v10m', 't2m', 'slp', 'psfc', 'pw', 'precip', 'tsoil', 'soilm', 'tmax', 'tmin', 'dpt', 'acpcp', 'ncpcp', 'asnow', 'lhtfl', 'shtfl', 'gflux', 'ssrun', 'dswrf', 'dlwrf', 'uswrf', 'ulwrf', 'nswrt', 'nlwrt', 'lcdc', 'mcdc', 'hcdc', 'spfh', 'epot', 'cwat', 'cice', 'soilw']


Observações
-----------

Após a inicialização do Modelo Específico algumas configurações são plotadas.

Exemplo do BAM

The Brazilian Global Atmospheric Model (TQ0666L064 / Hybrid)

Forecast data available for reading between 20221211 and 20221221.

Surface variables: t2m, u10m, v10m, slp, psfc, precip terrain, sbcape, sbcin, pw. Level variables: t, u, v, rh, g, omega.

levels (hPa): 1000 925 850 775 700 500 400 300 250 200 150 100 70 50 30 20 10 3.

Frequency: every 6 hours [0, 6, 12, 18,...,168].

.. warning::

  Usar essas informações da inicialização na definição dos valores das variáveis (date,vars,levels,steps)


