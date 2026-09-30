Interface de Linha de Comando (CLI)
=============

**O que é CLI**
- É uma forma de interagir com programas digitando comandos em um terminal ou console.
- Diferente de uma interface gráfica (GUI), o usuário escreve instruções em texto.
- É muito usada em ambientes de desenvolvimento, servidores e ferramentas técnicas porque permite automação e rapidez.

**Exemplos práticos**

- **[Git]** → `git clone`, `git commit`, `git push`

- **[Conda]** → `conda install pacote`

- **[Pip]** → `pip install cptec-monan`

- **MONAN (via CLI)** → `monan_load --date 2026-09-28 --var t2m`


Opções do CLI `monan_load`
--------------------------

O comando `monan_load` é a interface de linha de comando para acessar e baixar dados do **MONAN**.  

Ele oferece um conjunto completo de parâmetros que permitem configurar **data de inicialização**, **steps de previsão**, **variáveis e níveis atmosféricos**, **recortes espaciais (shapes)** e **opções de saída**.  

A seguir estão as opções disponíveis, organizadas por categoria:


Opções gerais
-------------

- **`-h, --help`**  

  Mostra a ajuda e encerra.

- **`--date DATE, -d DATE`**  

  Define a data da condição inicial no formato `YYYYMMDDHH.  
  Exemplo: `--date 2026092800`

Controle de steps
-----------------

- **`--steps STEPS [STEPS ...], -s STEPS [STEPS ...]`**  
  
  Lista de steps específicos.  
  Exemplo: `--steps 0 3 6`

- **`--range RANGE, -r RANGE`**  
  
  Define o step máximo para baixar de `0` até `N`.  
  Exemplo: `--range 12`

Variáveis e níveis
------------------

- **`--var VAR [VAR ...], -v VAR [VAR ...]`**  
  
  Variáveis a carregar.  
  Exemplo: `--var t2m u v`

- **`--level LEVEL [LEVEL ...], -l LEVEL [LEVEL ...]`**  
  
  Níveis a carregar.  
  Exemplo: `--level 1000 850`

- **`--list_levels`**  
  
  Lista todos os níveis disponíveis.

- **`--list_vars`**  
  
  Lista todas as variáveis disponíveis.

Áreas e shapes
--------------

- **`--shape SHAPE, -shp SHAPE`**  
  
  Define a abreviação da área (shape).  
  Exemplo: `--shape estados_sp`

- **`--areas {continentes,paises,regioes,estados,bacias,biomas}`**  
  
  Lista as áreas disponíveis por tipo.  
  Exemplo: `--areas estados`

Saída / Output arquivo
----------------------

- **`--prefix PREFIX, -p PREFIX`**  
  
  Prefixo do nome do arquivo NetCDF salvo (default: `MONAN`).  
  Exemplo: `--prefix MEUARQUIVO`

- **`--path PATH, -o PATH`**  
  
  Diretório de saída onde os arquivos NetCDF serão salvos (default: diretório atual).  
  Exemplo: `--path ./dados`


Exemplos de uso
---------------

**Baixar variáveis de superfície**

$ monan_load --date 2026092800 --var t2m u10m v10m --steps 0 3 6 --shape estados_sp

**Baixar variáveis de niveis (1000/850)**

$ monan_load --date 2026092800 --var t u v --levels 1000 850 --steps 0 3 6

.. warning::
   É possível solicitar, em um mesmo pedido, **variáveis de superfície** e **variáveis de níveis**.  
   Dessa forma, o usuário pode combinar diferentes tipos de dados em uma única requisição ao modelo MONAN.




