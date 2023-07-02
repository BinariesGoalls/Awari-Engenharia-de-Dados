![header-awari.png](https://github.com/BinariesGoalls/Awari-Engenharia-de-Dados/blob/master/awari-header.png)

Esta é a tarefa proposta para a **Aula 7: Batch, Diferencial e Kafka Streaming**, do curso de **Engenharia de Dados** da **[Awari](https://awari.com.br/)**.

---

# O que fazer?
##### Com base no que foi visto em aula e no Docker do curso, fazer o seguinte:

1. Importar as diferenças que são criadas nos dados da pasta /municipios-estados. A cada vez que um novo arquivo for adicionado neste diretório, os dados do mesmo devem ser importados para uma pasta da UF correspondente em um bucket no MinIO e adicionado ao fim do arquivo cidades.csv.
2. Utilizar Apache Kafka para fazer o mesmo processo, mas de maneira automatizada.

# Detalhes:

O script <code>extrator_dados.py</code> captura os dados de uma base de dados MongoDB (criada e populada préviamente na tarefa da Aula 06), divide em pequenos lotes (para simular vários arquivos sendo adicionados em tempos diferentes) e salva em arquivos CSV. Em seguida, envia o nome desses arquivos para o Kafka para que estes sejam processados posteriormente.

O script <code>processa_dados.py</code> consome mensagens que contêm nomes de arquivos a serem processados, enviadas pelo script anterior, processa os dados desses arquivos, e insere as informações em um arquivo .csv da UF correspondente localizado um bucket criado na ferramenta minIO.

# Como fazer?

#### Acesse o console do MinIO e crie um novo bucket chamado aula-07:

```
http://127.0.0.1:9001/
```

#### Utilizando o PowerShell navegue até o diretório que contém o script <code>extrator_dados.py</code>.
Execute o script usando o comando abaixo: 

```
docker compose -f docker-compose-por-aula/aula-07.yml run python-app sh -c "python ./app/aula-07/tarefa/scripts/extrator_dados.py"
```

#### Em uma outra janela do PowerShell, navegue até o mesmo diretório, que contém o script <code>processa_dados.py</code>.
Execute o script usando o comando abaixo: 

```
docker compose -f docker-compose-por-aula/aula-07.yml run python-app sh -c "python ./app/aula-07/tarefa/scripts/processa_dados.py"
```


#### Verifique os dados sendo carregados:

* Durante a execução dos scripts, você pode verificar os dados sendo processados na janela de execução do próprio script <code>processa_dados.py</code>.
  
* Você também pode verificar os dados sendo inseridos no MinIO. Vá para a interface da web do MinIO, clique no bucket "aula-07" e você deve ver os arquivos CSVs sendo atualizados.
  
* Você tambéem pode verificar as mensagens sendo enviadas para a fila do Kafka para processamento através da interface gráfica configurada acessando:

```
http://127.0.0.1:9099/
```

# Tecnologias Utilizadas

* Python
* Pandas
* MongoDB
* Kafka
* MinIO
