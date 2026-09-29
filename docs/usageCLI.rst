Como Usar CLI
=========

CLI
------

# O que significa CLI

**CLI** é a sigla para **Command Line Interface** (*Interface de Linha de Comando*).

## 🔹 O que é CLI
- É uma forma de interagir com programas digitando comandos em um terminal ou console.
- Diferente de uma interface gráfica (GUI), o usuário escreve instruções em texto.
- É muito usada em ambientes de desenvolvimento, servidores e ferramentas técnicas porque permite automação e rapidez.

## 🔹 Exemplos práticos
- **[Git](ca://s?q=Git_CLI_comandos)** → `git clone`, `git commit`, `git push`
- **[Conda](ca://s?q=Conda_CLI_comandos)** → `conda install pacote`
- **[Pip](ca://s?q=Pip_CLI_comandos)** → `pip install cptec-monan`
- **MONAN (via CLI)** →  
  ```bash
  monan_load --date 2026-09-28 --variable t2m
  ```

# Opções do CLI `monan_load`

O comando `monan_load` permite acessar e baixar dados do MONAN diretamente pela linha de comando.  
Abaixo estão as principais opções:

## 🔹 Opções gerais
- **`-h, --help`**  
  Mostra a ajuda e encerra.

- **`--date DATE, -d DATE`**  
  Define a data da condição inicial no formato `YYYYMMDDHH`.  
  Exemplo: `--date 2026092800`

## 🔹 Controle de steps
- **`--steps STEPS [STEPS ...], -s STEPS [STEPS ...]`**  
  Lista de steps específicos.  
  Exemplo: `--steps 0 3 6`

- **`--range RANGE, -r RANGE`**  
  Define o step máximo para baixar de `0` até `N`.  
  Exemplo: `--range 12`

## 🔹 Variáveis e níveis
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

## 🔹 Áreas e shapes
- **`--shape SHAPE, -shp SHAPE`**  
  Define a abreviação da área (shape).  
  Exemplo: `--shape estados_sp`

- **`--areas {continentes,paises,regioes,estados,bacias,biomas}`**  
  Lista as áreas disponíveis por tipo.  
  Exemplo: `--areas estados`

## 🔹 Saída
- **`--prefix PREFIX, -p PREFIX`**  
  Prefixo do nome do arquivo NetCDF salvo (default: `MONAN`).  
  Exemplo: `--prefix MEUARQUIVO`

- **`--path PATH, -o PATH`**  
  Diretório de saída onde os arquivos NetCDF serão salvos (default: diretório atual).  
  Exemplo: `--path ./dados`

---

## 🔹 Exemplos de uso

### Baixar variáveis de superfície
```bash
monan_load --date 2026092800 --var t2m u10m v10m --steps 0 3 6 --shape estados_sp
```





