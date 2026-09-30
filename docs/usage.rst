# Como Usar Biblioteca Python

## Acesso aos dados MONAN

Na nova versão dos pacotes de distribuição dos **Modelos Numéricos MONAN**, oferecemos duas formas de acessar, filtrar e receber os dados:

- [Interface de Linha de Comando (CLI)](usageCLI.html)  
  A maneira mais recente e prática, permitindo interação direta com o sistema.

- [Biblioteca Python](usagePython.html)  
  O método tradicional, que continua disponível para quem prefere integrar o MONAN em seus scripts e aplicações.


# Comparativo: CLI vs Biblioteca Python

| Aspecto               | **[CLI](ca://s?q=Quando_usar_CLI_MONAN)**                              | **[Biblioteca Python](ca://s?q=Quando_usar_biblioteca_Python_MONAN)** |
|------------------------|------------------------------------------------------------------------|------------------------------------------------------------------------|
| **Facilidade de uso**  | Comandos prontos, sem necessidade de programação                       | Requer conhecimento de Python e bibliotecas científicas                |
| **Velocidade**         | Ideal para tarefas rápidas e repetitivas                               | Mais detalhado, mas flexível                                           |
| **Automação**          | Scripts de shell e pipelines simples                                   | Integração em projetos complexos e notebooks                           |
| **Flexibilidade**      | Limitada aos parâmetros disponíveis                                    | Total, com uso de `numpy`, `pandas`, `xarray` e outras ferramentas     |
| **Perfil do usuário**  | Usuários menos técnicos ou que querem praticidade                      | Pesquisadores e desenvolvedores que precisam controle total            |
| **Exemplo de uso**     | `monan_load --date 2026-09-28 --variable t2m --output ./dados`         | `dados = CPTEC_MONAN(date="2026-09-28").get_variable("t2m")`           |


.. note::

  **Horários de inicialização do modelo MONAN**

  date = 'YYYYMMDD' ou
  date = 'YYYYMMDDHH' - não informar HH usa o default **00 UTC**
  

  O modelo **MONAN** roda com dois horários de inicialização principais:

  - **00 UTC** → fornece previsões de até **11 dias**.  
  - **12 UTC** → fornece previsões de até **5 dias**.

  Dessa forma, o usuário pode escolher entre uma previsão mais longa (00 UTC) ou uma previsão mais curta e atualizada (12 UTC), conforme sua necessidade.


.. note::

  **Definição de Steps**

  steps = **<int>**
  
  Define o número de steps que serão pedidos
  
  Ex. steps = ``6``
  
  O pedido será os steps ``0,3,6``
  
  steps = **<list>**
  
  Define os steps que serão pedidos 

  Ex. steps =  ``[0,3,6]``
  O pedido será os steps específicos pedidos ``0,3,6,9``

