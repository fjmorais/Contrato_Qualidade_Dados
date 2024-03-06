# Como fazer Contrato de Dados (Qualidade de Dados)

Ao se falar de Qualidade de Dados e a sua implementação, seria garantir que os dados sempre estejam disponíveis e sejam confiáveis.

Nesse workshop, será feito uma ETL em Python, inserindo o processo de DataQuality. Esse ETL teremos uma consulta em uma API JSON e salvar os dados em um banco de dados PostGres SQL.

Para fazer esse ETL com o contrato de dados, vamos usar o Pandera ou o Pydantic.



![alt text](pic/01_image.png)

Figura 01 - Contrato de dados usando o Pydantic ou o Pandera.

### Qual a diferença do Pydantic e do Pandera ?

Ambas são para validação dos dados no início do processo de contrato de dados. Porém o Pandera, é mais indicado para alto volume de processamento de dados e para tempo real (Indicado para Big Data).

Uma ótima representação do uso do Pydantic e do Pandera no início do processo de ETL. Porém, normalmente, essa validação é feito no processo de LOAD. Sendo que o contrato de dados busca em fazer essa validação já na extração. Na camada de LOAD, a gente fica muito reativo. Fazendo na extração, poderemos fazer no início do processo.

![alt text](pic/02_image.png)

Figura 02 - Contrato de dados na camada de Load e seus exemplos de ferramentas.

# Começando o projeto de contrato de dados (Qualidade dos dados)


1 - Criando um repositório do Zero - Acessar o Git hub, criar um repositório público, obter os códigos para executar no terminal e assim atribuir a pasta do projeto ao github.

![alt text](pic/03_image.png)

Figura 03 - Criando o Github na pasta do projeto.


![alt text](pic/04_image.png)

Figura 04 - Checklist do projeto.


![alt text](pic/05_image.png)

Figura 05 - PDF com o Checklist de todo projeto.


2 - Pyenv - permitir você trabalhar com multiplas versões de python. Para cada projeto que você for desenvolver, no nível de pasta será possível utilizar uma versão específica. Porém, como escolher a versão do pyenv para utilizar (versão do python) ? Fazer o brainstrom das ferramentas do projeta e escolher a versão do pyenv que vai atender a essas ferramentas. No nosso caso, vamos usar o Pydanitc, Pandera, Pandas, Dask e o DuckDB. Dessas todas, o pandera é a única que ainda não foi atualizada para o python 3.12. Com isso, vamos usar a versão 3.11.


![alt text](pic/06_image.png)

Figura 06 - Por causa do Pandera, vamos usar a versão 3.11 do Python.


Selecionando a versão mais avançada para o 3.11. que é a 3.11.5.

![alt text](pic/07image.png)

Figura 07 - Na pasta do projeto, selecionar o pyenv local 3.11.5

Com a execução do comando pyenv local, automaticamente é criado um arquivo .python-version no projeto.

![alt text](pic/08image.png)

Figura 08 - Arquivo .python-version

3 - Depois de escolher versão do pyenv adequada, é chegada a hora de fazer o uso do poetry. Executar o poetry init.

![alt text](pic/09image.png)

Figura 09 - Executando o comando poetry init na pasta do projeto e clicar enter em todos os passos para deixar em branco as opções.

Com o poetry init executado, automaticamente é criado uma pasta pyproject.toml, com as informações do projeto.

![alt text](pic/10image.png)

Figura 10 - Arquivo pyproject.toml.

IMPORTANTE: Para usar o ambinete virtual local com o poetry, é preciso executar o comando poetry shell na pasta do projeto e assim automaticamente será criado uma pasta .venc para desenvolvimento.

![alt text](pic/11image.png)

Figura 11 - Comando poetry shell.

4 - Instalação do mkdocs. Biblioteca para fazer a documentação do projeto. 

Criar o arquivo do gitignore, só para não ter de enviar arquivos indesejados para o repositório do github. Existe um site que informa todos os arquivos que não devem ser enviados para o github. Acessar a página git total e informar para lista o padrão do gitigone para python.

![alt text](pic/12image.png)

Figura 12 - Gitignore para Python.


