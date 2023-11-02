# Projeto criado para servir como base dos cursos de Python com Flask

Projeto criado como base para treinamentos dos cursos da **ALURA**

## Ambiente

1. Linux Ubuntu 22.04
2. VSCode 1.84.4
3. Python 3.10.12

## Desenvolvendo a aplicação

:warning: 
Utilizar ambiente virtual para desenvolvimento
:warning:

1. `python3 -m venv venv`
2. `source venv/bin/activate`

Antes de começar o projeto é necessário instalar as dependências da aplicação rodando o comando: 

`pip install requirements.txt`

## Rodando o aplicativo

Para executar o palicativo devemos rodar o comando: `python codigo/jogoteca.py` e acessar o endereço `localhost:5000/inicio` no navegador

## Testes

Comandos para rodar os testes

`pytest`

Comando para rodar testes com cobertura em todas as pastas do projeto

`pytest --cov`

definindo a pasta código (que contém os códigos da aplicação), e a pasta **tests/** que contém os testes

`pytest --cov=codigo tests/`

para gerar os testes de cobertura e informar as linhas faltantes na cobertura dos testes

`pytest --cov=codigo tests/ --cov-report term-missing`

para incluir os arquivos de cobertura em uma página html (será gerado um arquivo index.html na pasta *htmlcov*)

`pytest --cov=codigo tests/ --cov-report html`

## Personalizando coverage

Incluir configurações de cobertura de testes (coverage) para excluir testes desnecessários

1. criar o arquivo .coveragerc e personalizar conforme demanda

2. para personalizar o comando de testes com cobertura de código devemos incluir o *source* no arquivo **.coveragerc** informando a pasta que contém os arquivos que queremos gerar a cobertura, no nosso caso a pasta *codigo* no diretório *raiz*

```
[run]
source = ./codigo
```

3. para excluir testes devemos editar o arquivo *.coveragerc* incluindo as linhas a seguir:

Obs.: excluímos o teste do método *str*

```
[run]
source = ./codigo

[report]
exclude_lines =
    def __str__
```

4. para alterar a pasta padrão onde será armazenado o relatório html devemos incluir no arquivo *.coveragerc* o trecho conforme exemplo a seguir, no meu caso os relatórios html serão salvos na pasta *coverage_relatorio_html*

```
[run]
source = ./codigo

[report]
exclude_lines =
    def __str__

[html]
directory = coverage_relatorio_html
```

## Personalizando marcações nos testes

Incluir a configuração dos testes para aceitar marcações nos testes **@mark**

1. Criar o arquivo pytest.ini

2. incluir no arquivo a seguinte configuração:

```
[pytest]
markers =
    calcular_bonus: Teste para o método calcular_bonus
```

3. Podemos também incluir uma configuração no arquivo pytest.ini para rodar as flags de cobertura de testes incluindo a geração do arquivo html. Para esta configuração devemos alterar o arquivo *pytest.ini* conforme exemplo a seguir:

```
[pytest]
addopts = -v --cov=codigo tests/ --cov-report html
markers =
    calcular_bonus: Teste para o método calcular_bonus
```