## Resumo
* Essa é uma aplicação pensada a partir da nescessidade de preeencher repetidos dados no excel e informá-los à empresa em que trabalho.

  O transporte para a minha casa é feito por transporte por aplicativos, a AGl Brasil é quem paga esses valores quando os comprovantes são apresentados, afim de facilitar a coleta de dados pelo RH, eu decidi criar a tabela e jogar os valores para um melhor entendimento, já que se supõe que isso teria de ser feito de uma forma ou de outra, a tabela foi organizada da seguinte forma:
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

Os comprovantes gerados no aplicativo 99 são enviado ao meu email em formato HTML, para facilitar a coleta de dados foi desenvolvido essa aplicação.

# Introdução

#### *Os dados contidos aqui nesse repositório foram verificados e não há a nescessidade de cuidado para possíveis vazamentos*

* Quando enviados ao meu e-mail, o download ainda é feita de maneira manual, logo mais atualizarei essa parte da aplicação.

```
Clone este repositório e instale as dependencias -> requiriments.txt
```

# main.py

No arquivo principal definimos a classe main, onde teremos as funções `lerhtml`, `data`, `valor`, `origem`, `destino`, `método` e `categoria`, cada uma dessas funções tem a tarefa de entrar na raiz do html e buscar seus dados relativamente.