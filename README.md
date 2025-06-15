## Resumo
* Essa é uma aplicação pensada a partir da necessidade de preeencher repetidos dados no excel e informá-los ao RH da empresa [AGL Brasil](https://www.aglbrasil.com/).

  O transporte para a casa de funcionário é feito atráves de transporte por aplicativos, a [AGl Brasil](https://www.aglbrasil.com/) é quem paga esses valores quando apresentados os comprovantes. A fim de facilitar a coleta de dados pelo RH, a ideia de um desse funcionários foi criar uma tabela no excel e inserir os valores facilitando assim a coleta de dados por parte do setor de recursos humanos, partindo do pre-suposto que de alguma maneira alguém precisaria coletar esse dados para registro. A tabela foi organizada da seguinte forma:

### Estrutura da tabela no excel

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

#### *Os dados contidos nesse repositório foram verificados e não há a necessidade de cuidado para possíveis vazamentos*

* Quando enviados ao meu e-mail, o download ainda é feita de maneira manual, logo mais atualizarei essa parte da aplicação.

Clone este repositório, no bash instale as dependencias:
```
pip install requiriments.txt
```


# main.py

No arquivo principal definimos a classe main, onde se pode encontrar as funções `lerhtml`, `data`, `valor`, `origem`, `destino`, `método` e `categoria`, cada uma dessas funções tem a tarefa de entrar na raiz do html e buscar seus dados relativamente.

## lerhtml
* Na função `lerhtml` é onde usaremos a classe `BeautifulSoup` do módulo importado no início do código. A classe é instanciada em `soup` e a partir daí usamos a instância dessa classe para os elementos html que contém as informações que queremos exemplo de código.

### Raiz HTML

```
<tr>
  <td  style =  "padding:0;width:24px"></td>
    <td style="padding:40px 0 16px 0;" colspan="2">
      
        <span style="font-size: 14px;line-height:17px;color:#000000;">sex, 30 mai, 2025</span>
    </td>
  <td  style =  "padding:0;width:24px"></td>
</tr>
```

### Código na função data

```
def data(self, soup):
        data_td = soup.find("td", style="padding:40px 0 16px 0;")
        if data_td:
            span_data = data_td.find("span", style="font-size: 14px;line-height:17px;color:#000000;")
            if span_data:
                data = span_data.text.strip()
                return data
```

* Repare que ao passar `soup` como um parâmetro para a função data, o seu uso passará a ser indispensável para se conseguir navegar e coletar dados da raiz HTML. A mesma lógica será aplicada para coletar os demais dados nas outras funções.


# escrever_excel.py

* O arquivo `escrever_excel` será usado para injetarmos os dados dentro da nossa [tabela](#estrutura-da-tabela-no-excel) antes criada. Mesmo que tenhamos criado um construtor para a classe main deste arquivo, seu uso ainda não se fez necessário, assim tendo apenas o método `programa` que será chamado junto da classe quando se usar a aplicação, nesse caso alguns parâmetros serão passados, parâmetros esses usados para se escrever os dados na [tabela do excel](#estrutura-da-tabela-no-excel).

* Um arquivo csv também foi criado indicando de qual linha no excel os dados poderão ser insiridos para não se ter o incidente de dados serem acidentalmente serem sobescrevidos, ocasionando assim na perda total de dados importantes no arquivo, antes de iniciar o programa certifíque-se de que o índice está apontado para a linha de início desejada.