Instalação da biblioteca do mkdocs. Nesse caso vamos usar o poetry para fazer as instalações, pois esses softwares só existirão em nível de projeto. Usar o comando poetry add.

![alt text](pic/13image.png)

Figura 13 - Poetry add mkdocs.

Para começar a usar o mkdocs, pasta executar o comando mkdocs new. e automaticarmente será criado uma pasta docs no projetos.

![alt text](pic/14image.png)

Figura 14 - Iniciando o mkdocs com o comando "mkdocs new ."

Em outra janela do bash, executar comando "poetry run mkdocs serve" para iniciar o mkdocs.

![alt text](pic/15image.png)

Figura 15 - Acessando a UI do mkdocs.

Acessar a página que está renderizando o arquivo index.md:

![alt text](pic/16image.png)

Figura 16 - Acesso ao UI Web do mkdocs com as informações do arquivo index.md.

### Dica de como fazer uma documentação rápida no mkdocs.

Usar a extensão chamada "mermaid" para ajudar a fazer os organogramas para o mkdocs. Acessar o site:

![alt text](pic/17image.png)

Figura 17 - Acessar o site da mermaid.

Fazer a instalação do mermaid para o mkdocs:

![alt text](pic/18image.png)

Figura 18 - Instalação do plugin entre aspas.

Modificar o arquivo mkdocs.yml para ficar da forma abaixo:

![alt text](pic/19image.png)

Figura 19 - Ajuste do arquivo yml.

![alt text](pic/20image.png)

Figura 20 - Ajuste do arquivo yml.

O que já podemos fazer com o mermaid em execução ? 

Vamos obter um exemplo de fluxograma e informar no modo mermaid.

Exemplo de um digrama do mermaid:

![alt text](pic/21image.png)

Figura 21 - Diagrama do mermaid.

Inserir o arquivo no index.md:


![alt text](image.png)

Figura 22 - Arquivo index.md com o diagrama mermaid.


![alt text](pic/23image.png)

Figura 23 - Executar o poetry run mkdocs serve


![alt text](pic/24image.png)

Figura 24 - Página com o diagrama documentado.


Outro ponto muito importante, pois tem uma extensão do excalidraw que transforma o desenho do mesmo e transforma em mermaid.

Selecionar o triangulo e inserir o comando mermaid nesse board:

![alt text](image.png)

Figura 25 - Excalidraw reconhecendo o mermaid.

**ATENÇÃO**:Convertendo um fluxograma feito no excel para ser inserido no mkdocs usando o mermaid. Copiar o fluxograma do excel e inserir o chat gpt e solictar para ele converter para mermaid.

5 - Fazer a instalação do mkdocs material, para adequar o layout do mkdocs.

![alt text](pic/26image.png)

Figura 26 - mkdocs material.

Editar o arquivo mkdocs.yml para reconhecer o thema mkdocs material:

![alt text](pic/27image.png)

Figura 27 - Editando o arquivo mkdocs.yml para reconhecer o novo tema.

6 - Incluindo o plugin docstring.

Instalação do mkdocs string:

![alt text](pic/28image.png)

Figura 28 - No nosso exemplo não precisa do pacote cristal.

![alt text](pic/29image.png)

Figura 29 - Editando o arquivo mkdocs.yml para reconhecer o mkdocsstring.

7 - Instalalação do Taskpi.

Excecutar o comando poetry shell em caso de novo terminal e em seguida, executar poetry add taskpy.

![alt text](pic/30image.png)

Figura 30 - Instalando o taskpi.

### Para que ser o Taskpy ?

Para comando que precisa ficar executando a todo momento, o taskpy ajuda automatizar essas repetiçoes.

Editar o arquivo pyproject.toml e inserir os comandos abaixo:

![alt text](image.png)

Figura 31 - Editando o pyproject file para usar o taskpi.

```python
[tool.taskipy.tasks]
format = """
isort .
black .
"""
kill = "kill -9 $(lsof -t -i :8000)"
test = "pytest -v"
run = """
python3 app/main.py
"""
doc = "mkdocs serve"
```

# PAREI NO MINUTO 29:54