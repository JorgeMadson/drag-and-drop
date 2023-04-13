
# Tutorial drag-and-drop
Vamos começar do início com um tutorial passo a passo detalhado para criar uma funcionalidade de arrastar e soltar imagens usando JavaScript.

[Exemplo em funcionamento](https://jorgemadson.github.io/drag-and-drop/)

## Passo 1:
Configurando o HTML básico Começamos criando um arquivo HTML básico com três divs: duas divs de imagem e uma div de área de destino. Cada div de imagem terá um ID único para que possamos identificá-las no JavaScript. A div de área de destino também terá um ID único para referenciá-la posteriormente. Além disso, adicionamos algumas classes CSS para estilizar as divs de imagem e a div de área de destino:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Arrastar e Soltar Imagens</title>
    <style>
      .imagem {
        width: 100px;
        height: 100px;
        border: 1px solid #000;
        margin: 10px;
        padding: 10px;
        display: inline-block;
      }
      .area-de-destino {
        width: 300px;
        height: 200px;
        border: 1px dashed #000;
        padding: 10px;
      }
    </style>
  </head>
  <body>
    <img src="imagem1.png" alt="Minion" id="imagem1" class="imagem" draggable="true" />
    <img src="imagem2.png" alt="Cogumelo do Mário" id="imagem2" class="imagem" draggable="true" />
    <div id="areaDeDestino" class="area-de-destino">Área de Destino</div>
    <!-- JavaScript será adicionado posteriormente -->
  </body>
</html>
```

## Passo 2:
Adicionando atributos "draggable" Em cada div de imagem, adicionamos o atributo HTML5 "draggable" com o valor "true" para torná-las arrastáveis. Isso permite que as imagens sejam arrastadas pelo usuário.

## Passo 3:
Criando ouvintes de eventos de "dragstart" Agora, precisamos adicionar ouvintes de eventos de "dragstart" para cada div de imagem. Esses ouvintes de eventos serão acionados quando o usuário começar a arrastar uma imagem. No JavaScript, adicionamos o seguinte código:


```javascript
var imagem1 = document.getElementById("imagem1");
var imagem2 = document.getElementById("imagem2");
imagem1.addEventListener("dragstart", function (event) {
  event.dataTransfer.setData("text/plain", event.target.id);
});
imagem2.addEventListener("dragstart", function (event) {
  event.dataTransfer.setData("text/plain", event.target.id);
});
```

Nesse código, selecionamos as divs de imagem usando o método "getElementById" e atribuímos ouvintes de eventos de "dragstart" a cada uma delas. No evento de "dragstart", usamos o método "setData" do objeto "dataTransfer" para armazenar o ID da imagem que está sendo arrastada. Isso nos permitirá identificar a imagem posteriormente quando for solta na área de destino.

## Passo 4:
Criando ouvintes de eventos de "dragover" e "drop" Agora, precisamos adicionar ouvintes de eventos de "dragover" e "drop" à div de área de destino. O evento de "dragover" será acionado quando o usuário estiver arrastando uma imagem sobre a área de destino, e o evento de "drop" será acionado quando o usuário soltar a imagem na área de destino. No JavaScript, adicionamos o seguinte código:

```javascript
var areaDeDestino = document.getElementById("areaDeDestino");
areaDeDestino.addEventListener("dragover", function (event) {
  event.preventDefault();
});
areaDeDestino.addEventListener("drop", function (event) {
  event.preventDefault();
  var imagemId = event.dataTransfer.getData("text/plain");
  var imagem = document.getElementById(imagemId);
  areaDeDestino.appendChild(imagem);
});

```

Nesse código, selecionamos a div de área de destino usando o método "getElementById" e atribuímos ouvintes de eventos de "dragover" e "drop" a ela. No evento de "dragover", usamos o método "preventDefault" para evitar o comportamento padrão do navegador de não permitir a soltura de elementos arrastáveis em uma área de destino. No evento de "drop", usamos o método "preventDefault" novamente para evitar o comportamento padrão do navegador de abrir a imagem em uma nova guia. Em seguida, usamos o método "getData" do objeto "dataTransfer" para obter o ID da imagem que está sendo solta na área de destino. Com o ID da imagem, podemos selecionar a imagem usando o método "getElementById" e, em seguida, usamos o método "appendChild" para movê-la para a div de área de destino.

## Passo 5:
Testando a funcionalidade Agora que todo o código está configurado, você pode abrir o arquivo HTML em um navegador e testar a funcionalidade de arrastar e soltar imagens. Você deve ser capaz de arrastar as imagens "Imagem 1" e "Imagem 2" para a área de destino e vê-las sendo movidas para lá quando soltas.

Espero que este tutorial tenha sido útil para você entender como criar uma funcionalidade de arrastar e soltar imagens usando JavaScript. Com esses passos detalhados, os alunos mais novos devem ser capazes de seguir e entender bem o processo.
