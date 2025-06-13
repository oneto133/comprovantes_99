## Resumo
* Essa é uma aplicação pensada a partir da necessidade de preeencher repetidos dados no excel e informá-los ao RH da empresa [AGL Brasil](https://www.aglbrasil.com/).

  O transporte para a casa de funcionário é feito atráves de transporte por aplicativos, a [AGl Brasil](https://www.aglbrasil.com/) é quem paga esses valores quando apresentados os comprovantes. A fim de facilitar a coleta de dados pelo RH, a ideia de um desse funcionários foi criar uma tabela no excel e inserir os valores facilitando assim a coleta de dados por parte do setor de recursos humanos, partindo do pre-suposto que de alguma maneira alguém precisaria coletar esse dados para registro. A tabela foi organizada da seguinte forma:


<table>
  <thead>
    <tr>
      <th>Data</th>
      <th>Origem</th>
      <th>Destino</th>
      <th>Método</th>
      <th>Categoria</th>
      <th>Valor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>sex, 2 mai, 2025</td>
      <td>Agl, Segurança Eletrônica, 09:11 PM</td>
      <td>Rua das seringueiras, 480, 09:23 PM</td>
      <td>Cartão de Crédito/Débito</td>
      <td>Moto</td>
      <td>R$ 5,30</td>
    </tr>
    <tr>
      <td>sab, 3 mai, 2025</td>
      <td>Agl, Segurança Eletrônica, 09:20 PM</td>
      <td>Rua das seringueiras, 480, 09:34 PM</td>
      <td>Cartão de Crédito/Débito</td>
      <td>Moto</td>
      <td>R$ 4,60</td>
    </tr>
  </tbody>
</table>

Os comprovantes gerados no aplicativo 99 são enviado ao e-mail do solicitante em formato HTML, a coleta de dados entao foi feita usando a linguagem python com o framework `bs4`.

# Introdução

[!IMPORTANT]
#### *Os dados contidos nesse repositório foram verificados e não há a necessidade de cuidado para possíveis vazamentos*

* Quando enviados ao meu e-mail, o download ainda é feita de maneira manual, logo mais atualizarei essa parte da aplicação.

Clone este repositório, no bash instale as dependencias:
```
pip install requiriments.txt
```


# main.py

No arquivo principal definimos a classe main, onde teremos as funções `lerhtml`, `data`, `valor`, `origem`, `destino`, `método` e `categoria`, cada uma dessas funções tem a tarefa de entrar na raiz do html e buscar seus dados relativamente.

