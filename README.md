## Seja bem vindo ao Portifólio do Oz

You can use the [editor on GitHub](https://github.com/ozMoreira/inicial/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Acesse https://github.com/ozMoreira/inicial/blob/main/PingPong_nivel1.html para um jogo de Ping Pong
### Markdown

<html>
 <body>
   <canvas id="mesa" width="600" height="400"></canvas>

   <script>
    window.onload = function(){
      iniciar();
      setInterval(principal, 1000 / 30);
    }
    function iniciar(){
        folhaDesenho = document.getElementById("mesa");
        areaDesenho = folhaDesenho.getContext("2d");


        larguraCampo = 600;
        alturaCampo = 400;
        larguraLinha = 5;

        larguraBola = 5;

        alturaRaquete = 50;
        espessuraRaquete = 11;

        efeitoRaquete = 1;
        velocidadeJogador2 = 7;

        posicaoJogador1 = posicaoJogador2 = 40;
        posicaoBolaX = posicaoBolaY = 10;
        velocidadeBolaPosicaoX = velocidadeBolaPosicaoY = 10;
        pontuacaojogador1 = pontuacaoJogador2 = 0;

          folhaDesenho.addEventListener('mousemove', function(e){
            posicaoJogador1 = e.clientY - alturaRaquete / 2;
          });
      }

      function principal(){
        desenhar();
        calcular();
      }

      function desenhar(){
        //Criando Campo do Jogo
        areaDesenho.fillStyle ='#286047';
        areaDesenho.fillRect(0, 0, larguraCampo, alturaCampo);

        //Criando linha do campo
        areaDesenho.fillStyle = '#FFFFFF';
        areaDesenho.fillRect(larguraCampo / 2 - larguraLinha / 2, 0, larguraLinha, 400);

        //Raquete 1
        areaDesenho.fillRect(0, posicaoJogador1, espessuraRaquete, alturaRaquete);
        //Raquete 2
        areaDesenho.fillRect(larguraCampo-espessuraRaquete, posicaoJogador2, espessuraRaquete, alturaRaquete);

        areaDesenho.fillRect(posicaoBolaX - larguraBola / 2, posicaoBolaY - larguraBola / 2, larguraBola, larguraBola);
        areaDesenho.fillText("Humano - " + pontuacaojogador1 + "pontos", 100, 100);
        areaDesenho.fillText("Computador - " + pontuacaoJogador2 + "pontos", larguraCampo - 200 ,100);
      }

      function calcular(){
          posicaoBolaX = posicaoBolaX + velocidadeBolaPosicaoX;
          posicaoBolaY = posicaoBolaY + velocidadeBolaPosicaoY;

            //verifica lateral superior
            if (posicaoBolaY < 0 && velocidadeBolaPosicaoY < 0){
              velocidadeBolaPosicaoY = - velocidadeBolaPosicaoY;
            }

            //verifica lateral inferior
            if (posicaoBolaY > alturaCampo && velocidadeBolaPosicaoY >0){
              velocidadeBolaPosicaoY = - velocidadeBolaPosicaoY;
            }

            // verifica se o jogador 2 fez um ponto
            if (posicaoBolaX < 0){
              if(posicaoBolaY > posicaoJogador1 && posicaoBolaY < posicaoJogador1 + alturaRaquete){

              //rebate bola
              velocidadeBolaPosicaoX = - velocidadeBolaPosicaoX;

              var diferencaY = posicaoBolaY - (posicaoJogador1  + alturaRaquete / 2);
              velocidadeBolaPosicaoY = diferencaY * efeitoRaquete;
              }  else  {

              //ponto jogador 2
              pontuacaoJogador2 ++;

              // Reseta posicao inicial da bola apos ponto
              continuar();
              }
            }

            //Verifica se o jogador 1 fez pontos
            if (posicaoBolaX > larguraCampo){
              if (posicaoBolaY > posicaoJogador2 && posicaoBolaY < posicaoJogador2 + alturaRaquete){

                // rebater a larguraBola
                velocidadeBolaPosicaoX = - velocidadeBolaPosicaoX;

            var diferencaY = posicaoBolaY - (posicaoJogador2 + alturaRaquete / 2);
            velocidadeBolaPosicaoY = diferencaY * efeitoRaquete;
            }  else  {

            // ponto jogador 1
            pontuacaojogador1++;

            // Reseta posicao inicial da bola apos ponto
            continuar();
            }
          }

          if (posicaoJogador2 + alturaRaquete / 2 < posicaoBolaY){
            posicaoJogador2 = posicaoJogador2 + velocidadeJogador2;
          }  else  {
            posicaoJogador2 = posicaoJogador2 - velocidadeJogador2;
          }
        }
      function continuar(){
        posicaoBolaX = larguraCampo / 2;
        posicaoBolaY = alturaCampo / 2;
        velocidadeBolaPosicaoX = - velocidadeBolaPosicaoX;
        velocidadeBolaPosicaoY = 3;
      }

     </script>
   </body>
</html>
Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ozMoreira/inicial/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
