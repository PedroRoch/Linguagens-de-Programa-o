
# PSET 0 

## Jogo de Ritmo criado em Scrath

--- 

**Aluno:** Pedro Lucas da Rocha Barros

**Professor:** Abrantes Araújo Silva Filho

**Turma:** CC3M

---

# Introdução

Este trabalho foi feito ao longo de duas semanas, consegui desenvolver bem e entender cada função "existente" no Scrath, obivamente não tudo mas quase...
Bem, decidi criar um jogo de ritmo pela minha paixão de jogar esses tipos de jogos, embora o jogo esteja simples e sem musica que seria o intuito de um jogo de música, foi gratificante tentar faze-lo

Jogo se baseia muito em jogos de fliperama onde tem aquelas pistas de dança onde contém setas e você deve pisar para sincronizar com a batida na tela, nesses jogos existem setas onde caem e o jogador deve apertar no momento exato

Explicado isso, vamos ao jogo

---

## O jogo

![ezgif com-video-to-gif](https://user-images.githubusercontent.com/103005263/221083933-e2103999-4397-45af-9ac4-74fc5a867491.gif)

Pela imagem mostrada acima é bem simples de entender, as teclas são criadas aleatoriamente, você deve apertar as setas do teclado no momento exato quando a tecla colorida se aproxima da tecla preta

Existe uma pontuação, que toda vez que você acerta ganha um ponto, quando você erra, pontos são retirados de você, quando chega a 11 de pontuação a dificuldade do jogo começa a aumentar, onde começa a aparecer mais teclas para apertar ao mesmo tempo, quando chega a 21 de pontuação o jogo aumenta a dificuldade criando muitas teclas

Basicamente é isso o jogo, quando você fica sem pontos você recebe uma tela de Fim de jogo

Agora vamos analisar no fundo ele.

---

## Codigo do jogo 

![Referente as teclas pretas criadas](https://user-images.githubusercontent.com/103005263/221084748-bb165f29-e92c-4475-a4b6-e6d498f055f9.jpg)

Essa Parte do codigo é a mais simples de se explicar, então vamos lá...

Quando clicamos na bandeira verde(onde iniciamos o jogo) ele irá começar a criar as setas de acordo da posição onde eu coloquei, as setas referentes ao "AlvoY" é onde ele irá ficar na tela, as seteas pretas irão ser padronizas quase na borda na tela, mas não irá encostar na borda, após isso elas irão ser criadas

Sempre que for identificado o comando da seta no teclado, ele irá ser identificado, tive que fazer um sistema dele identificar no momento que o jogador está apertando a tecla, pois havia um bug que se o jogador estivesse segurando as setinhas, sempre acertava, então basicamente, fiz uma analise onde se a seta não estiver sendo acionada ela irá colocar o tempo da seta para 0, se pressionarmos as teclas o tempo do aperto da seta irá ser trocado para 1, então é um sistema onde sempre vamos verificar se o jogador está apertando a tecla no momento certo, se apertar ganhou o ponto, se não a tecla não é reconhecida(espero que dê para entender)

Agora na criação das setas, fiz 4 sprites para cada uma delas onde elas se multiplicam e virão 4, que são as setas que ficam paradas para esperar as setas que movimentam chegar, criando elas, fiz um espaçamento de 100, já que o Scratch usa um quadrado então cada medida é um valor, 100 era o ideal para meus testes, fiz varios testes, 60, 50... mas 100 foi o ideal do espaçamento entre elas

Continuando, após eu criar elas eu mudei os tamanhos dela e fiz elas ficarem exatamente onde eu queria, que era quase perto da borda mas nem tanto, se eu não fizesse elas se posicionarem, elas iriam para fora da tela, como esse sprite tem varias formas, esquerda, direita, cima baixo, coloquei um bloco que ele troca cada seta criada, como existem 4 sprites, ele muda de acordo com o numero, exemplo, se eu fosse criar um numero 1, seria o lado esquerdo, 2 lado direito e assim vai...

A Parte onde eu defino o movimento de quando o jogador for pressionar a tecla, se for identificado uma seta pressionada, o ID seria o numero de cada seta, esquerda, direita... 
Os nomes seriam os nomes das setas que eu estou pressionando, é basicamente isso o que esse bloco de comando faz, ele identifica e retorna o comando para o jogador. existe um "broadcast" que será acionada assim que a tecla for pressionada, vamos ver isso em outro lugar do codigo

Mesma coisa do "When I Receive Fim de jogo" vamos ver em outra parte do codigo

![teclas aleatorias criadas](https://user-images.githubusercontent.com/103005263/221088776-e6e7380c-d51c-4269-8988-fc8714d56237.jpg)

Parte mais complicada, talvez? 

Vamos lá, vamos começar pela criação das notas que vão ser aleatorias, elas irão desces e você terá que apertar no momento certo, comecei criando um clone do ID que seria as teclas 1(esqueda), 2 ,3 4, porém mudei as posições para ficar no topo da tela, está parte do codigo eu usei as mesmas sprites da parte do codigo anterior porém mudei a cor, fiz a mesma coisa delas se duplicarem, a mesma distancia para ficar direito, essa parte do codigo resumindo é todo o sistema do jogo, onde quando apertar no momento certo você acerta ou erra, acertando ele se multiplica em 5 gerando um efeito quando você acerta, se você erra a tecla vai para o fim da tela e aparece "Erro", assim perdendo a pontuação

não irei detalhar tudo dessa parte, mas em resumo ele irá criar setas aleatorias entre 0.5 a 1 segundo, passando de 10 pontos é criada de 0.2 a 0.5 segundos, passando de 20 pontos, ele irá criar de 0.1 a 0.1 segundos, dificil né?

![Alerta](https://user-images.githubusercontent.com/103005263/221091633-4f05ffdc-f521-4b51-9fe2-d06a654256b3.jpg)

Está parte do é a parte onde aparece o "Boa!!" e o "Erro" é relativamente simples, o alerta vai aparecer em posições perto das teclas,. se o jogador acerta aparece boa se não erro, coloquei uns efeito para ele crescer para deixar bonito, nada demais

![pontuação](https://user-images.githubusercontent.com/103005263/221091979-2c5b4a25-288e-4f09-ae39-79e93f298d73.jpg)

Está parte é o sistema de pontuação, quando você aperta a bandeira a pontuação começa a ser contada na parte superior da tela, onde é setada em 0, sempre que se o acerto for falso ele irá ver se a pontuação será = 0, se não for ele irá descontar pontos do jogador, se a pontuação for menor que 0, irá aparecer na tela o fim de jogo bem no meio dela e irá parar todo o Script, por isso que em todas as partes do codigo possuem "When I Receive Fim de jogo", ele irá parar todo o Script no final

---

# Fim

Embora eu tenha conseguido fazer uma engenharia dessa, o jogo parece simples mas deu para aprender como se comporta o Scratch 
