Como Usar
=========

Acesso aos dados MONAN
----------------------

Na nova versão dos pacotes de distribuição dos **Modelos Numéricos MONAN**, oferecemos duas formas de acessar, filtrar e receber os dados:

- `Interface de Linha de Comando (CLI) <usageCLI.html>`_ 
  - a maneira mais recente e prática, permitindo interação direta com o sistema.

- `Biblioteca Python <usagePython.html>`_  - 
  o método tradicional, que continua disponível para quem prefere integrar o MONAN em seus scripts e aplicações.


Comparativo: CLI vs Biblioteca Python
-------------------------------------

.. image:: _static/AspectosCLI_Python.png
   :width: 90%
   :align: center

.. note::

Horários de inicialização do modelo MONAN
------------------------------------------

  O modelo **MONAN** roda com dois horários de inicialização principais:

  - **00 UTC** → fornece previsões de até **11 dias**.  
  - **12 UTC** → fornece previsões de até **5 dias**.

  Para acessar uma inicialização especifica utilizar a opção `date`.

  **date = 'YYYYMMDD' ou date = 'YYYYMMDDHH'**

.. note::

  Caso não informar **HH** - usa o default **00 UTC**

  Caso não informar a opção **date** usa a data atual como default


Intervalo de previsão do MONAN
------------------------------

  O modelo **MONAN** gera saídas em intervalos regulares de tempo.  
  Cada **step** corresponde a uma previsão com avanço de **3 horas** em relação ao anterior.

  Isso significa que os dados disponíveis seguem a sequência: 0h, 3h, 6h, 9h, 12h, e assim por diante, até o limite definido pela inicialização (00 UTC ou 12 UTC).

  - **00 UTC** → fornece previsões de até **264 horas**.  
  - **12 UTC** → fornece previsões de até **120 horas**.

  Dessa forma, o número máximo de steps é:

  - **264** para o modelo inicializado às **00 UTC**. 

  - **120** para o modelo inicializado às **12 UTC**.


- **Step único** → define até quantas horas de previsão serão baixadas.  

  steps = **<int>**

  Exemplo: `steps = 6` → retorna os steps **0, 3 e 6**.

.. warning::
  Usando a Interface de Linha de Comando (CLI) essa opção é a ``--range RANGE, -r RANGE``.
  Exemplo: ``--range 6`` → retorna os steps **0, 3 e 6**.

- **Lista de steps** → permite especificar exatamente quais steps serão baixados.  

  steps = **<list>**

  Exemplo: `steps = [0, 3, 6]` → retorna apenas os steps **0, 3 e 6**.
  

