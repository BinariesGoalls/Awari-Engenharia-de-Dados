![header-awari.png](https://github.com/BinariesGoalls/Awari-Engenharia-de-Dados/blob/master/awari-header.png)

Esta é a tarefa proposta para a **Aula 6: Tratamento com MinIO e MongoDB**, do curso de **Engenharia de Dados** da **[Awari](https://awari.com.br/)**.

---

# O que fazer?
##### Com base no que foi visto em aula e com base nos dados e arquivos tratados na 5ª aula (aula anterior), a atividade consiste, sempre no workspace em Docker, em:

1. Criar script para ler os datasets em ./arquivos/ — o script deve:
    1. Criar uma pasta nomeada com a sigla da UF para cada estado encontrado no arquivo JSON;
    2. Organizar as cidades por estado um único arquivo CSV, nomeado como cidades.csv;
    3. Salvar esse arquivo cidades.csv dentro da pasta da UF (estado) correspondente.
2. Importar as pastas e arquivos salvos para um bucket no MinIO.
3. Exportar os dados para o MongoDB e visualizá-los a partir do banco de dados.

# Como fazer?

#### Acesse o console do MinIO e crie um bucket chamado aula-06:

```
http://127.0.0.1:9001/
```
#### Crie uma access key e aplique a policy de 'readwrite', salve as informações de access_key_id e secret_access_key (substitua no notebook onde necessário)

#### Siga os passos do arquivo:

```
aula-06-tarefa.ipynb
```
