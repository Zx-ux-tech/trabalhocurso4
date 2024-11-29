<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Bai+Jamjuree:wght@200;400;600&display=swap" rel="stylesheet">
    <title>A Jornada de Takumi Saito</title>
    <style>
        body {
            font-family: 'Bai Jamjuree', sans-serif;
            color: #DDD;
            margin: 0;
            transition: background-color 0.5s;
            background-color: #1C1C1C;
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow: hidden;
        }
        main {
            max-width: 600px;
            padding: 20px;
            text-align: center;
        }
        .btn-proximo, .btn-voltar {
            background-color: #555;
            color: #FFF;
            border: none;
            padding: 12px 20px;
            cursor: pointer;
            font-weight: bold;
            margin-top: 10px;
            border-radius: 4px;
            transition: background-color 0.3s;
        }
        .btn-proximo:hover, .btn-voltar:hover {
            background-color: #777;
        }
        .passo { display: none; }
        .ativo { display: block; }
        img {
            max-width: 100%;
            border-radius: 8px;
            margin-bottom: 15px;
        }
    </style>
</head>
<body id="body">
    <main>
        <!-- Primeira escolha -->
        <div class="passo ativo" id="passo-0">
            <img src="img/cenario-inicio.png" alt="Cidade abandonada ao entardecer">
            <p>Takumi Saito, ex-soldado e agora sobrevivente de uma pandemia, vaga por cidades abandonadas em busca de respostas. Uma carta misteriosa encontrada em uma cidade fantasma o guia para uma possível cura. Ele decide seguir as pistas, sabendo que qualquer decisão errada pode custar sua vida.</p>
            <button class="btn-proximo" data-proximo="1" onclick="mudarPasso(1, '#0A0A0A')">Entrar na cidade à noite</button>
            <button class="btn-proximo" data-proximo="2" onclick="mudarPasso(2, '#1C1C1C')">Esperar até o amanhecer</button>
            <button class="btn-voltar" disabled>Voltar</button>
        </div>

        <!-- Escolhas subsequentes -->
        <div class="passo" id="passo-1">
            <img src="img/edificio-ruinas.png" alt="Edifício abandonado e escuro">
            <p>Ao entrar na cidade à noite, Takumi escuta passos pesados em um prédio em ruínas. Ele pode tentar investigar em busca de suprimentos ou se esconder até ter certeza de que é seguro.</p>
            <button class="btn-proximo" data-proximo="3" onclick="mudarPasso(3, '#292929')">Investigar o prédio</button>
            <button class="btn-proximo" data-proximo="4" onclick="mudarPasso(4, '#1A1A1A')">Se esconder em silêncio</button>
            <button class="btn-voltar" onclick="mudarPasso(0, '#1C1C1C')">Voltar</button>
        </div>

        <div class="passo" id="passo-2">
            <img src="img/sobreviventes-armados.png" alt="Grupo de sobreviventes armados na rua">
            <p>Takumi espera até o amanhecer. A cidade está quieta, mas ele nota um grupo de sobreviventes armados na rua. Ele precisa decidir rapidamente o que fazer.</p>
            <button class="btn-proximo" data-proximo="5" onclick="mudarPasso(5, '#2B2B2B')">Confrontar os sobreviventes</button>
            <button class="btn-proximo" data-proximo="6" onclick="mudarPasso(6, '#3A3A3A')">Ficar escondido e observar</button>
            <button class="btn-voltar" onclick="mudarPasso(0, '#1C1C1C')">Voltar</button>
        </div>

        <div class="passo" id="passo-3">
            <img src="img/interior-predio.png" alt="Interior escuro e sombrio do prédio">
            <p>Dentro do prédio, Takumi encontra suprimentos úteis e um mapa detalhando uma possível rota para um refúgio seguro. No entanto, ele ouve um barulho vindo do andar de baixo.</p>
            <button class="btn-proximo" data-proximo="7" onclick="mudarPasso(7, '#2F2F2F')">Investigar o barulho</button>
            <button class="btn-proximo" data-proximo="8" onclick="mudarPasso(8, '#1B1B1B')">Escapar do prédio</button>
            <button class="btn-voltar" onclick="mudarPasso(1, '#0A0A0A')">Voltar</button>
        </div>

        <div class="passo" id="passo-4">
            <img src="img/infectados.png" alt="Grupo de infectados nas proximidades">
            <p>Takumi se esconde e percebe que o som vinha de um animal, mas isso chamou a atenção de um grupo de infectados próximos. Ele agora deve agir rápido.</p>
            <button class="btn-proximo" data-proximo="9" onclick="mudarPasso(9, '#404040')">Correr para longe</button>
            <button class="btn-proximo" data-proximo="10" onclick="mudarPasso(10, '#333333')">Tentar enfrentar os infectados</button>
            <button class="btn-voltar" onclick="mudarPasso(1, '#0A0A0A')">Voltar</button>
        </div>

        <!-- Outros cenários e finais podem ser desenvolvidos -->

        <div class="passo" id="passo-5">
            <img src="img/confronto-sobreviventes.png" alt="Confronto com sobreviventes">
            <p>Confrontar os sobreviventes foi arriscado, mas Takumi consegue convencê-los a deixá-lo passar. Eles compartilham informações valiosas sobre um abrigo seguro nas montanhas.</p>
            <button class="btn-voltar" onclick="mudarPasso(2, '#1C1C1C')">Voltar</button>
        </div>

        <div class="passo" id="passo-6">
            <img src="img/observando-sobreviventes.png" alt="Takumi observando grupo hostil">
            <p>Observando de longe, Takumi percebe que o grupo é hostil. Ele opta por recuar e traçar um novo plano.</p>
            <button class="btn-voltar" onclick="mudarPasso(2, '#1C1C1C')">Voltar</button>
        </div>

        <!-- Mais cenários -->

    </main>
    <script>
        function mudarPasso(proximo, cor) {
            document.querySelector('.ativo').classList.remove('ativo');
            document.getElementById('passo-' + proximo).classList.add('ativo');
            document.body.style.backgroundColor = cor;
        }
    </script>
</body>
</html>
