Biblioteca Python
================


- **[Biblioteca Python])**  
  O método tradicional, que continua disponível para quem prefere integrar o MONAN em seus scripts e aplicações.

.. warning::
  Alterar a data para os valores exibidos na inicialização
  
.. note::

Data Inicialização do MONAN
----------------------------

  Para saber mais detalhes sobre o uso da opção **date** consultar `Data de Inicialização <usage.html#horarios-de-inicializacao-do-modelo-monan>`_


Definição de Steps
------------------

   Para saber mais detalhes sobre o uso da opção **steps** consultar `Intervalo de Previsão <usage.html#intervalo-de-previsao-do-monan>`_

.. warning::
  O step do MONAN é de 3 em 3 horas
  Ex. steps =  ``[0,3,6,9]``
  O pedido será os steps específicos pedidos ``0,3,6,9``

.. code-block:: console

  # Import para o modelo MONAN
  import monanmodel.CPTEC_MONAN as MON

  # Durante a inicialização do construtor informações sobre os dados são exibidas
  # Entre elas informações de variaveis, niveis e frequência disponiveis para consulta

  mon = MON.model()

  # Data da IC
  date = '20260901'

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

>>> import monanmodel.CPTEC_MONAN as MON
>>> mon = MON.model()

#### Model for Ocean-laNd-Atmosphere PredictioN - (MONAN) (10km) #####

Forecast data available for reading between 20260920 and 20260930.

Surface variables: ['u10m', 'v10m', 't2m', 'slp', 'psfc', 'landmask', 'sbcape', 'sbcin', 'pw', 'precip', 'rainnc', 'acswdnb', 'aclwupb', 'aclwupt', 'q2', 'hfx', 'lh', 'cldfrac_tot_UPP', 'terrain'].

Level variables:   ['t', 'u', 'v', 'rh', 'g', 'omega', 'spechum'].

levels (hPa): ['1000', '925', '850', '775', '700', '500', '400', '300', '250', '200', '150', '100', '70', '50', '30', '20', '10', '3'].

Frequency: every 3 hours  [0,3,6,...,264].


Podem ser utilizados outros comandos:

>>> mon.list_variables()
Variables at the surface: ['u10m', 'v10m', 't2m', 'slp', 'psfc', 'landmask', 'sbcape', 'sbcin', 'pw', 'precip', 'rainnc', 'acswdnb', 'aclwupb', 'aclwupt', 'q2', 'hfx', 'lh', 'cldfrac_tot_UPP', 'terrain']
Variables at different levels: ['t', 'u', 'v', 'rh', 'g', 'omega', 'spechum']


>>> mon.get_var_description('t')
  Variable                                               Name Unit
0        t  Temperature interpolated to isobaric surfaces ...    C


>>> mon.list_levels()
Available levels: ['1000', '925', '850', '775', '700', '500', '400', '300', '250', '200', '150', '100', '70', '50', '30', '20', '10', '3']


Ler dados do MONAN
------------------

O pacote **MONAN** oferece duas formas principais de leitura de dados:

- **load_shape**  

  Utilizado quando se deseja aplicar um **recorte espacial** nos dados.  

  Permite selecionar áreas específicas (como estados, regiões ou continentes) usando abreviações de shape.  
  Exemplo: `shp="estados_sp"` para restringir os dados ao estado de São Paulo.

  Para listas as areas existentes utilizar o comando.

>>> mon.list_areas("continentes")
Usage: type_abbreviation e.g. shp='estados_sp'
Area    -   type_abbreviation
Africa - continentes_af
Antartica - continentes_an
Asia - continentes_as
Australia - continentes_au
Europa - continentes_eu
Oceania - continentes_oc
America do Sul - continentes_sa
America do Norte - continentes_na


- **load**  

  Utilizado para baixar dados **sem recorte de área**, ou seja, em domínio global ou completo.  
  É indicado quando o objetivo é trabalhar com a totalidade dos dados disponíveis, sem limitar a região.


**Baixar variáveis de superfície e com recorte de área**

>>> f = mon.load_shape(date="2026092800", var=["t2m", "u10m", "v10m"], steps=[0,3,6], shp="estados_sp")


**Baixar variáveis de niveis (1000/850)**

>>> f = mon.load( date="2026092800", var=["u","v"], level=[1000,850], steps=[0,3,6]) 


.. warning::
   É possível solicitar, em um mesmo pedido, **variáveis de superfície** e **variáveis de níveis**.  
   Dessa forma, o usuário pode combinar diferentes tipos de dados em uma única requisição ao modelo MONAN.