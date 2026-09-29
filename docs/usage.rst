Como Usar
=========

Acesso aos dados MONAN
======================

Na nova versão dos pacotes de distribuição dos **Modelos Numéricos MONAN**, oferecemos duas formas de acessar, filtrar e receber os dados:

- `Interface de Linha de Comando (CLI) <usageCLI>`_  
  A maneira mais recente e prática, permitindo interação direta com o sistema.

- `Biblioteca Python <usagePython>`_  
  O método tradicional, que continua disponível para quem prefere integrar o MONAN em seus scripts e aplicações.


# CLI vs Biblioteca Python

| Aspecto               | **[CLI](ca://s?q=Quando_usar_CLI_MONAN)**                              | **[Biblioteca Python](ca://s?q=Quando_usar_biblioteca_Python_MONAN)** |
|------------------------|------------------------------------------------------------------------|------------------------------------------------------------------------|
| **Facilidade de uso**  | Comandos prontos, sem necessidade de programação                       | Requer conhecimento de Python e bibliotecas científicas                |
| **Velocidade**         | Ideal para tarefas rápidas e repetitivas                               | Mais detalhado, mas flexível                                           |
| **Automação**          | Scripts de shell e pipelines simples                                   | Integração em projetos complexos e notebooks                           |
| **Flexibilidade**      | Limitada aos parâmetros disponíveis                                    | Total, com uso de `numpy`, `pandas`, `xarray` e outras ferramentas     |
| **Perfil do usuário**  | Usuários menos técnicos ou que querem praticidade                      | Pesquisadores e desenvolvedores que precisam controle total            |
| **Exemplo de uso**     | `monan_load --date 2026-09-28 --variable t2m --output ./dados`         | `dados = CPTEC_MONAN(date="2026-09-28").get_variable("t2m")`           |
